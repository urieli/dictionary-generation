# Getting dictionary from parallel corpus using mGiza

## Installation

1. Create a python virtual env under Python 3.11.10
1. Install required python packages:

```shell
 pip install -r requirements.txt
```

2. Install git submodules (mosesdecoder and mgiza):

```shell
git submodule update --init --recursive
```

3. Install required apt packages for boost:

```shell
sudo apt install build-essential libboost-system-dev libboost-thread-dev libboost-program-options-dev libboost-test-dev
```

3. Compile mgiza:

```shell
cd mgiza/mgizapp
cmake .
make
```

## Usage

1. Define config variables `LANG1`, `LANG2` and the parallel corpus file prefixes in `TRAIN_PREFIXES`. E.g.:

```
# config.yaml
LANG1: "en"
LANG2: "yi"

TRAIN_PREFIXES:
    - "data/book_prefix1"  # assuming you have book_prefix1.en and book_prefix1.yi files in the data sub-directory
```

2. Run snakemake : `snakemake --cores 2`

It will output a file `lang1-lang2.dic`, e.g.

```
en      tpi
disease sik
sick    sik
illness sik
tuberculosis    tb
tb      tb
he      em
his     em
him     em
a       wanpela
```

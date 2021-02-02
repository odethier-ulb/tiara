# Tiara 

Deep-learning-based approach for identification of eukaryotic sequences in the metagenomic data powered by [PyTorch] (https://pytorch.org).  

The sequences are classified in two stages:

- In the first stage, the sequences are classified to classes: 
      archea, bacteria, prokarya, eukarya, organelle and unknown.
- In the second stage, the sequences labeled as organelle in the first stage 
      are classified to either mitochondria, plastid or unknown.

For more information on the methods used, please refer to *link do pracy*.

## Requirements

- `Python >= 3.7`
- `numpy, biopython, torch, skorch, tqdm`

## Installation

More detailed installation instructions can be found [here](docs/detailed-installation.md).

#### Using setup.py

```bash
git clone https://github.com/ibe-uw/tiara.git
cd tiara
python setup.py install
```
This will install **tiara** in your Python environment.

#### Testing the installation

After the installation, run `tiara-test` to see if the installation was successful.

## Usage

#### Basic usage:
```bash
tiara -i sample_input.fasta -o out.txt
```

The sequences in the fasta file should be at least 3000 bases long (default value). We do not recommend classify sequences that are shorter than 1000 base pairs.

It creates two files: 

 - out.txt, a tab-separated file with header `sequence id, first stage classification result, second stage classification result`.
 - log_out.txt, containing model parameters and classification summary.

#### Advanced:

```bash
tiara -i sample_input.fasta -o out.txt --tf mit pla pro -t 4 -p 0.65 0.60 --probabilities
```

In addition to creating the files above, it creates, in the folder where `tiara` is run,
three files containing sequences from `sample_input.fasta` classified as 
mitochondria, plastid and prokarya (`--tf mit pla pro` option).

The number of threads is set to 4 (`-t 4`) and probability cutoffs 
in the first and second stage of classification are set to 0.65 and 0.6, respectively.

The probabilities of belonging to individual classes are also written to 
`out.txt`, thanks to `--probabilities` option.

For more usage examples, go [here](docs/usage.md).

## Citation 

## License

Tiara is released under an open-source MIT license 














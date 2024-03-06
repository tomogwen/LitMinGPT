[![Pre-commit](https://github.com/tomogwen/LitGPT/actions/workflows/pre-commit.yml/badge.svg)](https://github.com/tomogwen/LitGPT/actions/workflows/pre-commit.yml)&nbsp;&nbsp;[![Tests](https://github.com/tomogwen/LitGPT/actions/workflows/tests.yml/badge.svg)](https://github.com/tomogwen/LitGPT/actions/workflows/tests.yml)
# ⚡️ Lightning Minimal GPT

This repo contains my efforts to learn how to create a (better than research code, aspiring to production quality) deep learning repository. It trains an implementation of Kaparthy's [minGPT](https://github.com/karpathy/minGPT) in PyTorch Lightning.

**MWE:** The code here grew out of a minimal example of multi-node, multi-GPU training with PyTorch Lightning on a slurm cluster - if you're interested in that, please see the [slurmformer branch](https://github.com/tomogwen/LitGPT/tree/slurmformer).

## Installation

To install dependencies and activate the conda environment:
```
conda env create -f env.yml
conda activate litgpt
```

If developing, install pre-commit checks:
```
pre-commit install
```

## Usage

To train the model (whilst in the conda environment):
```
litgpt fit --config configs/default.yaml
```

You can override and extend the config file using the CLI. Arguments like `--optimizer` and `--lr_scheduler` accept Torch classes. For example:
```
litgpt fit --config configs/default.yaml --optimizer Adam
```

This uses the [LightningCLI](https://lightning.ai/docs/pytorch/stable/cli/lightning_cli_intermediate.html#). Full options can be seen by running `litgpt fit --help`.

## Usage (Slurm)

A shell script for Slurm HPC's is available. Set the required variables in the shell script, and run:

```
sbatch scripts/train.sh
```

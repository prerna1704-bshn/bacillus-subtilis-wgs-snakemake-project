# Bacillus subtilis WGS Analysis and Snakemake Workflow

## Project Overview

This project analyzes paired-end Illumina whole-genome sequencing data from *Bacillus subtilis* using a bioinformatics workflow.

The workflow was first performed step-by-step to understand each analysis stage and was then converted into a Snakemake workflow to automate and organize the same analysis.

## Workflow

Raw paired-end Illumina reads
↓
fastp — Read trimming and QC
↓
SPAdes — Genome assembly
↓
QUAST — Assembly quality assessment
↓
Prokka — Genome annotation
↓
BLASTP — Laccase candidate confirmation

## Tools Used

- Fastp — read preprocessing and quality control
- SPAdes — de novo genome assembly
- QUAST — assembly quality assessment
- Prokka — genome annotation
- BLASTP — protein sequence similarity search
- Snakemake — workflow automation and reproducibility
- Conda — environment management

## Dataset

- Organism: *Bacillus subtilis*
- Sequencing type: Illumina paired-end
- NCBI SRA accession: SRR39923808

## Results

### Genome Assembly

- Total assembly length: 4,222,878 bp
- Number of contigs: 43

### Genome Annotation

- CDS: 4,328
- rRNA: 18
- tRNA: 84
- tmRNA: 1
- ncRNA: 0

### Laccase Candidate Confirmation

BLASTP identified `DGGODKJG_04118` as a strong CotA laccase candidate.

- Reference protein: UniProt P07788 (COTA_BACSU)
- Sequence identity: 98.246%
- Alignment length: 513 amino acids
- E-value: 0.0
- Bit score: 1052

## Snakemake Workflow

After completing the analysis manually, the same workflow was implemented in Snakemake.

This provides:

- Automated execution of analysis steps
- Defined input and output dependencies
- Reproducible workflow structure
- Easier rerunning of individual steps
- Organized project management

The workflow includes rules for read preprocessing, genome assembly, assembly assessment, genome annotation, laccase confirmation, and final result summarization.

## Repository Structure

```text
laccase_project/
├── Snakefile
├── config.yaml
├── .gitignore
├── envs/
│   └── prokka.yaml
├── gene_confirmation/
├── prokka_output/
├── quast_output/
└── results/
    └── pipeline_summary.txt

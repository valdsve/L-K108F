# L-K108F
Repository for project in LÆK108F

# MITF knockdown RNA-seq re-analysis in U2OS cells

This repository contains the code used to re-analyze publicly available RNA-seq data from untreated U2OS cells following MITF knockdown.

The aim was to identify genes and biological pathways associated with MITF depletion and to assess sample-level variation within the dataset.

## Data source

RNA-seq data were obtained from GEO accession:

**GSE264653**

Six untreated U2OS libraries were analysed:

### siControl
- SRR28780436
- SRR28780442
- SRR28780448

### siMITF
- SRR28780433
- SRR28780439
- SRR28780445

Raw paired-end FASTQ files were downloaded from the European Nucleotide Archive (ENA) using the corresponding `fastq_ftp` links.

The raw FASTQ files are not included in this repository because of their size and can be re-downloaded from GEO/ENA using the accession numbers above.

## Analysis workflow

The main full-depth analysis consisted of:

1. Raw-read quality control using FastQC and MultiQC.
2. Transcript quantification using kallisto.
3. Import of kallisto abundance estimates into R using tximport.
4. Transcript-to-gene aggregation using Ensembl GRCh38 release 116 annotation.
5. Differential-expression analysis using DESeq2.
6. Exploratory analysis using PCA, sample correlation and hierarchical clustering.
7. Investigation of two atypical samples showing an immune/B-cell-associated expression signature.
8. GO Biological Process enrichment analysis.
9. GO gene-set enrichment analysis (GSEA).
10. Hallmark GSEA using the MSigDB Hallmark gene-set collection.
11. Sensitivity analysis after exclusion of SRR28780442 and SRR28780445.

A reduced-depth analysis using the first 1,000,000 read pairs from each library was performed separately.

## Reference files

The full-depth analysis used:

- Human genome build: **GRCh38**
- Ensembl release: **116**
- cDNA transcriptome: `Homo_sapiens.GRCh38.cdna.all.fa`
- Gene annotation: `Homo_sapiens.GRCh38.116.gtf`

A kallisto index was generated from the Ensembl cDNA FASTA before transcript quantification.

Reference files are not included in this repository and should be downloaded directly from Ensembl.

## Repository structure

```text
MITF_RNAseq_reanalysis/
├── README.md
├── sessionInfo.txt
│
├── analysis/
│   └── DESeq2_BioProj_LÆK108F.Rmd
│
├── metadata/
   ├── metadata.tsv
   └── ena_runs.tsv


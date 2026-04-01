# Dietary Patterns and Gut Microbiome Diversity
### An Exploratory Analysis Using the American Gut Project

## Overview

This project investigates whether plant-rich dietary patterns are associated with 
increased gut microbiome diversity, using publicly available data from the 
**American Gut Project (AGP)** — one of the largest citizen-science microbiome 
studies to date.

The central hypothesis, supported by current literature, is that greater plant 
consumption → higher dietary fiber → increased microbial alpha diversity. This 
project aims to explore that relationship empirically across a large, heterogeneous 
population.

## Research Question

Do individuals who consume a greater variety and quantity of plants show 
significantly higher gut microbiome diversity compared to those on low-plant diets?

## Background & Motivation

The gut microbiome plays a critical role in metabolic health, immune function, and 
disease risk. Dietary fiber — found predominantly in plants — is a primary energy 
source for gut bacteria, and research consistently links fiber intake to microbial 
richness and evenness. The American Gut Project offers a unique opportunity to 
explore this relationship at scale with real-world dietary data.

Key literature informing this project:
- McDonald et al. (2018) — *American Gut: an Open Platform for Citizen Science 
  Microbiome Research* — mSystems. DOI: 10.1128/mSystems.00031-18
- Dahl et al. (2023) — *A dietary fiber-deprived gut microbiota degrades the 
  colonic mucus barrier* — Cell. (foundational mechanistic support)

## Dataset: American Gut Project

**Source:** The AGP data is publicly available via the QIITA platform and the 
Knight Lab.

**Access:** [American Gut Project on GitHub](https://github.com/biocore/American-Gut)
or via QIITA study ID 10317.

**Key features of the dataset:**
- 16S rRNA amplicon sequencing (gut samples)
- Self-reported dietary surveys (including plant variety, frequency of consumption)
- Participant metadata (BMI, age, antibiotic use, etc.)

> **Note:** Dietary data is self-reported, which introduces recall bias. Findings here are observational and do not imply causation.

## Hypothesis

> Participants who report consuming **more than 30 different plant types per week** will exhibit significantly higher gut microbiome **alpha diversity** (Shannon index, observed species) compared to those consuming fewer plants.

This threshold is inspired by the AGP's own finding that 30+ plant types/week was a meaningful cutoff in their analysis.

## Methods

1. **Data acquisition & preprocessing** — Download and QC raw AGP data; filter samples by sequencing depth
2. **Dietary categorization** — Group participants by plant variety (e.g., <10, 10–20, 21–30, 30+ plant types/week)
3. **Alpha diversity analysis** — Shannon index, observed species, Faith's PD across dietary groups
4. **Beta diversity analysis** — UniFrac (weighted/unweighted), PCoA visualization
5. **Statistical testing** — Kruskal-Wallis, Dunn post-hoc, PERMANOVA
6. **Differential abundance** — Identify taxa enriched in high vs. low plant consumers

## Project Structure
```
├── data/               # Raw and processed data (not tracked in git)
├── notebooks/          # Exploratory and analysis notebooks
├── src/                # Reusable functions (diversity metrics, plotting)
├── scripts/            # Data download and preprocessing scripts
└── results/            # Figures and summary tables
```

## Status

🔄 **In progress** — currently in data acquisition and EDA phase.

Planned milestones:
- [ ] Data download and QC
- [ ] Dietary grouping and metadata cleaning
- [ ] Alpha diversity analysis
- [ ] Beta diversity and PCoA
- [ ] Differential abundance testing
- [ ] Final write-up / summary notebook

## Setup
```bash
conda env create -f environment.yml
conda activate gut-analysis
```

Or with pip:
```bash
pip install -r requirements.txt
```

## About

This is a personal portfolio project exploring the intersection of nutrition and 
the gut microbiome. It is an observational, exploratory analysis and does not 
imply causality.

Built with Python, QIIME2 (planned), scikit-bio, pandas, and matplotlib/seaborn.
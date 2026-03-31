# Generative Modeling for Nanohole Array Design

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![PyTorch](https://img.shields.io/badge/Framework-PyTorch-red.svg)
![Optuna](https://img.shields.io/badge/Optimization-Optuna-green.svg)
![Status](https://img.shields.io/badge/Status-Research%20Code-informational.svg)
![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)

This repository contains the implementation of my MSc thesis on **forward and inverse design of nanohole arrays (NHAs)** using deep generative models. The framework combines a **forward surrogate neural network** for rapid spectrum prediction with **Conditional Variational Autoencoders (CVAE)**, **latent-space Bayesian Optimization (BO)**, and **InfoGAN** for accurate, scalable, and interpretable inverse nanophotonic design.

---

## Overview

Nanohole arrays are important nanophotonic structures, but their inverse design is challenging because multiple different geometries can produce very similar optical spectra. In addition, conventional **finite-difference time-domain (FDTD)** simulations are computationally expensive for large-scale design exploration.

To address this, this project develops a unified data-driven framework that:

- predicts transmission spectra from geometry using a forward surrogate model,
- reconstructs geometry from target spectra using CVAE,
- refines inverse solutions using latent-space Bayesian Optimization,
- and explores interpretable, ambiguity-aware inverse design using InfoGAN.

---

## Main Components

### 1. Forward Model
A feedforward neural network is trained to predict the **200-point transmission spectrum** from nanohole array parameters such as:

- thickness
- hole radius
- periodicity
- material type
- lattice type

This model acts as a fast surrogate for repeated FDTD evaluation.

### 2. CVAE Inverse Design
The CVAE learns a probabilistic latent representation of transmission spectra and reconstructs:

- thickness
- radius
- periodicity
- material
- lattice

This helps address the **non-uniqueness** of the inverse design problem.

### 3. CVAE + Bayesian Optimization
Bayesian Optimization is performed in the learned latent space of the CVAE to improve spectrum-domain matching without running additional FDTD simulations.

### 4. InfoGAN Inverse Design
InfoGAN introduces structured latent codes and mutual information maximization to support **interpretable** and **ambiguity-aware** inverse generation.

---

## Methodology Workflow

1. Generate or collect FDTD-based nanohole array simulation data  
2. Train a forward surrogate model for spectrum prediction  
3. Train a CVAE for inverse parameter reconstruction  
4. Apply Bayesian Optimization in latent space to refine inverse solutions  
5. Train InfoGAN for interpretable and controllable inverse design  
6. Benchmark model performance using regression and spectrum-domain metrics

---

## Figure Placeholders

### Overall Pipeline
![Overall Pipeline](figures/overall_pipeline.png)

### Forward Model Architecture
![Forward Model](figures/forward_model.png)

### CVAE Architecture
![CVAE Architecture](figures/cvae_architecture.png)

### CVAE + BO Hybrid Framework
![CVAE+BO Architecture](figures/cvae_bo_architecture.png)

### InfoGAN Architecture
![InfoGAN Architecture](figures/infogan_architecture.png)

### Example Results
![Results Overview](figures/results_overview.png)

> Replace these image paths with your actual figure filenames.

---

## Suggested Repository Structure

```bash
.
├── data/
│   ├── raw/
│   ├── processed/
│   └── README.md
├── notebooks/
│   ├── forward_model.ipynb
│   ├── final_cvae_model.ipynb
│   ├── infogan_model.ipynb
│   └── bo_optimization.ipynb
├── scripts/
│   ├── train_forward.py
│   ├── train_cvae.py
│   ├── train_infogan.py
│   ├── run_bo.py
│   └── evaluate.py
├── models/
│   ├── forward_model.py
│   ├── cvae.py
│   ├── infogan.py
│   └── utils.py
├── figures/
├── results/
│   ├── checkpoints/
│   ├── plots/
│   └── tables/
├── thesis_report.pdf
├── requirements.txt
└── README.md

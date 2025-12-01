# Assessing-Causal-Discovery-Algorithms-for-Smoking-Outcome-Relationships
A causal discovery project evaluating PC and GES causal discovery algorithms on real-world CDC data to identify relationships between smoking and health outcomes. Provides a benchmark for applying causal inference algorithms towards other epidemiology and public health issues.


## Overview
This project establishes a **real-world testbed** for evaluating the effectiveness of two prominent **causal discovery algorithms**, the **Peter-Clark (PC)** algorithm and the **Greedy Equivalence Search (GES)** algorithm, in the context of **public health epidemiology**.

Specifically, we use data from the CDC’s National Health and Nutrition Examination Survey (**NHANES**) to analyze established causal relationships between **smoking status** and various **health outcomes** (e.g., COPD, stroke, heart disease). The goal is to benchmark these algorithms' ability to correctly infer causal structures and directionality on complex, observational, real-world data.

---

## Methodology & Data
* **Data Source:** National Health and Nutrition Examination Survey (**NHANES**, 2009–2018 cycles), focusing on ~28,500 individuals.
* **Target Relationships:** Ground truth causal links (e.g., Smoking Status $\rightarrow$ COPD) were defined using established medical literature.
* **Algorithms Evaluated:**
    * **PC Algorithm:** A **constraint-based** method using conditional independence tests.
    * **GES Algorithm:** A **score-based** method optimizing the Bayesian Information Criterion (BIC).
* **Robustness:** Both algorithms were tested using **bootstrapping** (30 runs) and applied across demographic subgroups (age, gender, ethnicity) to assess stability and heterogeneity.

---

## Key Results and Findings
### 1. Edge Discovery & Consistency
* Both PC and GES consistently identified the same set of **strong statistical relationships** (edges) connected to Smoking Status, suggesting robust underlying signals in the baseline data.
* **PC** proved more eager to find edges and stable in subgroup analyses due to its constraint-based nature and more lenient statistical threshold.
* **GES** was more **conservative**, often dropping edges in smaller subgroups due to the BIC's penalty for model complexity, but occasionally highlighted potential **heterogeneity** (subgroup-specific effects).
* **PC** seemed to be more robust and generalizable across subgroups than GES.

### 2. Directionality and Generalizability Limitations
* One challenge was **identifying correct directionality**. While GES attempts to orient edges, the inferred causal directions often **did not match established medical ground truths**.
* Both algorithms frequently identified edges between **Smoking Status and demographic factors** (Age, Gender, Ethnicity), emphasizing the strong influence of confounders inherent in cross-sectional, observational data.

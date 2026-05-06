# CRANE: Explainable Academic Advising via Category-Routed Knowledge Graph Retrieval and Generation

**CRANE** stands for **Category-Routed Answering over Networked Evidence**. It is a category-routed retrieval and generation framework for regulation-grounded academic advising.

## Authors

**Huu-Hoa Nguyen**, **Tri-Tam La**, and **Thanh Ma**

College of Information and Communication Technology  
Can Tho University  
Can Tho City, Vietnam

Contact:  
- Huu-Hoa Nguyen: nhhoa@ctu.edu.vn  
- Tri-Tam La: tamla@gmail.com  
- Thanh Ma: mtthanh@ctu.edu.vn  

## Associated Manuscript

**Title:** Explainable Academic Advising via Category-Routed Knowledge Graph Retrieval and Generation

This repository provides the datasets, source code, and reproducibility materials associated with the CRANE framework.

## Abstract

Advising on academic regulations is difficult because sources are fragmented, frequently revised, and written in administrative prose. We present CRANE, a five-stage category-routed advising framework with two algorithms: *CRANE Build* for offline construction and *CRANE Resolve* for online answering. It unifies dense retrieval with graph-guided reasoning over a regulation-enriched graph. A lightweight classifier routes each query to a domain-specific subgraph and restricts vector search to the matching index partition. Graph evidence is gated by an edge-confidence threshold τ and does not affect vector similarity. Vietnamese named-entity recognition and PhoBERT embeddings provide language-appropriate enrichment, and the generator receives a structured prompt with citations and version metadata.

We evaluate CRANE on institutional question-answering using two resources: 13,684 labeled queries and 8,635 question-answer pairs verified by academic staff. Under protocol parity, CRANE attains an F1 Score of 99.03% with GPT and 98.69% with Mistral at τ = 0.6. It improves over a vector-only RAG baseline by 3.66 and 3.71 points while maintaining average end-to-end latency near 7 seconds per query. The domain router reaches 97.29% accuracy and 96.72% F1 Score on six-way domain classification. Ablation studies show that removing query routing, named-entity recognition, or budgeted τ-thresholded graph expansion reduces F1 Score by 2.56 to 4.38 points. Sensitivity analysis peaks at τ = 0.6. Scalability tests keep accuracy stable with near-linear latency as the vector index grows. These results indicate that category-routed retrieval with confidence-gated graph evidence can deliver verifiable regulation advising with high accuracy under a bounded latency budget.

## Keywords

Academic advising, regulation question-answering, retrieval-augmented generation, knowledge graphs, query routing, Vietnamese NLP, explainable AI

## Overview

CRANE is designed for regulation-centric question-answering tasks where responses must be grounded in official sources and remain traceable to valid document anchors. The framework combines:

- Domain classification for routing each query to a relevant advising category.
- Domain-partitioned dense retrieval using PhoBERT embeddings.
- A regulation-enriched graph that represents passages, entities, categories, and typed relations.
- Confidence-gated graph evidence controlled by the threshold τ.
- Version-aware and cohort-aware filtering before prompt construction.
- Citation-grounded generation with structured evidence.

The framework consists of two main algorithms:

1. **CRANE Build**: constructs the domain-partitioned vector index and the regulation-enriched graph from official regulatory documents.
2. **CRANE Resolve**: routes a query, retrieves relevant passages, expands graph evidence under fixed budgets, assembles a structured prompt, and generates a citation-grounded answer.

## Datasets

This repository includes resources used in the evaluation of CRANE:

- A six-way domain classification dataset with **13,684 labeled queries**.
- A regulation-oriented question-answering dataset with **8,635 question-answer pairs**.
- Reproducibility materials for the reported experiments.

The question-answer pairs were verified by academic staff and are intended for evaluating regulation-grounded advising systems.

## Main Results

At the main operating point τ = 0.6, CRANE achieved the following results under the evaluation protocol reported in the manuscript:

| Generator | Accuracy | Precision | Recall | F1 Score | Avg. latency |
|---|---:|---:|---:|---:|---:|
| GPT | 98.78% | 99.15% | 98.91% | 99.03% | 7.13 s |
| Mistral | 97.44% | 99.09% | 98.29% | 98.69% | 7.01 s |

The domain router achieved **97.29% accuracy** and **96.72% F1 Score** on the six-way classification task.

## Data and Code Availability

The datasets generated and/or analyzed during the current study, together with the source code and reproducibility materials, are publicly available in this repository:

https://github.com/tamB2203579/CRANE

## Citation

If you use this repository, please cite the associated manuscript:

**Nguyen, H.-H., La, T.-T., and Ma, T.**  
*Explainable Academic Advising via Category-Routed Knowledge Graph Retrieval and Generation.*

The final bibliographic information will be updated after publication.

## Acknowledgements

The authors thank the academic staff of Can Tho University for supporting the verification of the labeled queries and regulation-oriented question-answer pairs used in this study. The authors also thank the AI and Big Data Laboratory, College of Information and Communication Technology, Can Tho University, for helpful discussions and technical support.

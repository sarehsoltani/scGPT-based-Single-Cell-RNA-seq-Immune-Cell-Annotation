# Immune Cell Type Annotation from scRNA-seq using scGPT

We applied the **scGPT** transformer-based model to single-cell RNA-seq data to classify and annotate immune cell types from blood samples. This end-to-end pipeline processed ~20,000 cells and leveraged scGPT embeddings for dimensionality reduction, clustering, and immune subtype classification.

We identified ~10 immune subpopulations, validated using canonical marker genes and highly variable gene (HVG) selection. Our results demonstrate the power of large-scale generative models for high-resolution immune profiling, showcasing how transformer-based deep learning can effectively analyze complex, high-dimensional biological data.

---

## 📊 1. Data Preprocessing

- Loaded raw single-cell RNA-seq count matrix.
- Performed quality control: filtered low-quality cells and genes.
- Normalized and log-transformed gene expression values.
- Selected highly variable genes (HVGs) for downstream analysis.

---

## 🤖 2. Embedding Extraction with scGPT

- Used the pre-trained `whole_human` checkpoint from [scGPT](https://huggingface.co/bowang/scGPT).
- Extracted cell embeddings using the `embed_data` function for all ~20K cells.

---

## 🧬 3. Clustering and Visualization

- Applied **UMAP** for 2D visualization of the scGPT-generated cell embeddings.
- Performed **Leiden clustering** to detect distinct cell populations.

Image 1: UMAP of scGPT embeddings with Leiden clusters
<img width="500" height="431" alt="Image" src="https://github.com/user-attachments/assets/fb1860a2-5915-48b1-bfd0-e9ae1e41e11c" />

---

## 🧾 4. Cell Type Annotation

- Used canonical marker genes to assign immune cell identities.
- Grouped cell types into three major immune categories:
  - **Lymphocyte**
  - **Myeloid**
  - **Platelet**
- Visualized both detailed annotations and grouped categories on UMAP plots.

Image 2: Annotated UMAP with immune subtypes and categories
<img width="500" height="431" alt="Image" src="https://github.com/user-attachments/assets/a4590525-15ca-4620-a43d-0942895c11be" />
---

## ✅ Results

- **UMAP** visualization revealed clear separation of major immune cell types.
- **Leiden clustering** detected distinct subpopulations with high biological relevance.
- **Marker gene-based annotation** identified the following cell types:
  - CD4+ T cells
  - CD8+ T cells
  - Regulatory T cells (Tregs)
  - B cells
  - Plasma cells
  - Natural Killer (NK) cells
  - Monocytes
  - Dendritic cells
  - Macrophages
  - Neutrophils
  - Platelets
  - Erythrocytes
- Main immune categories (Lymphocyte, Myeloid, Platelet) were visualized and quantified.

---

## ✅ Strengths

- **Transformer-powered**: scGPT models complex, nonlinear, and sparse single-cell data.
- **Pre-trained on large-scale data**: The `whole_human` checkpoint enables strong generalization and transfer learning.
- **Gene-gene and cell-cell interactions**: Captures long-range biological dependencies.
- **Superior embeddings**: Clearer separation of cell types and subtypes.
- **Highly flexible**: Adaptable to multi-modal data, metadata integration, and custom tasks.
- **Scalable and efficient**: Optimized for large-scale datasets.
- **Effective for rare cell types**: Better annotation in underrepresented populations.
- **Minimal fine-tuning required**: Transfer learning enables use on new datasets with limited labeled data.

---

## ⚠️ Limitations

- Requires **careful preprocessing** and thoughtful marker selection.
- Performance depends on **pre-trained model quality** and comprehensive marker gene lists.
- **Computationally intensive**, particularly when training from scratch.
- Transformer models are less interpretable than simpler alternatives (e.g., PCA, scVI).

---

## 🔗 Resources

- [scGPT Paper (bioRxiv)](https://www.biorxiv.org/content/10.1101/2023.04.05.535799v1)
- [Hugging Face scGPT Model](https://huggingface.co/bowang/scGPT)
- [scGPT GitHub Repository](https://github.com/bowang-lab/scGPT)


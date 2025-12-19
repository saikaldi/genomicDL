This README file is designed to be the professional documentation for your project. It summarizes the technical journey from raw genomic data to a high-performance ensemble system.

---

# Multi-Stage Genomic Classification: From ML Baselines to Optimized SAE Ensembles

This project implements a comprehensive bioinformatics pipeline to classify cancer subtypes using high-dimensional gene expression data (1,000 features). The primary challenge addressed is the extreme class imbalance and the "curse of dimensionality."

## Project Roadmap (8 Sections)

### Section 1 - Importing Libraries and Data Loading

* **Action:** Cleaned the dataset and applied `StandardScaler`.
* **Goal:** Ensure that all 1,000 genes contribute equally to the model, preventing genes with higher numerical ranges from dominating the gradients.

### Section 2: Exploratory Data Analysis (EDA)

* **Models:** Random Forest (RF), SVM, and Gradient Boosting (GB).
* **Finding:** These models achieved high global accuracy (~91%) but failed on rare subtypes. The RF showed a Macro F1 of only 0.60, proving a heavy bias toward majority classes.

### Section 3: Data Preprocessing

* **Action:** Compared Convolutional Neural Networks (CNN) with Stacked Autoencoders (SAE).
* **Finding:** CNNs performed poorly (53% accuracy) because genomic data lacks spatial locality. The SAE emerged as the superior architecture for feature compression.

### Section 4: Training Traditional Machine Learning Models

* **Action:** Built a 3-layer Autoencoder to compress 1,000 genes into a **128-unit Latent Space**.
* **Goal:** Noise reduction. By forcing the data through a "bottleneck," the model learns the essential biological signals and ignores random genetic noise.

### Section 5: Deep Learning Architecture Baseline: Stacked Autoencoder (SAE)

* **Action:** Introduced **GELU activation, Gaussian Input Noise, L2 Regularization,** and **Class-Weighted Cross-Entropy**.
* **Result:** This model became our "Specialist." It raised the Recall for rare Subtype 4 from **0.50 to 0.83**.

### Section 6: Optimizing & Hyperparameter Tuning 

* **Action:** Implemented **Early Stopping** and **Learning Rate Reduction** on plateau.
* **Goal:** Prevented overfitting despite the rising training loss, ensuring the model generalizes well to unseen patient samples.

### Section 7: Diversity Ensemble & Final Evaluation

* **Action:** Created a "Soft Voting" ensemble combining three different architectures: **Balanced, Deep & Narrow, and Wide & Shallow.**
* **Result:** Achieved **100% Precision** for rare subtypes. The ensemble acts as a high-confidence "Judge" to verify the SAE's findings.

### Section 8: Results and Visualization

* **Action:** Comparative analysis of all 7 models (RF, SVM, GB, Std SAE, CNN, Opt SAE, Ensemble).
* **Visualization:** Used t-SNE latent space plots and performance bar charts to prove the superiority of the optimized deep learning approach.

---

## 🏆 Final Conclusion

The project successfully demonstrates that **Architectural Optimization** is more critical than raw model depth in bioinformatics.

1. **The Winner for Discovery:** The **Optimized SAE** is the most effective model for clinical screening, reaching an **87% Accuracy** and **83% Recall** for rare cancer subtypes where traditional ML failed.
2. **The Winner for Certainty:** The **Diversity Ensemble** is the superior tool for diagnostic confirmation, achieving **90.65% Accuracy** and **100% Precision** for complex classes.
3. **Key Takeaway:** By compressing 1,000 genes into a 128-feature latent space, we removed enough noise to allow deep learning models to identify the subtle "genetic fingerprints" of rare cancer variants.

---

## 🛠️ Technologies Used

* **Python / TensorFlow / Keras:** Deep Learning Architecture.
* **Scikit-Learn:** Traditional ML baselines and metrics.
* **Imbalanced-Learn (SMOTE):** Data augmentation for minority classes.
* **Matplotlib / Seaborn:** Advanced data visualization.

---

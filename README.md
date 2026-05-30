# 🌾🚀 Multimodal Spectral Fusion for Wheat Disease Classification

---

# 🧠 Overview

This project presents a deep learning framework for wheat disease classification using multispectral (MS) and hyperspectral (HS) imagery.

The system classifies wheat crop patches into:

* 🌿 Healthy
* 🍂 Rust
* ⚫ Other

The project demonstrates that spectral imaging significantly outperforms traditional RGB imagery for crop disease detection.

---

# 🛰️ Why Spectral Imaging?

RGB imagery often fails to reveal early physiological stress, while spectral imaging captures:

* Chlorophyll absorption
* Red-edge shifts
* Near Infrared (NIR) stress signatures

---

# 🧪 Key Contributions

✅ Built modality-specific deep learning models for:

* RGB imagery
* Multispectral imagery
* Hyperspectral imagery

✅ Designed MS + HS fusion using:

* Learnable gating
* Cross-modal attention
* 4-head attention mechanism

✅ Demonstrated why RGB should be excluded from fusion:

* RGB is synthetically derived from HS bands
* RGB + HS introduces redundant information

✅ Evaluated learned fusion embeddings using:

* SVM
* KNN
* Logistic Regression
* Random Forest

---

# 🧠 Fusion Model Architecture

## 🔄 Pipeline

```text
MS Input → MS Encoder
HS Input → HS Encoder
        ↓
Cross-Modal Attention
        ↓
256-D Fusion Embedding
        ↓
MLP Classifier
        ↓
Healthy / Rust / Other
```

---

# ⚙️ Preprocessing Pipeline

## 🌈 RGB Preprocessing

* CLAHE enhancement
* Custom normalization
* Resize to 224×224

## 🛰️ MS Preprocessing

* uint16 scaling (/65535)
* Per-band normalization
* Spectral augmentation
* Resize to 112×112

## 🔬 HS Preprocessing

* Trimmed from 125 → 101 clean bands
* Per-band normalization
* Spectral noise augmentation
* Clamp normalization

---

# 🤖 Model Architectures

## 🌈 RGB Model

* ResNet-18 backbone

## 🛰️ Multispectral Model

* Modified 5-channel ResNet-18

## 🔬 Hyperspectral Model

Hybrid architecture with:

* Spectral branch
* Spatial branch
* Feature fusion module

## 🚀 Fusion Model

Fusion combines:

* MS embeddings
* HS embeddings

Using:

* Learnable gating
* Cross-modal attention
* Multi-head attention
* MLP classifier head

---

# 📊 Validation Accuracy

| Model            | Validation Accuracy |
| ---------------- | ------------------- |
| RGB              | 55.83%              |
| Multispectral    | 73.33%              |
| Hyperspectral    | 72.50%              |
| Fusion (MS + HS) | 74.17%              |

---

# 📈 Classical Classifier Evaluation

The learned 256-D fusion embeddings were evaluated using:

* SVM
* KNN
* Logistic Regression
* Random Forest

🎯 Purpose:

* Evaluate feature-space separability
* Benchmark learned fusion representations

---

# 🔥 Why MS + HS Fusion?

RGB was excluded from fusion because:

* RGB is synthetically generated from hyperspectral bands
* RGB + HS introduces redundant information

### 🛰️ MS provides:

* Stable broad spectral cues
* Red-edge + NIR information

### 🔬 HS provides:

* Dense biochemical signatures
* Fine-grained disease information

### 🧠 Cross-modal attention enables:

Adaptive interaction between complementary modalities.

---

# ⚙️ Training Configuration

| Setting           | Value                          |
| ----------------- | ------------------------------ |
| Optimizer         | AdamW                          |
| Scheduler         | Cosine Annealing               |
| Early Stopping    | Patience = 15                  |
| Loss Function     | CrossEntropy + Label Smoothing |
| Gradient Clipping | max_norm = 1.0                 |
| Framework         | PyTorch                        |

---

# 🛠️ Technologies Used

* Python
* PyTorch
* Torchvision
* Rasterio
* NumPy
* Scikit-learn
* Matplotlib

---

# 🚀 Future Work

* Transformer-based spectral architectures
* Explainable AI (Grad-CAM, SHAP)
* UAV edge deployment
* Larger datasets for improved generalization

---

# 👨‍💻 Author

## Sovan Pal

---

# 📜 License

MIT License

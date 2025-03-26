# Sleep Disorder Prediction
![alt text](https://www.mdanderson.org/images/publications/cancerwise/Generics/cw-sleep-graphic.jpg)

## Project Overview - Anna
This main objective of this machine learning project aims to analyze a range of lifestyle and medical factors—including age, BMI, physical activity, sleep duration, and blood pressure—to predict the likelihood and type of sleep disorders an individual may develop. Conditions such as insomnia and sleep apnea can severely impact overall health and well-being. By identifying those at risk, this study seeks to facilitate early intervention and personalized treatment strategies, ultimately enhancing sleep quality and promoting long-term health.

## Data Set Description

## Patterns found in exploratory data analysis
We analyzed medical factors such as age, BMI, physical activity, sleep duration, and blood pressure to predict the likelihood and type of sleep disorders an individual may develop. To understand how each factor influences sleep disorders, we visualized distributions and relationships using various plots.

**Observed Patterns**
- More females were diagnosed with a sleep disorder compared to males. The number of women with sleep apnea is higher than those with insomnia. Meanwhile, although men were observed to have a lower likelihood of developing sleep disorders, those who do are more likely to have insomnia than sleep apnea.
-  
## Heat Map Explanation


## **📊 Model Training and Evaluation**

We trained and evaluated multiple models to determine the **best classification model** for our dataset. Based on **accuracy, precision, recall, and F1-score**, focusing on **misclassification trends** to identify areas for improvement.

Each model is assessed using the following parameters:
- **Precision**: How many of the predicted instances were actually correct?
- **Recall**: How well does the model identify all instances of a class?
- **F1-Score**: A balance between precision and recall.
- **Support**: The number of actual instances per class.

---

### **1️⃣ Precision (Positive Predictive Value)**
**"When the model predicts this class, how often is it correct?"**  
<img src="https://latex.codecogs.com/svg.latex?\text{Precision}=\frac{\text{TP}}{\text{TP}+\text{FP}}" />

For example:
- **Precision = 0.67** → When the model predicts a certain class, it is **correct 67% of the time**.
- **A low precision means the model often misclassifies other classes as that class (False Positives).**

---

### **2️⃣ Recall (Sensitivity)**
**"How well does the model identify actual instances of this class?"**  
<img src="https://latex.codecogs.com/svg.latex?\text{Recall}=\frac{\text{TP}}{\text{TP}+\text{FN}}" />

For example:
- **Recall = 0.73** → The model correctly identifies **73% of all the actual Class samples**.
- **A recall below 1.0 means some actual instances are misclassified as other classes (False Negatives).**

---

### **3️⃣ F1-Score (Balance Between Precision & Recall)**
**"A single score balancing precision and recall."**  
<img src="https://latex.codecogs.com/svg.latex?\text{F1-Score}=2\times\frac{\text{Precision}\times\text{Recall}}{\text{Precision}+\text{Recall}}" />

- If **precision and recall are both high**, F1-score will be high.
- If one is **low**, F1-score will also be **lower**.

---

### **4️⃣ Support (Number of True Instances per Class)**
**"How many actual samples belong to each class?"**
- **Support does NOT affect model performance.**  
- **But an imbalanced class (low support) may have lower recall.**  
  - Example: **If Class 0 has only 17 samples like in the KNN model**, makes it harder to classify correctly.

---

### **Model Comparison Table**

---
### **K-Nearest Neighbors (KNN) Results**
📌 **Optimal K: 11**  
📌 **Best Accuracy: 89% (with feature selection after SMOTE)**  

**📋 KNN Classification Report**  
Each row corresponds to a **specific class** (e.g., `0`, `1`, or `2`), and each column represents an **evaluation metric**.
```
              precision    recall  f1-score   support
           0       0.71      0.88      0.79        17
           1       0.96      0.96      0.96        55
           2       0.89      0.73      0.80        22

    accuracy                           0.89        94
   macro avg       0.86      0.86      0.85        94
weighted avg       0.90      0.89      0.89        94
```
**📌 Metric Breakdown**
| Metric | Class 0 (17 samples) | Class 1 (55 samples) | Class 2 (22 samples) |
|--------|----------------|----------------|----------------|
| **Precision** |**71%** (29% false positives) | **96%** (only 4% false positives) | **89%** (11% false positives) |
| **Recall** | **88%** (12% false negatives) | **96%** (4% false negatives) | **73%** (27% false negatives) |
| **F1-Score** | **0.79** | **0.96** | **0.80** |
| **Support** | **17** | **55** | **22** |

Despite performing well (89% accuracy), KNN **struggled with Class 2 misclassification** (often confused with Class 0).  
- **SMOTE oversampling did not improve Class 2 recall significantly.**
- **Feature selection slightly improved Class 0 recall but did not help Class 2.**
- **Even with weighted classification** (`weights='distance'`), KNN relies on distance-based decision boundaries, which can be **less effective for overlapping classes**. This is evident in the misclassification of Class 2 as Class 0.**  

**🔹 Confusion Matrix (Feature Selection after SMOTE)**
```
[[15  1  1]
 [ 1 53  1]
 [ 5  1 16]]
```
✅ **Class 0 recall improved (88%).**  
✅ **Class 1 is almost perfectly classified.**   
❌ **Class 2 recall remained low (73%) since it is often confused with Class 0.**  

Since **KNN struggled with Class 2 separability**, we tested **alternative models**.

---

### **Random Forest Classifier**
---
### **Support Vector Machines**
---
### **Decision Tree Classifier**
---
### **Logistic Regression**
---
## Conclusion and Overall Takeaways


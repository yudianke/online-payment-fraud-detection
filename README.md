# Online Payment Fraud Detection

This project explores **machine learning approaches for detecting fraudulent online payment transactions** using a large-scale transaction dataset containing over **6.3 million records**. The goal is to accurately identify fraudulent behavior while minimizing false alarms that negatively impact legitimate users.

---

## 📌 Problem Statement

Online payment systems are highly vulnerable to fraud due to their scale and real-time nature. Missing a fraudulent transaction can lead to significant financial loss, while excessive false alarms can harm user experience.

**Objective**:
- Predict whether a transaction is fraudulent (`isFraud = 1`) or legitimate (`isFraud = 0`)
- Prioritize **high recall for fraud detection**
- Maintain reasonable **precision** to reduce false positives

---

## 📊 Dataset

- **Source**: Kaggle – Online Payments Fraud Detection Dataset  
  https://www.kaggle.com/datasets/rupakroy/online-payments-fraud-detection-dataset
- **Size**: ~6.3 million transactions
- **Features**: Transaction amount, balances before/after transfer, transaction type, time step
- **Imbalance**: Fraud accounts for ~0.1% of all transactions

This dataset is synthetic but designed to closely resemble real-world online payment behavior.

---

## 🔍 Exploratory Data Analysis

Key observations:
- Fraud occurs almost exclusively in `TRANSFER` and `CASH_OUT` transactions
- Balance-related features show extreme outliers and strong non-linear patterns
- Linear correlations with fraud are weak, motivating non-linear models

---

## 🛠 Feature Engineering

To capture fraud-specific behavior, the following features were engineered:

- **Balance inconsistency features**:
  - `errorBalanceOrig`
  - `errorBalanceDest`

These features measure deviations from expected balance updates and strongly correlate with fraudulent behavior, reflecting common account-draining patterns.

---

## 🤖 Models Evaluated

Three models were trained and compared:

1. **Logistic Regression**  
   - Serves as a baseline
   - Achieves high fraud recall but produces excessive false positives

2. **Random Forest**  
   - Captures complex feature interactions
   - Achieves near-perfect performance but may overfit highly predictive engineered features

3. **CatBoost (Gradient Boosting)**  
   - Industry-grade model optimized for tabular data
   - Provides the best balance between recall and precision
   - Demonstrates strong generalization and stable performance

---

## 📈 Evaluation Metrics

- Precision, Recall, F1-score
- Confusion Matrix
- ROC Curve and AUC

**Key Result**:
CatBoost achieves near-perfect fraud recall with high precision, offering the most practical solution among the evaluated models.

---

## 🧠 Key Insights

- Fraud is characterized by **abrupt balance inconsistencies**
- Transaction type plays a critical role in fraud risk
- Machine learning models outperform simple rule-based systems by combining multiple signals

---

## 🚀 Practical Recommendations

- Focus monitoring efforts on `TRANSFER` and `CASH_OUT` transactions
- Use balance consistency checks as early warning signals
- Tune decision thresholds based on business cost trade-offs
- Periodically retrain models to adapt to evolving fraud strategies

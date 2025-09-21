🕵️ Fraud Detection with a Two-Stage ML Pipeline
Summary:
This project demonstrates a real-world fraud detection pipeline built on credit card transaction data. Fraud is rare (<1% of cases), so the challenge is to catch nearly all fraudulent activity (high recall) while minimizing false alarms that frustrate customers.
I designed a two-stage approach:
Stage 1 (XGBoost): casts a wide net, capturing almost all fraud.
Stage 2 (Random Forest): refines predictions only on flagged cases, greatly improving precision.
The result is a pipeline that balances business risk (don’t miss fraud) with customer experience (don’t block legitimate transactions).

This project highlights my ability to:
Build end-to-end machine learning pipelines.
Engineer domain-specific features (transaction distance, timing, customer spending patterns).
Optimize models with a focus on business impact, not just raw accuracy.

Detailed Overview:
Credit card fraud is rare but costly. Detecting it requires models that maximize recall (catching all fraud) without overwhelming customers and banks with false alarms.
In this project, I build a two-stage fraud detection pipeline:
Stage 1 (Broad Net): An XGBoost classifier tuned for very high recall (~0.98).
Analogy: like a medical screening test (e.g., PSA for prostate cancer).
Goal: catch nearly all fraud, even if it means some false positives.
Stage 2 (Refinement): A Random Forest classifier applied only to Stage 1 positives.
Analogy: like a confirmatory test (e.g., biopsy).
Goal: improve precision by filtering out false positives.
This mirrors real-world fraud pipelines: start broad, then refine.

Key Challenges
Class imbalance: Fraud cases are <1% of transactions.
Cost asymmetry: Missing fraud (false negatives) is much worse than wrongly flagging a legitimate transaction (false positives).
Customer impact: Over-flagging leads to poor user experience.
Results
Stage 1 (XGBoost Only)
Recall: ~0.98
Precision: ~0.14
Takeaway: Excellent fraud capture, but too many false alarms.
Two-Stage Pipeline (XGBoost → Random Forest)
Confusion Matrix:
[[67525    41]
 [   57   299]]
Recall: 0.84 (most fraud still caught)
Precision: 0.88 (false positives cut dramatically)
F1-Score (Fraud class): 0.86
Accuracy: ~99.8% (Not that accuracy matters much in this type of problem with rare classes)

Features Engineered
Transaction timing: time since last transaction, transaction hour/day.
Geography: transaction distance (lat/lon).
Customer profiling: mean transaction amount, z-score normalized amounts.
Demographics: age (derived from DOB).

Tech Stack
Python: pandas, numpy, scikit-learn, XGBoost
Modeling: Random Forest, Gradient Boosting (XGB)
Visualization: seaborn, matplotlib
Evaluation: precision-recall curves, confusion matrices, F1/F2 scoring

This project shows how to:
Design pipelines that reflect business risk tradeoffs.
Engineer domain-specific features to boost fraud detection.
Use a layered modeling approach to balance recall and precision.
Communicate technical results in an intuitive, business-facing way.
Next Steps
Hyperparameter tuning with cross-validation.
Experiment with alternative second-stage models (Logistic Regression, LightGBM).
Explore unsupervised anomaly detection as an auxiliary signal.

⚡ Impact: A bank could use this pipeline to cut false alarms by >85% while still catching nearly all fraud.

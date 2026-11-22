<div align="center">

  <h1>🛡️ Intrusion Detection System (IDS) using ML Algorithms</h1>

  <p>
    An end-to-end Machine Learning pipeline designed to classify network traffic and detect malicious intrusions using the <strong>KDD Cup '99 Dataset</strong>.
  </p>

  <p>
    <a href="https://github.com/riminipa16/Intrusion-Detection-System-using-ML-algorithms">
      <img src="https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python Version" />
    </a>
    <a href="https://scikit-learn.org/">
      <img src="https://img.shields.io/badge/scikit--learn-F79A3E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="scikit-learn" />
    </a>
    <a href="https://pandas.pydata.org/">
      <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas" />
    </a>
    <a href="https://colab.research.google.com/github/riminipa16/Intrusion-Detection-System-using-ML-algorithms/blob/main/Intrusion_Detection_System_Using_ML_Algorithms.ipynb">
      <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" />
    </a>
  </p>

  ---
</div>

## 📌 Project Overview

Network Security is a critical aspect of modern digital infrastructure. An **Intrusion Detection System (IDS)** acts as a defensive mechanism that monitors network traffic to identify suspicious activity and potential security threats. 

This project implements and evaluates multiple supervised Machine Learning algorithms to categorize network connection records as either **normal traffic** or one of several **cyberattack types**.

---

## 📊 Dataset Description

The project utilizes the **KDD Cup '99 Dataset** (10% subset), consisting of approximately 494,021 network connection records. Each connection contains **41 feature attributes** detailing connection duration, protocol, payload size, login attempts, and traffic error rates.

### Attack Categorization

The attack types present in the dataset are mapped into four major attack categories:

| Attack Category | Description | Included Attack Types |
| :--- | :--- | :--- |
| **DoS** (Denial of Service) | Exhausts system resources to prevent legitimate access. | `back`, `land`, `neptune`, `pod`, `smurf`, `teardrop` |
| **Probe** | Scans networks to gather vulnerability information. | `ipsweep`, `nmap`, `portsweep`, `satan` |
| **R2L** (Remote to Local) | Unauthorized access from a remote machine. | `ftp_write`, `guess_passwd`, `imap`, `multihop`, `phf`, `spy`, `warezclient`, `warezmaster` |
| **U2R** (User to Root) | Local privilege escalation to superuser access. | `buffer_overflow`, `loadmodule`, `perl`, `rootkit` |
| **Normal** | Standard, non-malicious network traffic. | `normal` |

---

## ⚙️ Pipeline & Workflow

```
┌─────────────────┐     ┌──────────────────┐     ┌──────────────────────┐
│ Raw Network     │ ──> │ Data             │ ──> │ Feature Encoding     │
│ Connection Logs │     │ Preprocessing    │     │ & Min-Max Scaling    │
└─────────────────┘     └──────────────────┘     └──────────────────────┘
                                                            │
                                                            ▼
┌─────────────────┐     ┌──────────────────┐     ┌──────────────────────┐
│ Model           │ <── │ Multi-Model      │ <── │ Train / Test         │
│ Evaluation      │     │ Training         │     │ Split                │
└─────────────────┘     └──────────────────┘     └──────────────────────┘
```

1. **Data Ingestion & Formatting:** Appending feature names (`kddcup.names.txt`) and setting target labels.
2. **Attack Mapping:** Mapping 22 specific attack labels into 5 broader classes (`Normal`, `DoS`, `Probe`, `R2L`, `U2R`).
3. **Data Cleaning & Verification:** Checking for missing/null values across all columns.
4. **Feature Encoding & Scaling:** One-Hot Encoding categorical features (`protocol_type`, `service`, `flag`) and applying `MinMaxScaler` to continuous features.
5. **Model Training & Evaluation:** Training multiple classifiers and evaluating accuracy and execution timing.

---

## 🤖 Models Evaluated

The following algorithms are implemented and benchmarked:

* **Naive Bayes** (`GaussianNB`)
* **Decision Tree** (`DecisionTreeClassifier`)
* **Random Forest** (`RandomForestClassifier`)
* **Gradient Boosting** (`GradientBoostingClassifier`)
* **Support Vector Machine** (`SVC`)
* **Logistic Regression** (`LogisticRegression`)

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.8+ installed along with the required dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/riminipa16/Intrusion-Detection-System-using-ML-algorithms.git
   cd Intrusion-Detection-System-using-ML-algorithms
   ```

2. **Download Dataset Files:**
   Ensure the following files are present in your project directory:
   * `kddcup.data_10_percent_corrected`
   * `kddcup.names.txt`
   * `training_attack_types.txt`

3. **Run the Notebook:**
   Launch Jupyter Notebook or Google Colab:
   ```bash
   jupyter notebook Intrusion_Detection_System_Using_ML_Algorithms.ipynb
   ```

---

## 📈 Results & Key Findings

*Detailed model performance benchmarks (Accuracy, Precision, Recall, and Execution Time) are computed inside the notebook.*

---

## 🤝 Contributing

Contributions are welcome! Feel free to open an **issue** or submit a **Pull Request** if you want to add new algorithms, perform feature selection (e.g., using Chi-Square or Random Forest feature importance), or improve visualization techniques.

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).

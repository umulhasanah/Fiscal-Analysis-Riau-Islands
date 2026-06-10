# 🏛️ Regional Government Fiscal Performance Analysis
### Riau Islands Province, Indonesia (2018–2022)

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![SQL](https://img.shields.io/badge/SQL-Data%20Querying-lightblue?logo=postgresql)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Domain](https://img.shields.io/badge/Domain-Public%20Finance-purple)
![Data](https://img.shields.io/badge/Data-Real%20%7C%20Official%20LRA-darkgreen)

> **Author:** Umul Hasanah, S.M.  
> **LinkedIn:** [linkedin.com/in/umul-hasanah](https://linkedin.com/in/umul-hasanah)  
> **Tools:** Python · Pandas · Matplotlib · SQL  
> **Data Source:** Official Budget Realization Reports (LRA) — BPKAD Riau Islands Province  
> **Based on:** Undergraduate Thesis — Universitas Riau Kepulauan, 2024 (GPA 3.75 / Cum Laude)

---

## 📌 Project Overview

This project analyzes the **fiscal performance of the Riau Islands Provincial Government** using four key financial ratios derived from official regional budget realization reports (Laporan Realisasi Anggaran / LRA) spanning **5 fiscal years (2018–2022)**.

> ⚠️ **This project uses real government data** — not a simulated dataset. Data was sourced directly from the Regional Financial and Asset Management Agency (BPKAD) of Riau Islands Province as part of original undergraduate thesis research.

This repository is the **Python-based analytical reproduction** of my undergraduate thesis, originally written as an academic paper. The goal is to demonstrate how the same research can be translated into a data analytics workflow using modern tools — making the findings more visual, reproducible, and accessible.

**Why Riau Islands?** As an archipelagic province with limited local economic activity outside of Batam's Special Economic Zone, Riau Islands faces a unique challenge: how to grow fiscal independence while still heavily relying on central government transfers. This analysis tracks that challenge across five years.

---

## ❓ Research & Policy Questions

1. How fiscally independent is the Riau Islands Provincial Government?
2. Is the province effectively collecting its budgeted local revenue (PAD)?
3. How efficient is the province in managing its expenditures?
4. What is the 5-year trend in fiscal decentralization — improving or stagnating?
5. Which fiscal areas need the most policy attention?

---

## 📐 Financial Ratios Explained

| Ratio | Formula | Interpretation |
|-------|---------|---------------|
| **Fiscal Decentralization** | PAD ÷ Total Revenue × 100% | Higher = more self-funded development |
| **Fiscal Independence** | PAD ÷ Central Transfers × 100% | Higher = less reliant on central gov't |
| **PAD Effectiveness** | Realized PAD ÷ Budgeted PAD × 100% | Higher = better revenue realization |
| **Fiscal Efficiency** | Total Expenditure ÷ Total Revenue × 100% | Lower = more efficient spending |

**Criteria Reference (Mahmudi, 2010 & Hanafi, 2005):**

| Ratio | Range | Category |
|-------|-------|----------|
| Decentralization | > 50% | Very Good |
| Decentralization | 40–50% | Good |
| Decentralization | 30–40% | Sufficient |
| Decentralization | 20–30% | Moderate |
| Independence | > 75% | Very High |
| Independence | 50–75% | High / Moderate |
| Independence | 25–50% | Moderate / Low |
| Effectiveness | > 100% | Very Effective |
| Effectiveness | 90–100% | Effective |
| Efficiency | < 60% | Very Efficient |
| Efficiency | 60–100% | Efficient |
| Efficiency | > 100% | Inefficient |

---

## 📁 Dataset

> **Data source:** Official LRA (Laporan Realisasi Anggaran) reports published by BPKAD Riau Islands Province, 2018–2022. Data collected as primary research for undergraduate thesis at UNRIKA.

| Column | Description |
|--------|-------------|
| `year` | Fiscal year (2018–2022) |
| `local_own_revenue_pad` | Pendapatan Asli Daerah / PAD (IDR) |
| `total_revenue` | Total regional revenue (IDR) |
| `central_transfers` | Dana Transfer dari Pemerintah Pusat (IDR) |
| `budget_pad` | Budgeted PAD target (IDR) |
| `realized_pad` | Actual PAD realized (IDR) |
| `total_expenditure` | Total regional expenditure / Belanja Daerah (IDR) |
| `decentralization_ratio_pct` | Calculated decentralization ratio (%) |
| `independence_ratio_pct` | Calculated independence ratio (%) |
| `effectiveness_ratio_pct` | Calculated PAD effectiveness ratio (%) |
| `efficiency_ratio_pct` | Calculated fiscal efficiency ratio (%) |

📄 [Download Dataset](data/riau_islands_fiscal_data_REAL.csv)

---

## 🔍 Analysis Workflow

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load real government data
df = pd.read_csv('riau_islands_fiscal_data_REAL.csv')

# Verify all four ratios from raw figures
df['decentralization_check'] = (df['local_own_revenue_pad'] / df['total_revenue'] * 100).round(2)
df['independence_check']     = (df['local_own_revenue_pad'] / df['central_transfers'] * 100).round(2)
df['effectiveness_check']    = (df['realized_pad'] / df['budget_pad'] * 100).round(2)
df['efficiency_check']       = (df['total_expenditure'] / df['total_revenue'] * 100).round(2)
```

📓 [View Full Notebook](notebooks/fiscal_analysis_REAL.ipynb)

---

## 📊 Key Findings

### 1. All Four Ratios — 5-Year Trend

![All Ratios Trend](charts/all_ratios_trend.png)

> 💡 **Finding:** Four distinct performance patterns emerge across 2018–2022. PAD Effectiveness (green) consistently leads above 100%, while Fiscal Efficiency (red) also stays above 100% — but in an unfavorable way, indicating persistent overspending. Decentralization (dark blue) and Independence (light blue) both show gradual improvement.

---

### 2. PAD vs Total Revenue Growth

![PAD vs Revenue](charts/pad_vs_revenue.png)

> 💡 **Finding:** PAD grew from **IDR 1.22 Trillion (2018)** to **IDR 1.68 Trillion (2022)** — a **+37.3% increase** over five years. However, PAD still represents only 34–43% of total revenue, meaning the province remains significantly dependent on central government transfers to fund operations.

---

### 3. Fiscal Decentralization with Criteria Zones

![Decentralization Zones](charts/decentralization_zones.png)

> 💡 **Finding:** The province spent 2018–2021 in the **"Sufficient"** zone (30–40%), then broke into the **"Good"** zone in 2022 at 42.77% — the first meaningful milestone in 5 years. This reflects the significant PAD growth in 2022, driven by improved tax collection and economic recovery post-COVID.

---

## 📈 Summary Results (2018–2022)

| Year | Decentralization | Criteria | Independence | Criteria | Effectiveness | Criteria | Efficiency | Criteria |
|------|-----------------|----------|--------------|----------|--------------|----------|------------|----------|
| 2018 | 34.88% | Sufficient | 53.59% | Moderate | 106.86% | Very Effective | 102.35% | Inefficient |
| 2019 | 33.30% | Sufficient | 49.94% | Moderate | 104.09% | Very Effective | 107.81% | Inefficient |
| 2020 | 34.02% | Sufficient | 51.60% | Moderate | 102.55% | Very Effective | 91.16% | Efficient ✅ |
| 2021 | 36.11% | Sufficient | 57.17% | Moderate | 95.80% | Effective | 102.86% | Inefficient |
| 2022 | 42.77% | **Good** ⬆️ | 74.77% | Moderate | 116.00% | Very Effective | 101.97% | Inefficient |
| **Avg** | **36.22%** | Sufficient | **57.41%** | Moderate | **105.06%** | Very Effective | **101.23%** | Inefficient |

---

## 💡 Policy Recommendations

| # | Finding | Recommendation |
|---|---------|---------------|
| 1 | Decentralization ratio still mostly Sufficient (30–40%) | Develop **trade, manufacturing, and maritime sectors** to grow PAD beyond Batam-centric revenue |
| 2 | Independence ratio plateaued at Moderate despite improvement | Educate communities on **natural resource management** to increase local revenue participation |
| 3 | PAD Effectiveness consistently Very Effective (>100%) | **Sustain and optimize** existing PAD collection mechanisms; 2021 dip linked to COVID-19 warrants contingency planning |
| 4 | Fiscal Efficiency Ratio persistently Inefficient (>100%) | **Deploy regional officials by field expertise** to reduce unnecessary expenditure; study 2020 efficiency success (91.16%) |

---

## 🗂️ Repository Structure

```
fiscal-analysis-riau-islands/
│
├── 📁 data/
│   └── riau_islands_fiscal_data_REAL.csv    # Official LRA data 2018–2022
│
├── 📁 notebooks/
│   └── fiscal_analysis_REAL.ipynb           # Full Python analysis notebook
│
├── 📁 charts/
│   ├── all_ratios_trend.png                 # All 4 ratios in one chart
│   ├── pad_vs_revenue.png                   # PAD vs total revenue bar chart
│   └── decentralization_zones.png           # Decentralization with criteria zones
│
└── README.md
```

---

## ▶️ How to Run

**Option 1 — Google Colab (Recommended)**

1. Open [colab.research.google.com](https://colab.research.google.com)
2. Upload `fiscal_analysis_REAL.ipynb`
3. Upload `riau_islands_fiscal_data_REAL.csv` to the Colab file sidebar
4. Click **Runtime → Run All**

**Option 2 — Local**

```bash
git clone https://github.com/umul-hasanah/fiscal-analysis-riau-islands
cd fiscal-analysis-riau-islands
pip install pandas matplotlib
jupyter notebook notebooks/fiscal_analysis_REAL.ipynb
```

---

## 📚 References

- Mahmudi. (2010). *Manajemen Keuangan Daerah*. Erlangga.
- Hanafi, I. (2005). *Analisis Rasio Keuangan Pemerintah Daerah*. BPFE.
- BPKAD Provinsi Kepulauan Riau. (2018–2022). *Laporan Realisasi Anggaran (LRA).*
- Mardiasmo. (2009). *Akuntansi Sektor Publik*. Andi Offset.

---

## 👩‍💼 About the Author

**Umul Hasanah, S.M.**  
Bachelor of Management — Financial Management Concentration  
Universitas Riau Kepulauan (GPA 3.75 / 4.00, Cum Laude) | Graduated March 2024

**Thesis Title:**  
*"Analisis Rasio Derajat Desentralisasi Fiskal, Rasio Kemandirian, Rasio Efektivitas PAD, dan Rasio Efisiensi Keuangan Daerah dalam Mengukur Kinerja Keuangan Daerah Pemerintah Provinsi Kepulauan Riau"*

4+ years of experience as Administrative Staff Coordinator at Etama Dental Clinic, Batam — with hands-on expertise in financial recording, budgeting, and operational reporting. Certified in Full Stack Data Analytics (RevoU, 2024).

🔗 [LinkedIn](https://linkedin.com/in/umul-hasanah) · 💻 [GitHub](https://github.com/umul-hasanah) · ✉️ umulhasanah30@gmail.com

---

*Data sourced from official LRA reports published by BPKAD Riau Islands Province. This repository is intended for portfolio and educational purposes.*

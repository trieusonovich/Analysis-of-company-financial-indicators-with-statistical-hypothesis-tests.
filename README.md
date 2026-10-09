# Analysis of Company Financial Indicators: Statistical Hypothesis Tests

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-data%20analysis-150458?logo=pandas&logoColor=white)
![scipy](https://img.shields.io/badge/scipy-hypothesis%20testing-8CAAE6?logo=scipy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

A financial statistics project that analyzes the financial indicators of 100 companies over the past year using statistical hypothesis tests. The workflow covers exploratory data analysis, correlation and distribution analysis, and seven hypothesis tests (one-sample, two-sample, paired, proportion, and non-parametric) at a significance level of α = 0.05.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Key Results](#key-results)
- [Hypothesis Test Summary](#hypothesis-test-summary)
- [Author](#author)

---

## Overview

Company financial indicators reflect both internal management decisions and external market conditions. This project applies statistical inference to answer a focused question: **do ownership type and capital structure significantly affect company performance, and do the sample companies meet key economic benchmarks?**

**Objectives**

1. Explore and understand the financial indicators of 100 companies
2. Analyze correlations and distributions across indicators and ownership types
3. Test economic hypotheses on revenue, ROE, EBITDA, and debt ratios
4. Draw conclusions at a 5% significance level and interpret them economically

## Dataset

| Property | Value |
|---|---|
| Observations | 100 companies |
| Period | Last year (with previous-year debt ratio) |
| File | `financial_companies.csv` |
| Columns | `Ownership_Type`, `Revenue_Mln`, `EBITDA_Mln`, `Debt_Ratio`, `ROE_Percent`, `Debt_Ratio_Prev` |

**Variable descriptions**

- `Ownership_Type` — ownership type: `Private` (privately owned) or `Public` (publicly traded/listed)
- `Revenue_Mln` — revenue over the past year, in millions of RUB
- `EBITDA_Mln` — EBITDA over the past year, in millions of RUB
- `Debt_Ratio` — debt leverage ratio (debt-to-equity)
- `ROE_Percent` — return on equity, in percent
- `Debt_Ratio_Prev` — debt leverage ratio in the previous year

**Sample composition:** 63 private companies (63%) and 37 public companies (37%). No missing values.

## Methodology

**1. Exploratory analysis**
Descriptive statistics (mean, median, std, quartiles), data types, missing-value checks, and ownership distribution.

**2. Correlation and distribution analysis**
Correlation heatmap of numeric indicators and a pairplot colored by ownership type.

**3. Hypothesis testing** (α = 0.05)

- One-sample t-tests: mean revenue and mean ROE vs. benchmarks
- Independent two-sample t-tests: public vs. private EBITDA and debt ratio
- Paired t-test: debt ratio vs. previous year
- Proportion z-test: share of high-debt companies vs. 30%
- Mann–Whitney U test: ROE distributions of public vs. private companies

## Key Results

### Correlation highlights

| Pair | r | Interpretation |
|---|---|---|
| Revenue & EBITDA | 0.77 | Strong positive — higher revenue accompanies higher operating earnings |
| ROE & Debt Ratio | −0.67 | Higher debt burden associated with lower return on equity |
| Other pairs | ≈ 0 | Little to no linear relationship |

## Hypothesis Test Summary

| # | Hypothesis | Test | Statistic | p-value | Decision |
|---|---|---|---|---|---|
| H1 | Mean revenue > 480 mln RUB | One-sample t (greater) | t = 1.4487 | 0.0753 | Fail to reject H₀ |
| H2 | Mean ROE < 15% | One-sample t (less) | t = −29.4842 | ≈ 0.0000 | **Reject H₀** |
| H3 | Public EBITDA > Private EBITDA | Two-sample t (greater) | t = 0.0690 | 0.4726 | Fail to reject H₀ |
| H4 | Private debt ratio < Public debt ratio | Two-sample t (less) | t = −0.8745 | 0.1920 | Fail to reject H₀ |
| H5 | Debt ratio changed YoY | Paired t (two-sided) | t = −4.1229 | 0.0001 | **Reject H₀** |
| H6 | Share with Debt_Ratio > 2.0 = 30% | Proportion z-test | z = −6.0724 | ≈ 0.0000 | **Reject H₀** |
| H7 | ROE distributions differ by type | Mann–Whitney U | U = 1047.0 | 0.3995 | Fail to reject H₀ |

**Economic interpretation of the significant results**

- **H2 (ROE < 15%):** Mean ROE is significantly below 15%, suggesting inefficient equity management, a high debt burden eroding profits, or unfavorable macroeconomic conditions.
- **H5 (debt ratio changed):** A statistically significant year-over-year change occurred. Since the mean difference is negative, companies are **reducing leverage** — repaying debt and lowering financial risk.
- **H6 (high-debt share):** The actual proportion of companies with a debt ratio above 2.0 is significantly **below 30%**, indicating more conservative financial policies or more limited access to credit in the sample.

**Overall conclusion:** Based on the available sample, there is insufficient statistical evidence to establish clear differences between private and public companies in EBITDA, debt ratio, or ROE. Mean revenue is broadly consistent with the benchmark, while mean ROE is significantly below 15%. Capital structures shifted downward year over year, and high-debt companies are less common than the 30% benchmark.

## Author
Nguyen Dinh Trieu

Economics (Analytical Economics and Econometrics)

trieu31072004@gmail.com

## Repository Structure

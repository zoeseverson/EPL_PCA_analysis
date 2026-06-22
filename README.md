# Predicting EPL Player Goal Scoring Using PCA and Machine Learning
### English Premier League • 2024–2025 Season • 562 Players • 57 Variables

## Overview
This project analyzes player performance data from the English Premier League (EPL) 2024–2025 season to answer the question:

**How well do principal components derived from EPL performance statistics predict total goals scored?**

Using a dataset of 562 players and 57 variables from the SCORE sports data repository, the analysis explores offensive, defensive, disciplinary, and goalkeeper metrics to understand how underlying performance patterns relate to goal scoring. Principal Component Analysis (PCA) is used to reduce dimensionality before fitting predictive models.

---

## Dataset
The dataset includes:
- Player information: team, nationality, position  
- Offensive metrics: shots, goals, assists, xG, shot accuracy  
- Defensive metrics: tackles, interceptions, blocks  
- Discipline: fouls, yellow/red cards, errors  
- Goalkeeper metrics: saves, save percentage, goals conceded, goals prevented  

Preprocessing steps:
- Converted percentage columns to numeric  
- Removed Player Name, Club, and Nationality (not predictive of goals)  
- Split data into 80% training and 20% testing sets  

---

## Exploratory Data Analysis
### Distribution of Goals
- The distribution of goals is extremely right‑skewed  
- Median = 0 goals  
- 75% of players scored two or fewer goals  
- A small group of forwards accounts for most scoring  

This imbalance reflects positional roles and highlights the difficulty of predicting goals.

### Key EDA Findings
- Shots and goals show a positive but noisy relationship  
- Many performance metrics are correlated  
- PCA is appropriate for reducing redundancy and improving model efficiency  

---

## Dimensionality Reduction (PCA)
PCA was applied after:
- Dummy‑encoding categorical variables  
- Removing zero‑variance predictors  
- Normalizing numeric predictors  

Principal components explaining **95% of total variance** were retained.

---

## Models
Three models were trained using the PCA‑transformed predictors:

### Multiple Regression (Elastic Net)
- Training R²: **0.664**  
- Testing R²: **0.425**  
- Mild overfitting  

### Random Forest Regressor
- Training R²: **0.907**  
- Testing R²: **0.487**  
- Highest test performance but severe overfitting  

### SVM Regressor (RBF Kernel)
- Training R²: **0.646**  
- Testing R²: **0.415**  
- Similar performance to regression  

---

## Model Comparison

| Model | Train R² | Test R² | Notes |
|-------|----------|---------|-------|
| Elastic Net Regression | 0.664 | 0.425 | Mild overfitting |
| Random Forest | 0.907 | 0.487 | Best test R²; severe overfitting |
| SVM (RBF) | 0.646 | 0.415 | Moderate fit |

The random forest model achieved the highest testing R² but showed the most overfitting.

---

## Conclusion
Across all models, testing R² values ranged from **0.41 to 0.49**, meaning PCA‑derived components explain **roughly 41–49% of the variation in goals scored**.

Key takeaways:
- PCA captures meaningful structure in EPL performance metrics  
- Goal scoring remains difficult to predict due to positional differences and low scoring frequency  
- Random forest performed best overall, but all models showed some overfitting  

PCA helped reduce dimensionality and highlight broad trends, but additional contextual variables (minutes played, tactical role, xG chain, etc.) would likely improve predictive accuracy.

---

## Repository Structure

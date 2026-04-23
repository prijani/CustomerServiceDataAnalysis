# Spotify Track Analysis and Popularity Prediction

This project explores a dataset of over 110,000 Spotify tracks to identify the mathematical patterns that drive musical popularity. Using Python's statistical and machine learning libraries, the study analyzes audio features (such as danceability, energy, and valence) to predict hits and group tracks into distinct musical categories.

## Dataset

The data used in this project is the **Spotify Tracks Dataset** sourced from [Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset). It contains 114,000+ tracks with 21 columns of metadata and audio-engineered features provided by the Spotify Web API.

## Repository Structure

### 1. Preprocessing&Visual.ipynb

This notebook serves as the **Data Engineering and Exploratory Data Analysis (EDA)** phase of the project.

* **Data Cleaning:** Handling missing values, removing duplicates, and feature engineering (e.g., converting duration from milliseconds to minutes).

* **Outlier Detection:** Identifying anomalies in track duration and popularity using IQR and Z-score methods.

* **Visualizations:** Distribution plots of audio features, correlation heatmaps, and genre-based popularity comparisons.

* **Text Analysis:** A Word Cloud visualization of album titles and track names to identify common branding themes.

### 2. Analysis.ipynb

This notebook contains the **Advanced Statistical Modeling** and machine learning workflows.

* **Multiple Linear Regression (OLS):** An investigation into which audio features are statistically significant predictors of popularity. This includes checks for Multicollinearity (VIF) and interpretation of p-values.

* **Logistic Regression:** A classification model designed to predict whether a track will be a "Hit" (above median popularity) based on its musical key and audio profile. Evaluation is performed using Confusion Matrices and ROC-AUC scores.

* **K-Means Clustering:** An unsupervised learning approach to group songs into "Musical Tribes." This section utilizes feature scaling (L2 Norms) and centroid analysis to define distinct clusters of sound regardless of metadata labels.

### 3. Predictions.ipynb

This notebook includes **non-linear algorithms** and **multiclass predictions**.

* **Random Forest Regression:** Predicts exact popularity scores, comparing performance against baseline linear models.

* **High-Threshold Hit Prediction:** A Logistic Regression model identifying top-tier chart hits (Popularity $\ge$ 70).

* **Acoustic Profiling (Classification):** Utilizes Random Forest Classifiers to predict whether a track is "Explicit" and correctly classify songs into their top 5 respective genres based purely on their instrumental and rhythmic features.

## Methods and Tools Used

* **Languages:** Python (Jupyter Notebook)

* **Data Manipulation:** Pandas, NumPy

* **Statistical Modeling:** Statsmodels (OLS Regression, VIF calculation)

* **Machine Learning:** Scikit-Learn

  * **Regression:** Multiple Linear Regression, Random Forest Regressor

  * **Classification:** Logistic Regression, Random Forest Classifier

  * **Unsupervised:** K-Means Clustering, PCA

  * **Utilities:** StandardScaler, 10-Fold Cross-Validation, Feature Importance Analysis

* **Visualization:** Matplotlib, Seaborn, WordCloud

## Key Findings

### Regression Results

While audio features like danceability and loudness are statistically significant (p < 0.05), linear relationships only account for a small fraction of a song's success (R-squared ~ 0.02). Transitioning to non-linear models (Random Forest) improved predictive power significantly (explaining ~22% of the variance), but ultimately confirms that external factors such as marketing and artist fame are the primary drivers of massive popularity.

### Classification Success

Using a Median Split to ensure balanced classes, the initial Logistic Regression model achieved an accuracy of 57% and an ROC-AUC of 0.58. This indicates that while music popularity is chaotic, audio features provide a predictive advantage over random chance. Furthermore, logistic coefficients revealed that high instrumentalness and acousticness actively hurt a track's chances of becoming a mainstream hit.

### Advanced Predictive Profiling

The Random Forest classifiers successfully decoded distinct acoustic signatures within the data:

* **Explicit Content:** The model identified explicit tracks with **81% accuracy** without performing any text analysis on the lyrics, utilizing features like speechiness and danceability.

* **Genre Classification:** The algorithm successfully distinguished between the top 5 most common genres with **77% accuracy**, proving that genres like 'House' and 'Pagode' have highly rigid mathematical structures.

### Unsupervised Discovery

K-Means successfully identified three distinct profiles in modern music:

1. **The Unplugged:** High acousticness and low energy.

2. **The High-Energy:** High energy with lower valence and acousticness.

3. **The Feel-Good Hits:** High danceability and high valence.

**Authors:** Priya Jani, Vanna Q, Cole Decker

**Date:** April 2026

**Course:** Statistical Data Analysis

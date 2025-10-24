# cancer-drug-response-prediction
# Predicting Drug Sensitivity in Breast Cancer Using GDSC Data
A linear regression model to predict drug sensitivity (LN_IC50) in breast cancer cell lines using GDSC data.

# Run this notebook
This notebook can be easily run on any device as it onlu needs one input (you need to upload your kaggle api json file when prompted)

## Project Overview

In this project i have used the GDSC (Genomics of Drug Sensitivity in Cancer) Dataset. This data was collected by the Genomics of Drug Sensitivity in Cancer project, a collaboration between the Sanger Institute (UK) and the Massachusetts General Hospital Cancer Center (USA). The project involves large-scale screening of human cancer cell lines with a wide range of anti-cancer drugs. Data was collected through large-scale screening of human cancer cell lines with various anti-cancer drugs. Cell viability was measured using CellTiter-Glo assay after 72 hours of drug treatment.

The full GDSC Dataset is very large and incorporates various cancer types and hundreds of anti-cancer drugs. Here  i have restricted this Dataset to only include one specific cancer type (e.g. Breast Cancer) to build a simple LinearRegression Model which predicts drug response specifically for breast cancer.

The datasets can be accessed and downloaded from the GDSC website: https://www.cancerrxgene.org/

## Biological Context and Motivation

Drug sensitivity in cancer varies significantly between individuals, even for the same cancer type. By analyzing data from large-scale screens like GDSC, computational methods can help identify patterns that predict how effective a drug might be. This project focuses specifically on breast cancer cell lines to investigate how drug concentration and other properties correlate with sensitivity.

## Methodology

The project follows a standard machine learning workflow:
1.  **Data Acquisition**: I downloaded the required data files from Kaggle
2.  Data files can be accessed using this link (https://www.kaggle.com/datasets/samiraalipour/genomics-of-drug-sensitivity-in-cancer-gdsc?resource=download&select=GDSC_DATASET.csv)
3.  One excel file which contained cell line details (`Cell_Lines_Details.xlsx`) and two separate CSV files were used, one containing drug sensitivity and cancer type (`GDSC_DATASET.csv`), and another containing drug concentration details (`GDSC_dataset2.csv`).
4.  **Data Preparation**:
    *   The datasets were merged using a common `DRUG_ID`.
    *   The data was filtered to include only breast cancer cell lines (`TCGA_DESC == 'BRCA'`).
    *   Missing values were handled, and categorical features were one-hot encoded.
    *   In this data `LN_IC50`is used, which is a continuous variable so a Linear Regression Model was preferred. 
5.  **Model Training**: A `LinearRegression` model was trained to predict the `LN_IC50` value. A `scikit-learn` pipeline was used to ensure consistency in preprocessing.
6.  **Evaluation**: The model's performance was evaluated using standard regression metrics (R-squared, RMSE) and a visualization comparing predicted versus actual values.

## Key Findings

The linear regression model achieved an **R-squared of 0.7231**, indicating that it explains over 72% of the variance in drug sensitivity for breast cancer cell lines. This suggests a strong predictive relationship based on the selected features.

## Visualizations

The scatter plot below compares the model's predicted `LN_IC50` values against the actual values. Points that lie close to the diagonal line indicate accurate predictions.

assets/regplot.png

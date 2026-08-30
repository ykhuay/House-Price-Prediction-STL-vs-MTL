# STL-vs-MTL-House-Price-Prediction

# House Price Prediction: STL vs MTL

## Overview

This project investigates the performance of Single-Task Learning (STL) and
Multi-Task Learning (MTL) approaches for house price prediction.

We compare three models:

- Ridge Regression (STL)
- Random Forest (STL)
- Multi-Task Learning with L₂,₁ regularisation (MTL)

The models are trained and evaluated using the House Sales in King County, USA
dataset from Kaggle.

## Project Objectives

The main objectives of this project are to:

- Compare STL and MTL approaches for house price prediction
- Implement an L₂,₁-regularised MTL model
- Investigate whether MTL can outperform traditional STL models
- Analyse how task definition and dataset characteristics affect MTL performance

## Dataset

We use the House Sales in King County, USA dataset.

The dataset contains 21,613 housing records with structural and geographical
features such as:

- Living area
- Number of bedrooms and bathrooms
- House grade and condition
- Latitude and longitude
- Year built

Dataset source:
https://www.kaggle.com/datasets/harlfoxem/housesalesprediction

## Models

### 1. Ridge Regression

Ridge Regression is used as a linear STL baseline. L₂ regularisation is applied
to improve model stability and reduce overfitting.

### 2. Random Forest

Random Forest is used as a non-linear STL baseline. The model uses 100 decision
trees and can capture non-linear relationships between housing features.

### 3. Multi-Task Learning

Our MTL model uses an L₂,₁-regularised linear framework.

The dataset is divided into 8 tasks based on:

- 4 geographical clusters obtained using K-means
- 2 house-size groups based on `sqft_living`

This produces 4 × 2 = 8 spatial-structural tasks.

The MTL model learns task-specific weight vectors while applying L₂,₁
regularisation to encourage shared feature selection across tasks.

## Data Preprocessing

The preprocessing pipeline includes:

1. Data cleaning
2. Exploratory data analysis
3. Feature engineering
4. Log transformation
5. Train-test splitting
6. Feature scaling

Additional features include house age, renovation status, basement status,
and cyclic month encoding.

The dataset is split into 70% training and 30% testing data.

## Results

The three models were evaluated using:

- RMSE
- MAE
- R²

Based on our experiments:

**Random Forest performed the best overall**, followed by MTL L₂,₁ and Ridge
Regression.

The results suggest that the effectiveness of MTL depends strongly on the
quality of the task definitions and the richness of the available dataset.

## Key Findings

Our results show that MTL does not automatically outperform STL.

While the MTL model was able to learn some region- and size-specific patterns,
the Random Forest model performed better because it could capture complex
non-linear relationships in the dataset.

The relatively limited contextual and geographical information in the
King County dataset also made it difficult for the MTL approach to fully
exploit shared task relationships.

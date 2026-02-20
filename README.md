# DeepLearning_Lab
# Movie Text Modeling with GloVe Embeddings

Name: Samay Kharidia
Student ID: 202301433

Project Overview

This project explores text-based prediction tasks using pretrained GloVe embeddings and neural models. The goal is to evaluate how different textual inputs (overview, tagline, keywords) contribute to:

Rating Prediction (Regression)

Genre Prediction (Multi-Label Classification)

Genre-specific word analysis

We use TF-IDF weighted GloVe document embeddings as input features.

Dataset

The dataset contains movie metadata including:

overview

tagline

keywords

genres

vote_average

Only these allowed columns were retained for modeling.

# Task 1 – Data Preparation
Preprocessing Steps

Convert text to lowercase

Remove URLs

Remove punctuation

Remove numbers

Tokenize

Remove stopwords

Optional lemmatization

Data Split

Reproducible split (random_state=42):

70% Training

15% Validation

15% Test

# Task 2 – GloVe Embedding Pipeline
Pretrained Embeddings Used

GloVe 100-dimensional vectors (glove.6B.100d.txt)

All experiments use 100D embeddings for consistency.

Embedding Coverage
Coverage
=
unique tokens found in GloVe
total unique tokens
Coverage=
total unique tokens
unique tokens found in GloVe
	​


Reported Coverage: XX.X%​


TF-IDF fitted on training data

Weighted average of word vectors

Output dimension = 100

# Task 3 – Model A: Rating Prediction (Regression)
Objective

Predict vote_average using document embeddings.

Model Architecture

Neural network:

Linear(100 → 128)

ReLU

Linear(128 → 1)

Loss Function

Mean Squared Error (MSE)

Evaluation Metrics

MSE

RMSE

Baseline

Predict global mean rating from training set.


Overview typically performs best due to richer semantic content.

Tagline often underperforms due to short length.

Keywords may improve genre-specific prediction.

# Task 4 – Model B: Genre Prediction (Multi-Label Classification)
Setup

Multi-hot encoding for genres

Output size = number of unique genres

Sigmoid activation

Loss

BCEWithLogitsLoss

Evaluation Metrics

Micro-F1

Macro-F1

Hamming Loss

Jaccard Score


Keywords often perform best for genre prediction.

Overview captures broader thematic context.

Taglines provide limited discriminative power.

Task 5 – Frequent Words per Genre

For each genre:

Compute top 10 most frequent content words

Compute bottom 10 least frequent words (min frequency ≥ 3)

Example (Action)

Top Words:

war

battle

mission

soldier

fight

explosion

army

hero

enemy

rescue

Interpretation:
Action films emphasize conflict, combat, and high-intensity themes.

# Task 6 – Genre-Indicative Words (TF-IDF + Logistic Regression)

Method:

Train one-vs-rest logistic regression per genre

Extract highest positive coefficient words

Example (Romance)

Indicative Words:

love

relationship

marriage

couple

heart

romance

affair

wedding

passion

emotional

Interpretation:
These words strongly signal emotional and relationship-driven narratives.

*Word Complexity Prediction for Romanian Language*



*Overview*

This project focuses on predicting the complexity score of Romanian words in context using Natural Language Processing (NLP) techniques and Machine Learning regression models.

The system extracts semantic, lexical, and grammatical features from target words and uses multiple regression algorithms to estimate a complexity score between 0 and 1.

The project was developed for the Word Complexity Prediction Challenge 2025 and evaluates different machine learning approaches to determine the most effective model.

*Features*

Romanian language processing using SpaCy
Contextual word embeddings
Automatic feature extraction
Part-of-speech (POS) analysis
Multiple regression models
Automatic model selection based on R² score
Submission file generation for competition evaluation
Technologies Used
Python
Pandas
NumPy
SpaCy (ro_core_news_lg)
Scikit-Learn
LightGBM
Project Pipeline
1. Data Loading

The project loads:

train.csv
test.csv

The training dataset contains:

sentence
target token
complexity score

while the test dataset contains only the input features.

2. Feature Extraction

For each target word, the following features are extracted:

Semantic Features
Contextual SpaCy embedding vector
Lexical Features
Word length
Uppercase indicator
Title-case indicator
Contains digits
Punctuation-only indicator
Grammatical Features
Adjective flag
Noun flag
Verb flag
Adverb flag

These features are combined into a single numerical representation used for training the models.

3. Data Preparation

The extracted features are transformed into a feature matrix by:

Collecting all embedding vectors
Creating additional linguistic features
Concatenating everything into a single input matrix

The dataset is then split into:

80% Training
20% Validation

for model evaluation.

4. Machine Learning Models

The following regression models are evaluated:

Ridge Regression
Support Vector Regression (SVR)
Gradient Boosting Regressor
LightGBM Regressor

Each model is trained inside a Scikit-Learn pipeline with feature standardization.

5. Model Selection

Performance is evaluated using the R² (coefficient of determination) metric.

The model achieving the highest validation score is automatically selected as the final predictor.

6. Prediction and Submission

The selected model is used to predict complexity scores for the test set.

Predictions are:

clipped to the interval [0,1]
saved in the required competition format

Output file:

submission.csv

Installation

Clone the repository:

git clone https://github.com/your-username/word-complexity-prediction.git
cd word-complexity-prediction

Install dependencies:

pip install pandas numpy scikit-learn spacy lightgbm

Download the Romanian SpaCy model:

python -m spacy download ro_core_news_lg
Running the Project

Place the datasets in the project directory:

train.csv
test.csv

Run:

python main.py

The script will:

Extract features
Train all models
Select the best performer
Generate predictions
Create submission.csv

*Results*

The project compares several regression techniques and automatically selects the model with the highest validation R² score.

This approach combines:

contextual semantic information
linguistic characteristics
machine learning regression

to estimate word complexity in Romanian text.

*Future Improvements:*
Transformer-based embeddings (Romanian BERT)
XGBoost integration
Hyperparameter optimization
Ensemble learning
Additional linguistic and psycholinguistic features

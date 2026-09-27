# Plagiarism Detection System

A machine learning-based system for detecting plagiarism in C/C++ source code using source-code tokenization, TF-IDF feature extraction, engineered code-length features, and Random Forest classification.

## Overview

Source-code plagiarism can be difficult to detect because students can modify variable names, formatting, comments, and other superficial elements while retaining similar program structure.

This project represents source code using token-level features and statistical representations and then classifies pairs of source files as plagiarized or non-plagiarized.

## Approach

The system follows the pipeline:

```text
C/C++ Source Code
        ↓
Comment Removal
        ↓
Source-Code Tokenization
        ↓
Stop-Token Removal
        ↓
TF-IDF Feature Extraction
        ↓
Source Length + Token Length Features
        ↓
Paired Code Representation
        ↓
Random Forest Classifier
        ↓
Plagiarism Classification
```

## Feature Engineering

The project extracts several types of information from source code.

### Source-Code Tokenization

The source files are processed to:

* Remove comments
* Tokenize C/C++ source code
* Remove selected punctuation and comment tokens
* Represent source code using meaningful tokens

### TF-IDF Features

TF-IDF is used to represent the frequency and importance of source-code tokens.

Each source file is converted into a numerical vector based on its token distribution.

### Additional Features

The system also incorporates:

* Normalized source-code length
* Normalized token count

These features are combined with the TF-IDF representation.

### Pair-Based Classification

The system creates pairs of source-code representations:

* Plagiarized pairs → label `1`
* Non-plagiarized pairs → label `0`

The combined pair representation is then provided to the classifier.

## Machine Learning Model

A **Random Forest Classifier** is used for plagiarism classification.

The implementation performs:

* Train/test splitting
* 5-fold cross-validation
* Model training
* Prediction
* Accuracy evaluation
* Recall evaluation
* F1-score evaluation
* Confusion-matrix analysis
* Learning-curve visualization

The experiment repeats the train/test process multiple times and aggregates the evaluation metrics.

## Technologies Used

* Python
* NumPy
* Pandas
* Scikit-learn
* TF-IDF
* Random Forest
* C/C++ tokenization
* Matplotlib
* Pickle
* tqdm

## Project Files

### `make_vector.py`

Responsible for:

* Reading source-code files
* Removing comments
* Tokenizing C/C++ code
* Removing selected stop tokens
* Creating TF-IDF representations
* Calculating source/token length statistics
* Creating paired code vectors
* Generating the feature dataset

### `classification.py`

Responsible for:

* Loading the generated feature dataset
* Splitting data into training and testing sets
* Training the Random Forest classifier
* Performing 5-fold cross-validation
* Calculating accuracy, recall and F1-score
* Generating the confusion matrix
* Saving the trained model

### `RNN_LSTM_CNN.py`

Contains additional experimental modelling work for source-code classification.

## Evaluation

The system evaluates the classifier using:

* Accuracy
* Recall
* F1-score
* Confusion Matrix
* Cross-validation score
* Learning curves

F1-score is particularly useful because it considers both precision and recall rather than relying only on accuracy.

## Requirements

Install the required Python packages:

```bash
pip install numpy pandas scikit-learn matplotlib tqdm
```

The project also uses the source-code tokenization and TF-IDF modules included/referenced by the implementation.

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/plagiarism-detection-system.git
cd plagiarism-detection-system
```

### 2. Prepare the source-code datasets

Create the required directories:

```text
plag_original_codes/
nonplag_original_codes/
```

Place the corresponding source-code files inside these directories.

### 3. Generate the feature dataset

Run:

```bash
python make_vector.py
```

This generates the feature representation used by the classifier.

### 4. Train and evaluate the classifier

Run:

```bash
python classification.py
```

The program performs cross-validation, trains the Random Forest model, evaluates it on test data, and reports classification metrics.

## Key Learning Outcomes

* Source-code preprocessing and tokenization
* Feature engineering for source-code analysis
* TF-IDF representation
* Pair-based classification
* Random Forest classification
* Cross-validation
* Confusion-matrix analysis
* Evaluation using accuracy, recall and F1-score

## Future Improvements

* Add AST-based source-code representations
* Compare multiple similarity measures
* Experiment with graph-based code representations
* Add more programming languages
* Compare Random Forest with transformer-based code models
* Build a web interface for uploading and comparing source files

## Author

**Boda Praveen**
B.Tech Electrical Engineering
Indian Institute of Technology Madras

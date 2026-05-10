# COVID-19 Twitter Sentiment Analysis

## Overview
This repository contains the codebase for analyzing public sentiment regarding the COVID-19 pandemic using Twitter data. The project relies on a dataset of over 450,000 tweets gathered using popular pandemic-related hashtags. This data serves as the foundation for in-depth exploratory data analysis (EDA) and sentiment classification.

The project is divided into core phases, primarily focusing on robust text pre-processing (Phase I) to remove noise, followed by textual and sentiment analysis (Phase II) to derive meaningful insights about public opinion.

## Project Workflow

### 1. Data Aggregation
* Merges multiple raw data files (`S-Covid-2021-1.csv` through `S-Covid-2021-9.csv`) into a single, comprehensive pandas DataFrame containing 450,000 tweets.
* Filters the dataset to isolate English-language tweets using `langdetect`.

### 2. Text Pre-processing (Phase I)
To ensure high-quality data for analysis, extensive text normalization is performed to remove unnecessary noise. Steps include:
* **Tokenization & Stop Word Removal:** Utilizes `NLTK` and `spaCy` (`en_core_web_sm`) to strip out standard English stop words.
* **Noise Reduction:** Uses Regular Expressions (`re`) to meticulously remove:
  * `@` User mentions
  * Website URLs (http/https/www)
  * Hashtag symbols (while retaining the textual tag)
  * Punctuation marks (hyphens, commas, colons, semi-colons, etc.)
* **Corpus Filtering:** Validates and retains only recognizable English words using the `nltk.corpus.words` dictionary.
* **Normalization:** Converts all text to lowercase for uniformity.
* **Output:** Saves the refined dataset as `S-Covid1-cleaned.csv` for downstream analysis.

### 3. Exploratory Data Analysis & Sentiment Classification (Phase II)
* **Word Cloud Generation:** Visualizes the most prominent themes in the cleaned dataset while filtering out specific vaccine-related keywords (e.g., Pfizer, Moderna, Covishield, AstraZeneca) to focus on broader sentiments.
* **Sentiment Analysis:** Implements the `NLTK VADER` (Valence Aware Dictionary and sEntiment Reasoner) Lexicon to calculate Polarity Scores.
  * Assigns **Positive**, **Negative**, and **Neutral** scores to every tweet.
  * Aggregates the scores to determine the overarching public sentiment (e.g., predominantly Neutral, Positive, or Negative).
* **Word Frequency Analysis:** Calculates the absolute frequency of the most common terms using `collections.Counter`, exports the top results to `most_frequent_words.csv`, and plots the distribution using `matplotlib`.

## Technologies & Libraries Used
This project leverages the following Python libraries:
* **Data Manipulation:** `pandas`, `numpy`
* **Natural Language Processing (NLP):** `nltk` (VADER, stopwords, words corpus), `spacy`
* **Language Detection:** `langdetect`
* **Text Cleaning:** `re` (Regex)
* **Data Visualization:** `matplotlib.pyplot`, `wordcloud`, `seaborn`

## Setup & Installation

To run this notebook locally, ensure you have the required dependencies installed. You can install them via pip:

```bash
pip install pandas numpy nltk spacy langdetect wordcloud matplotlib seaborn



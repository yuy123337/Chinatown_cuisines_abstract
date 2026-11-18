# How U.S. Google reviews frame Chinese and Japanese cuisines

Replication materials for my school project.

## Data

The review data is in this Google Drive folder: https://drive.google.com/drive/folders/19buM2yZZgOPXQef2wxkNLTUgyuRpFR5n?usp=sharing

The notebooks read the data from `/home/ymusic7/metro_restaurants/`, the folder I used when I ran them. Change that path to wherever you save the data.

## What's in this repo

```
notebooks/   analysis notebooks (listed below)
scripts/     the review scraper and a clustering helper
figures/     figures saved from the notebooks
data/        shapefiles: New York City 2020 census tracts, Chicago neighborhoods (2012)
docs/        thesis proposal (PDF)
```

## Notebooks

| Notebook | What it does |
| --- | --- |
| `ny_chinatown.ipynb` | Loads the shapefiles and uses a spatial join to mark which restaurants are in Chinatown, then splits the reviews into Chinatown and non-Chinatown sets |
| `time_series.ipynb` | Monthly review counts (2019–2024) and Prophet time-series models |
| `time_series2.ipynb` | Month-by-month trends in how often reviews mention "Chinese" or "Japanese", with TextBlob sentiment |
| `cluster.ipynb` | TF-IDF, k-means clusters and LDA topics on a balanced sample of Chinese and Japanese restaurant reviews |
| `cluster_kmeans_topic_modeling.ipynb` | A second version of `cluster.ipynb` |
| `tfidf_similarity.ipynb` | TF-IDF and k-means clusters, sentiment by cluster, and each review's cosine similarity to its cluster center |
| `new_pca.ipynb` | Bag-of-words (n-gram) PCA of the reviews |
| `bow_pca.ipynb` | A second version of the PCA; makes `combined_pca_terms.png` |

## Scripts

- `scripts/scraping_script.py` collects Google Maps reviews for restaurants found with the keywords "chinese restaurant" and "japanese restaurant".
- `scripts/find_central_kcluster_review.py` lists the top TF-IDF words and the share of reviews in each k-means cluster.

## Setup

Python 3.7 or later. Install the packages with:

```bash
pip install pandas numpy matplotlib seaborn pyspark dask scikit-learn fbprophet geopandas shapely folium fiona pyproj rtree descartes sqlalchemy jupyterlab nltk textblob spacy wordcloud pyyaml pyarrow tqdm py4j
```

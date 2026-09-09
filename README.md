# Web Scraping and Data Analysis

## 📌 Project Overview

This project focuses on collecting publicly available product data from a website using Python web-scraping techniques, cleaning and organizing the collected information, and performing exploratory data analysis (EDA) to identify useful trends and patterns.

The project demonstrates the complete data analytics workflow:

**Web Scraping → Data Cleaning → Data Analysis → Visualization → Data Export**

---

## 🎯 Objective

The main objectives of this project are:

* Collect data from a publicly available website.
* Extract structured product information.
* Collect details such as product name, price, rating, availability, and category.
* Clean and organize the scraped data.
* Handle missing values and duplicate records.
* Perform exploratory data analysis.
* Identify trends and patterns in the data.
* Create visualizations to communicate findings.
* Export the final dataset to CSV and Excel formats.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **BeautifulSoup**
* **Requests**
* **Matplotlib**
* **Jupyter Notebook**
* **Excel**
* **GitHub**

---

## 📂 Project Structure

```text
Web-Scraping-Data-Analysis/
│
├── README.md
├── requirements.txt
│
├── data/
│   ├── raw/
│   │   └── scraped_data.csv
│   │
│   └── cleaned/
│       ├── cleaned_data.csv
│       └── cleaned_data.xlsx
│
├── notebooks/
│   └── web_scraping_analysis.ipynb
│
├── src/
│   └── scraper.py
│
└── outputs/
    ├── price_distribution.png
    ├── rating_distribution.png
    ├── price_vs_rating.png
    ├── category_analysis.png
    └── availability_analysis.png
```

---

## 🌐 Data Collection

The data was collected from a publicly available website using Python.

The following libraries were used for web scraping:

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
```

The scraping process involved:

1. Sending a request to the website.
2. Downloading the webpage content.
3. Parsing the HTML using BeautifulSoup.
4. Extracting relevant product information.
5. Storing the extracted information in a Pandas DataFrame.

---

## 📊 Data Extracted

The dataset contains structured product information such as:

| Column       | Description               |
| ------------ | ------------------------- |
| Product      | Name/title of the product |
| Price        | Product price             |
| Rating       | Customer/product rating   |
| Availability | Availability status       |
| Category     | Product category          |

> Column names may vary depending on the structure of the scraped website.

---

## 🧹 Data Cleaning

The collected data was cleaned using Pandas.

### Price Cleaning

Currency symbols were removed and prices were converted into numeric format.

```python
df_web["Price"] = (
    df_web["Price"]
    .astype(str)
    .str.replace("£", "", regex=False)
    .str.strip()
)

df_web["Price"] = pd.to_numeric(
    df_web["Price"],
    errors="coerce"
)
```

### Rating Cleaning

Text-based ratings were converted into numerical values.

```python
rating_map = {
    "One": 1,
    "Two": 2,
    "Three": 3,
    "Four": 4,
    "Five": 5
}

df_web["Rating"] = df_web["Rating"].replace(rating_map)

df_web["Rating"] = pd.to_numeric(
    df_web["Rating"],
    errors="coerce"
)
```

### Duplicate Removal

Duplicate records were removed:

```python
df_web = df_web.drop_duplicates()
```

### Missing Values

Missing values were checked and handled appropriately.

```python
print(df_web.isnull().sum())
```

---

## 🔎 Exploratory Data Analysis

Exploratory Data Analysis was performed to understand the dataset and identify important patterns.

The analysis included:

* Dataset shape
* Column information
* Statistical summary
* Average product price
* Minimum product price
* Maximum product price
* Average rating
* Product rating distribution
* Price distribution
* Category distribution
* Product availability
* Relationship between price and rating

Example:

```python
print(df_web.describe())

print("Average Price:", df_web["Price"].mean())
print("Minimum Price:", df_web["Price"].min())
print("Maximum Price:", df_web["Price"].max())
print("Average Rating:", df_web["Rating"].mean())
```

---

## 📈 Visualizations

The following visualizations were created:

### 1. Price Distribution

Shows how product prices are distributed across the dataset.

### 2. Rating Distribution

Shows the number of products for each rating.

### 3. Price vs Rating

Helps understand whether product price has any relationship with rating.

### 4. Category Analysis

Shows the number of products available in each category.

### 5. Availability Analysis

Shows the availability status of products.

---

## 💡 Key Insights

The analysis helps identify:

* The general price range of products.
* The average product rating.
* The most common rating among products.
* Categories containing the highest number of products.
* Availability patterns.
* Whether higher-priced products tend to have higher ratings.

---

## 📤 Exporting the Dataset

The cleaned dataset can be exported to CSV:

```python
df_web.to_csv(
    "cleaned_data.csv",
    index=False
)
```

It can also be exported to Excel:

```python
df_web.to_excel(
    "cleaned_data.xlsx",
    index=False
)
```

---

## ⚙️ Requirements

Install the required libraries using:

```bash
pip install requests beautifulsoup4 pandas numpy matplotlib openpyxl
```

Or use the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

---

## ▶️ How to Run the Project

### Step 1: Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### Step 2: Open the project

```bash
cd Web-Scraping-Data-Analysis
```

### Step 3: Install dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Open the Jupyter Notebook

```bash
jupyter notebook
```

### Step 5: Run the notebook

Open:

```text
notebooks/web_scraping_analysis.ipynb
```

and execute the cells sequentially.

---

## ⭐ Bonus: Automation

The scraping process can be automated using Python.

The scraper can be scheduled to run periodically and automatically:

* Collect updated data.
* Clean the data.
* Save the latest dataset.
* Export the results to CSV/Excel.

This makes the project reusable for future data collection.

---

## 📌 Conclusion

This project demonstrates the complete process of web scraping and data analysis using Python.

The project successfully covers:

**Data Collection → Data Extraction → Data Cleaning → Exploratory Analysis → Visualization → Data Export**

It provides practical experience in handling real-world data and converting raw web data into meaningful analytical insights.

---

## 👨‍💻 Author

**Santoshi Pandalwad**

Artificial Intelligence & Data Science

GitHub: `pandalwadsantoshi3-hub`

---

## 📜 Disclaimer

This project uses publicly available website data for educational and internship purposes. The scraping process should always respect the website's terms of service, robots.txt, and applicable laws.

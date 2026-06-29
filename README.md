# 🧹 Customer Data Cleaning Using Pandas

## 📌 Project Overview

This project demonstrates various data cleaning techniques using the Python Pandas library. Real-world datasets often contain duplicate records, missing values, inconsistent formatting, and unwanted characters. This notebook focuses on cleaning customer data to make it ready for analysis and machine learning tasks.

The project covers essential preprocessing steps such as removing duplicates, standardizing data formats, handling missing values, and transforming columns.

---

## 🎯 Objectives

- Identify and remove duplicate records.
- Standardize inconsistent data formats.
- Clean text columns by removing unwanted characters.
- Format phone numbers into a consistent structure.
- Split address information into separate columns.
- Handle missing and invalid values.
- Remove unnecessary columns from the dataset.

---

## 📂 Dataset Information

The dataset contains customer information such as:

- First Name
- Last Name
- Phone Number
- Address
- Paying Customer Status
- Do Not Contact Status
- Additional customer details

---

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- Pandas

---

## 🔄 Data Cleaning Steps Performed

### 1️⃣ Import Dataset

- Loaded customer data using Pandas.

```python
import pandas as pd
df = pd.read_excel("Datasets/ccl.xlsx")
```

---

### 2️⃣ Duplicate Record Detection

- Identified duplicate records.
- Removed duplicate entries from the dataset.

```python
df.duplicated().sum()
df.drop_duplicates(inplace=True)
```

---

### 3️⃣ Standardizing Text Data

- Removed unwanted characters from customer names.
- Cleaned and standardized the `Last_Name` column.

```python
df['Last_Name'] = df['Last_Name'].str.strip("123._/")
```

---

### 4️⃣ Phone Number Cleaning

- Converted phone numbers into string format.
- Removed special characters.
- Standardized phone numbers into a common format.

Example:

```text
1234567890 → 123-456-7890
```

```python
df['Phone_Number'] = df['Phone_Number'].apply(lambda x: str(x))
df['Phone_Number'] = df['Phone_Number'].str.replace('[^0-9]', '', regex=True)
```

---

### 5️⃣ Address Column Transformation

- Split the address column into separate fields.

New columns created:

- Street Address
- City
- Pin Code

```python
df[['Street_Address','City','Pin_Code']] = df['Address'].str.split(',', expand=True)
```

---

### 6️⃣ Standardizing Categorical Values

Converted values such as:

```text
Yes → Y
No  → N
```

Applied on:

- Paying Customer
- Do Not Contact

```python
df['Paying Customer'] = df['Paying Customer'].str.replace('Yes','Y')
df['Paying Customer'] = df['Paying Customer'].str.replace('No','N')
```

---

### 7️⃣ Removing Unnecessary Columns

Dropped irrelevant columns from the dataset.

```python
df.drop(columns=['Not_Useful_Column', 'Address'], inplace=True)
```

---

### 8️⃣ Handling Missing Values

Replaced invalid values and filled missing records.

Handled values such as:

- N/a
- NaN
- --

```python
df.replace('N/a', '', inplace=True)
df.replace('NaN', '', inplace=True)
df.replace('--', '', inplace=True)
df.fillna('', inplace=True)
```

---

## 📊 Key Data Cleaning Techniques Demonstrated

✅ Duplicate Removal  
✅ Text Standardization  
✅ String Manipulation  
✅ Lambda Functions  
✅ Regular Expressions (Regex)  
✅ Column Splitting  
✅ Missing Value Handling  
✅ Column Deletion  
✅ Data Formatting

---

## 📈 Learning Outcomes

After completing this project, you will be able to:

- Clean real-world datasets efficiently.
- Handle duplicate and missing data.
- Standardize inconsistent data formats.
- Perform text preprocessing using Pandas.
- Prepare datasets for data analysis and machine learning.

---

## 🚀 Future Improvements

- Implement advanced missing value imputation techniques.
- Automate data validation checks.
- Build reusable data cleaning pipelines.
- Integrate data quality reporting tools.

---

## 📁 Project Structure

```text
├── DataCLeaning(Cust_data).ipynb
├── ccl.xlsx
├── README.md
└── images/
```

---

## ▶️ How to Run

### Clone the Repository

```bash
git clone https://github.com/yourusername/customer-data-cleaning.git
```

### Install Required Library

```bash
pip install pandas openpyxl
```

### Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `DataCLeaning(Cust_data).ipynb` and run all cells.

---

## 📜 License

This project is intended for educational and learning purposes.

---

## 👨‍💻 Author

**zeba**  
Data Science Enthusiast | Python Developer | Machine Learning Learner

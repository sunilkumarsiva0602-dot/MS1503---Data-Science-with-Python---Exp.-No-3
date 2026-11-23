# Experiment 3 : Retail Sales and Profit Analysis Using Pandas

## Aim
To create a sample retail dataset, identify and handle missing values (`NaN`/`None`) and duplicate records, and compute summary statistics using Pandas in Python.

## Algorithm

1. **Start** the program.
2. **Import Library**: Import the `pandas` library as `pd` for tabular data cleaning and analysis.
3. **Initialize Raw Retail Dataset**: Create a Python dictionary `data` containing retail records (`Order_ID`, `Product`, `Region`, `Sales`, `Discount`, `Profit`) with deliberate missing (`None`) entries and duplicate rows.
4. **Construct DataFrame & Inspect**:
   * Convert `data` into a Pandas DataFrame `df` using `pd.DataFrame(data)`.
   * Print the original dataset and its initial dimensions (`df.shape`).
5. **Detect Missing Values**:
   * Count missing entries per column using `df.isnull().sum()`.
6. **Impute Missing Values**:
   * Replace missing numerical values in `Sales`, `Discount`, and `Profit` with their respective column means using `.fillna(df[col].mean())`.
   * Replace missing categorical values in `Region` with the column mode (most frequent category) using `.fillna(df["Region"].mode()[0])`.
7. **Remove Duplicate Records**:
   * Drop exact duplicate rows from `df` using `df.drop_duplicates()`.
8. **Display Cleaned Dataset & Summary Statistics**:
   * Print the cleaned DataFrame, updated dimensions (`df.shape`), and descriptive statistical metrics (`df.describe()`).
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation & Inspection** | `pd.DataFrame()` | Converts a Python dictionary into a labeled 2D tabular DataFrame |
| | `df.shape` | Returns the `(rows, columns)` dimensions before and after cleaning |
| | `df.isnull().sum()` | Counts the number of missing (`NaN`/`None`) values in each column |
| **Missing Value Imputation** | `df[col].fillna()` | Replaces missing values with a specified replacement value |
| | `df[col].mean()` | Calculates the arithmetic mean for numerical column imputation |
| | `df[col].mode()[0]` | Retrieves the most frequent category for categorical column imputation |
| **Deduplication & Summary** | `df.drop_duplicates()` | Identifies and removes duplicate rows from the DataFrame |
| | `df.describe()` | Generates count, mean, standard deviation, min, quartiles, and max for numerical features |

## Program

    # Cleaning and Preparing Retail Data using Pandas
    import pandas as pd
    
    # Step 1: Create a sample retail dataset
    data = {
        "Order_ID": [201, 202, 203, 204, 205, 206, 207, 208, 202],
        "Product": [
            "Laptop",
            "Office Chair",
            "Desk Lamp",
            "Monitor",
            "Mechanical Keyboard",
            "Standing Desk",
            "Webcam",
            "USB-C Hub",
            "Office Chair",
        ],
        "Region": [
            "South",
            "North",
            None,
            "West",
            "South",
            "East",
            "North",
            None,
            "North",
        ],
        "Sales": [
            55000.0,
            12000.0,
            2500.0,
            None,
            8500.0,
            24000.0,
            4200.0,
            None,
            12000.0,
        ],
        "Discount": [0.10, 0.15, None, 0.05, 0.20, None, 0.10, 0.05, 0.15],
        "Profit": [
            8200.0,
            1800.0,
            None,
            2400.0,
            1100.0,
            3600.0,
            None,
            650.0,
            1800.0,
        ],
    }
    
    df = pd.DataFrame(data)
    print("=== Original Retail Dataset ===")
    print(df)
    print("Initial Shape (rows, columns):", df.shape)
    print()
    
    # Step 2: Check for missing values
    print("=== Missing Values Per Column ===")
    print(df.isnull().sum())
    print()
    
    # Step 3: Fill missing numeric values with column mean
    for col in ["Sales", "Discount", "Profit"]:
        df[col] = df[col].fillna(df[col].mean())
    
    # Step 4: Fill missing Region with mode (most frequent value)
    df["Region"] = df["Region"].fillna(df["Region"].mode()[0])
    
    # Step 5: Remove duplicate records
    df = df.drop_duplicates()
    
    print("=== Cleaned Retail Dataset ===")
    print(df)
    print("Cleaned Shape (rows, columns):", df.shape)
    print("Remaining Missing Values:", df.isnull().sum().sum())
    print()
    
    # Step 6: Display summary statistics
    print("=== Summary Statistics ===")
    print(df.describe())
    


## Output
<img width="780" height="282" alt="image" src="https://github.com/user-attachments/assets/995b791b-d0cc-403f-833c-82080e8ba7d7" />
<img width="802" height="747" alt="image" src="https://github.com/user-attachments/assets/7459b3ae-8bd9-46c9-b048-1e9e0bcd0b14" />


## Result
The program successfully creates a retail dataset, identifies missing entries and duplicate rows, imputes missing values using mean and mode strategies, removes duplicates, and outputs a clean dataset ready for downstream analysis.

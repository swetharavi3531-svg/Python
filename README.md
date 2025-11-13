import numpy as np
import pandas as pd

# Read data from a CSV file into a dataframe
employee = pd.read_csv('./csvfiles/data_cleaning.csv')
print(employee)

# Remove duplicate entries based on 'Name' column
employee.drop_duplicates(subset="Name", keep='first', inplace=True)
print(employee)

# Check for missing values
missing = employee.isnull()
print(missing)

# Drop rows having missing values
employee = employee.dropna(axis=0)
print(employee)

# Delete unnecessary column
del employee['Sr.No']

# Fix manual spelling errors ("mobile" to "Mobile")
employee['Project'] = employee['Project'].str.replace('mobile', 'Mobile')

# Rename columns for clarity
employee.columns = ['EmployeeName', 'Address', 'Mobile', 'Domain', 'E-mailid']
print(employee)

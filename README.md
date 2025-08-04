# Task-1
Data cleaning  and Preprocessing 

import pandas as pd
df = pd.read_csv("indian_stock_data_raw.csv")
df_cleaned = df.dropna()
df_cleaned = df_cleaned.drop_duplicates()
df_cleaned['Stock'] = df_cleaned['Stock'].str.upper()
df_cleaned['Date'] = pd.to_datetime(df_cleaned['Date'], errors='coerce')
df_cleaned = df_cleaned.dropna(subset=['Date'])
df_cleaned.columns = df_cleaned.columns.str.lower().str.replace(' ', '_')
df_cleaned['volume'] = df_cleaned['volume'].astype(int)
for col in ['open', 'high', 'low', 'close']:
    df_cleaned[col] = df_cleaned[col].astype(float)
df_cleaned.to_csv("indian_stock_data_cleaned.csv", index=False)

i have used above codes in python(pandas) to complete my task 1 in data analyst internship

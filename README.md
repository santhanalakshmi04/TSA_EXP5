# DEVELOPED BY : SANTHANA LAKSHMI K
# REG NO. : 212222240091
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrate how to perform time series analysis and decomposition on the monthly average temperature from powerconsumption.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
DEVELOPED BY : SANTHANA LAKSHMI K
REG NO. : 212222240091
```
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the power consumption dataset
file_path = '/content/powerconsumption.csv'  
data = pd.read_csv(file_path)

# Convert 'Datetime' column to datetime format and set it as index
data['Datetime'] = pd.to_datetime(data['Datetime'], format='%m/%d/%Y %H:%M')
data.set_index('Datetime', inplace=True)
print("FIRST FIVE ROWS:")
print(data.head())

# Extract power consumption for Zone 1
power_data = data['PowerConsumption_Zone1']
plt.figure(figsize=(12, 6))
plt.plot(power_data, label='Power Consumption Zone 1')
plt.title('PLOTTING THE DATA')
plt.legend()
plt.show()

# Perform time series decomposition
period = 144  # Assuming a daily pattern with 144 ten-minute intervals in 24 hours
result = seasonal_decompose(power_data, model='multiplicative', period=period)

# Plot the decomposition components
plt.figure(figsize=(12, 8))

# Seasonal Plot Representation
print("\nSEASONAL PLOT REPRESENTATION:")
plt.figure(figsize=(12, 4))
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

# Trend Plot Representation
print("\nTREND PLOT REPRESENTATION:")
plt.figure(figsize=(12, 4))
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

# Original time series
plt.subplot(4, 1, 1)
plt.plot(power_data, label='Original')
plt.title('Original Time Series')
plt.legend()
```
### OUTPUT:
FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/45e802fb-3d65-4552-a21d-a4d691bf0c0d)

PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/f77add4c-62e5-4d84-adbf-18cb10b3b9a3)

SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/18fae911-5708-4eff-94a0-397a0d04ee73)

TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/99a29e23-d301-4f3e-85f1-38599b45a8ef)

OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/af69d44e-006d-421a-a336-456935f9f65a)

### RESULT:
Thus, The python code for the time series analysis and decomposition is executed successfully.

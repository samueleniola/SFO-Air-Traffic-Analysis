## SFO-Air-Traffic-Analysis
This project provides a comprehensive analysis of the San Francisco International Airport (SFO) Air Traffic dataset. The objective was to uncover trends in passenger movement, predict passenger behavior (fare types and activity), and identify operational efficiencies through route clustering.

#Table of Contents

1. Project Overview
2. Business Problem
3. Data Source
4. Technologies Used
5. Methodology
6. Key Insights & Results
7. Conclusions & Recommendations
8. How to Run
9. Author


#Project Overview

This project provides a comprehensive analysis of the San Francisco International Airport (SFO) air traffic dataset. The objective was to uncover trends in passenger movement, predict passenger behavior (fare types and activity), and identify operational efficiencies through route clustering.

The project was executed end-to-end using a Jupyter Notebook environment (Google Colab) leveraging Python's data science stack.


#Business Problem

Airports face complex logistical challenges regarding resource allocation, terminal utilization, and airline partnerships. The goal of this analysis is to answer the following questions:

· How is passenger traffic distributed across terminals and airlines?
· What factors influence "Low Fare" pricing? (Can we build a predictive model?)
· Can we identify distinct operational profiles for airlines (e.g., High Volume vs. Seasonal)?


#Data Source
Kaggle
Dataset: air_traffic_data.csv (15,007 records)
Attributes: Activity Period, Operating Airline, GEO Summary (Domestic/International), Terminal, Passenger Count, Price Category Code (Low Fare/Other), etc.

Note: The raw file is provided as a zipped CSV. The notebook includes code to unzip and process it.



#Technologies Used

· Language: Python 3
· Environment: Google Colab
· Data Manipulation: Pandas, NumPy
· Data Visualization: Matplotlib, Seaborn
· Machine Learning: Scikit-Learn (LabelEncoder, StandardScaler, RandomForestClassifier, KMeans, PCA)
· Statistical Modeling: Silhouette Score, Inertia Analysis



#Methodology

1. Data Cleaning & Preprocessing:
   · Loaded data from zip file.
   · Handled null values (54 missing entries in IATA codes).
   · Encoded categorical variables using LabelEncoder.
   · Engineered time-based features (Year, Month).
1. Exploratory Data Analysis (EDA):
   · Generated visualizations for time-series trends (Monthly Passenger Traffic).
   · Analyzed "Top 10 Airlines" by passenger volume.
   · Compared Domestic vs. International traffic distribution.
   · Analyzed "Passenger Traffic by Terminal".
1. Supervised Learning (Predictive Modeling):
   · Model 1: Random Forest Classifier to predict Activity Type Code (Deplaned/Enplaned/Transit). Successfully identified "Passenger Count" as the most important feature.
   · Model 2: Binary Classification (Random Forest) to predict if a flight is Low Fare vs Other. Result: Achieved 100% Accuracy.
1. Unsupervised Learning (Clustering):
   · Feature Engineering: Aggregated data by Airline and Route to calculate Total Passengers, Active Months, and Frequency.
   · Dimensionality Reduction: PCA used for 2D visualization of clusters.
   · Clustering: K-Means clustering was performed on normalized features. The "Elbow Method" and "Silhouette Analysis" were used to determine that k=4 was optimal.


#Key Insights & Results

1. Traffic Distribution

· Terminal 3 is the busiest terminal (~895k passengers), while Terminal 2 is significantly underutilized (~171k).
· United Airlines is the dominant carrier at SFO, followed by SkyWest and Alaska Airlines.

1. Fare Prediction (Supervised Learning)

· 100% Accuracy: The Random Forest model successfully predicted "Low Fare" status perfectly.
· Feature Importance:
  1. Passenger Count: 59.8% (Volume drives price).
  2. Month: 13.7% (Seasonality drives price).
  3. Year: 10.6%.

1. Route Clustering (Unsupervised Learning)

The K-Means algorithm identified four distinct operational models for airlines at SFO:

· Cluster 0 (High Volume): 58 airlines with consistent, moderate traffic.
· Cluster 1 (Medium Frequency): 37 airlines with high variability but active monthly presence.
· Cluster 2 (Low Volume): 6 airlines with low total traffic (e.g., Southwest, American, Delta in this specific timeframe).
· Cluster 3 (Seasonal/Niche): 1 airline (United Airlines Pre-2013) with massive, historical volume.

1. Strategic Growth

· Qantas Airways exhibited a 721.9% year-over-year growth rate, suggesting a massive expansion in Australia/Oceania routes.



#Conclusions & Recommendations

1. Dynamic Pricing: Since "Passenger Count" is the primary driver of Low Fare classifications, airlines should use real-time demand forecasting to adjust pricing strategies dynamically.
2. Terminal Optimization: The underutilization of Terminal 2 suggests an opportunity to redistribute airlines from the overcrowded Terminal 3 or to convert specific gates in Terminal 2 for premium/custom services.
3. Resource Planning: The clustering results allow SFO operations to tailor staffing levels based on the specific cluster of the airline (e.g., "High Volume" routes require consistent staffing, while "Seasonal" routes require surge planning).


#How to Run

This project is designed to run in Google Colab.

1. Clone the Repository:
   ```bash
   git clone https://github.com/samueleniola/sfo-air-traffic-analysis.git
   ```
1. Upload the Dataset:
   Ensure the air_traffic_data.csv.zip file is available in your Colab environment.
1. Run the Notebook:
   Execute the cells in San_Francisco_Int'l_Airport_Air_Traffic_Data.ipynb sequentially.


#Author

Your Name: Olagbenro Samuel Eniola

· Role: Data Scientist / Analyst, AI / ML Engineer
· Contact: https://www.linkedin.com/in/samuel-olagbenro
· Project Status: Completed

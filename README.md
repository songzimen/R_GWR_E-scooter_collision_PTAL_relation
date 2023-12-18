# R_GWR_E-scooter_collision_PTAL_relation

## Initial project scope
# Aim and objectives:
To explore if the transport accessibility influenced E-scooter collisions in London.

# Research Question:
Does accessibility to urban infrastructure and public services have an impact on the occurrence of E-scooter accidents?

# Data
1. Resources:
  In this exam, we will use London 2011 wards shapefile data, Transport for London's (TFL) Public Transport Accessibility Levels (PTALs) data of London, and the E-scooter collision points data.

  London 2011 wards shapefile data can be found:
https://data.london.gov.uk/download/statistical-gis-boundary-files-london/9ba8c833-6370-4b11-abdc-314aa020d5e0/statistical-gis-boundaries-london.zip

  Transport Accessibility Levels (PTALs) data can be found:
https://data.london.gov.uk/download/public-transport-accessibility-levels/8d489aed-8341-499e-9d73-d69b3c2fac49/Ward2011%20AvPTAI2015.csv

  The E-scooter collision points data (2020-2022) can be found here:
https://www.data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data/datafile/84435d09-105b-4429-8e96-1174dfa32c8a/preview

  The collision points last 5 years data (with location) can be found here (This one is too big to upload to github, please download it and put under data):
https://www.data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data/datafile/77c26682-93e7-4e77-aa4f-5681510ca57c/preview

2. The Dataset
In the London 2011 wards shapefile data, we can get the multipolygon boundary of each ward in London with CRS of 27700. 
In the Transport Accessibility Levels (PTALs) data of London, we can get the data of  PTAL score in 2015 of all London wards.
In the E-scooter collision points data, we can get all the location of E-scooter collisions from 2018 to 2022. Particularly, we extract graffitis happens during 2020-2022, which the exam required.

3. Preprocessing and Wrangling data:
  We will use The E-scooter collision points data (2020-2022) and The collision points last 5 years data (with location), make a join so we get the E-scooter collision points during 2020-2022. 
  Next, we will do a spatial join, and cont the points in each ward, finally get a new shp include point counts of wards.
  Finally, we will join the PTAL score data to the merged shp data, get a integrated dataset include PTAL score and E-scooter collision count of each ward.

# Analysis
1. Hypothesis: 
The public transport accessibility will decrease the occurrences of E-scooter collision.

2. Null Hypothesis:
The public transport accessibility have no relation with or increase the occurrences of E-scooter collision.

3. Methods:
KED: Observe the distribution pattern of E-scooter collision locations, visually check  if they had a tendency to congregate.
Moran's I: quantitatively explore if the E-scooter collision points count and PTAL score have cluster or dispersed pattern.
Local indicators of spatial association (LISA): explore the pattern of E-scooter collision points count and PTAL score distribution and find where they clustered or dispersed in map.
GRW: Built a model that how the public transport accessibility (PTAL score) influence the occurrences of E-scooter collision, so the graffiti occurrences can be predictd.

# Potential Limitations
  Perhaps the above methods are suitable for this dataset in some ways, but there are still some drawbacks:
  1. Data: The accuracy of the E-scooter collision data and the PTAL scores is crucial. Any errors or omissions in these datasets could lead to inaccurate conclusions. The PTAL data is from 2015, which might not accurately reflect current transportation accessibility levels. The choice of spatial scale (wards) might influence the results. Different results could be obtained if a finer or broader spatial scale was used.
  
  2. Outliers: Any isolated bright spots located in the peripheries or away from the central clusters could be outliers or areas with specific issues leading to a higher-than-expected number of accidents.

  3. Constrained by computational capacity and the scope of the research, this study has only selected one factors that may influence the occurrence of E-scooter collisions. Incorporating additional influencing factors into the GWR model could enhance the accuracy of the model's predictions.

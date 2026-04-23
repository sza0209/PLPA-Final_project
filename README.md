# Land cover classification and model transferability in Alabama Wildlife Management Areas

Author

Sinka Khadijah Abubakar

## Project overview

This project develops a fully reproducible geospatial workflow to apply a previously trained Random Forest land cover classification model to Landsat 8/9 imagery (2024) across multiple Wildlife Management Areas (WMAs) in Alabama.

The main objective is to evaluate the **spatial transferability and robustness of a supervised land cover classification model** when applied to new geographic locations and independent satellite imagery.

The workflow integrates:
- Multispectral remote sensing data (Landsat 8/9)
- Reference land cover datasets (NLCD and Tree Canopy Cover)
- Field-collected validation data
- Machine learning classification (Random Forest)

All analysis is fully scripted in R and designed to be reproducible from raw data to final figures.

---

## Research question

This project addresses the following question:

> How well does a Random Forest land cover classification model trained on one spatial context generalize when applied to new Landsat 8/9 imagery from a different time point, and how does classification accuracy compare to reference datasets and field validation data?

---

## Analytical workflow summary

The project follows a structured geospatial machine learning pipeline:

### 1. Data acquisition and organization
- Download or access Landsat 8/9 imagery
- Load NLCD and Tree Canopy Cover datasets
- Import Wildlife Management Area (WMA) boundaries
- Import field validation points

### 2. Spatial preprocessing
- Harmonization of coordinate reference systems (CRS)
- Raster cropping and masking to study area
- Resampling and alignment of predictor layers
- Construction of a multi-layer raster stack

### 3. Model application
- Build and load trained Random Forest model
- Apply model to stacked predictor raster
- Generate spatial land cover classification map

### 4. Accuracy assessment
- Extract predicted values at validation locations
- Compare predicted vs observed land cover classes
- Compute confusion matrix and accuracy metrics

### 5. Visualization
- Generate publication-ready land cover maps
- Create accuracy and validation matrix tables

---

## Link to analysis
- [Land cover model building script](Scripts/landcoverModelScript.Rmd)
- [Prediction script](Scripts/PredictionScript.Rmd)

---

## File tree

```
├── model
│   └── rf_model.RData
├── PLPA-Final_project.Rproj
├── Proposal.docx
├── README.md
└── Scripts
    ├── landcoverModelScript.Rmd
    └── PredictionScript.Rmd
```

---

## Data sources, access and description

Due to the large size of geospatial raster datasets (Landsat imagery, NLCD, and Tree Canopy Cover layers), these files exceed GitHub’s file size limits for standard repositories. To ensure accessibility while maintaining reproducibility, all large geospatial datasets are hosted in a separate, shared laboratory GitHub repository with expanded storage capacity. The link to that repository is provided below:

Data repository: 

### Landsat 8/9 surface reflectance (2024)
- Source: USGS Earth Explorer  
- https://earthexplorer.usgs.gov/  
- Multispectral satellite imagery used to derive spectral predictors for classification

---

### National Land Cover Database (NLCD 2023)
- Source: Multi-Resolution Land Characteristics Consortium (MRLC)  
- https://www.mrlc.gov/  
- Used as a reference land cover dataset for comparison and validation

---

### Tree Canopy Cover (TCC 2023)
- Source: MRLC Consortium  
- https://www.mrlc.gov/  
- Provides continuous canopy cover estimates used as a predictor layer

---

### Wildlife Management Area boundaries
- Source: Alabama GIS datasets / custom shapefile  
- Defines spatial extent of analysis

---

### Field validation data
- GPS-collected ground reference points  
- Converted from CSV to shapefile format  
- Used for independent accuracy assessment of classification output

---

## Software environment

This project was developed using:

- R version ≥ 4.5.1
- RStudio IDE

### Main required packages

- terra (raster processing and spatial analysis)
- sf (vector spatial data handling)
- randomForest (machine learning model)
- caret (accuracy assessment and confusion matrix)
- dplyr (data manipulation)
- ggplot2 (visualization)

---


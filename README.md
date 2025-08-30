# Data-Engineering-Project-Portfolio
An end-to-end data engineering pipeline on Azure processing real-time Polish air quality data from a public API. The project uses Azure Data Factory for ingestion, Synapse PySpark for transforming raw JSON into clean Delta Lake tables, and Power BI for an interactive dashboard. Demonstrates automation and BI skills.




# End-to-End Data Engineering Pipeline: Polish Air Quality Analysis

*Data as of: August 29, 2025*

## Project Goal

This project demonstrates a complete, end-to-end data engineering pipeline built on the Microsoft Azure platform. The goal was to automatically ingest, process, and visualize real-time air quality data from a public API, transforming raw JSON data into an interactive analytical dashboard.

## Final Dashboard

Here is a demonstration of the final interactive Power BI report. The dashboard allows users to filter data by city and air quality index, providing an immediate overview of the current situation in Poland.

![Interactive Dashboard Demo](showcase/PBI_report.gif)

---

## Architecture

The project follows a modern data platform architecture, ensuring scalability and automation.



### Technology Stack
* **Orchestration:** Azure Data Factory
* **Storage:** Azure Data Lake Storage Gen2
* **Processing:** Azure Synapse Analytics (using a PySpark notebook)
* **Data Format:** Delta Lake
* **Visualization:** Power BI

---

## Project Workflow

### 1. Data Ingestion
Two pipelines in **Azure Data Factory** orchestrate the data flow:
* A pipeline fetches the master list of all monitoring stations.
* A `ForEach` loop in a second pipeline then dynamically calls the API for each station to retrieve the latest air quality index.
* The raw, nested JSON files are stored in a `raw` layer in Azure Data Lake.

*Code: [ADF Pipeline JSONs](/adf-pipelines/)*

### 2. Data Transformation
A **PySpark notebook** in Azure Synapse Analytics reads the raw data and performs all transformations:
* Parsing and flattening the nested JSON structure.
* Cleaning data and selecting necessary columns.
* Enriching measurement data by joining it with station dimension data.
* The final, clean, and structured table is saved back to the Data Lake in a `processed` layer using the efficient **Delta Lake** format.

*Code: [PySpark Notebook](/synapse-notebook/)*

### 3. Data Visualization
A **Power BI** report connects to the processed data via the Synapse Serverless SQL endpoint. Key features of the dashboard include:
* KPI cards for a high-level overview.
* A geographically precise map with conditional formatting.
* Ranking charts and interactive slicers.

*Showcase: [Dashboard Screenshots](/showcase/)*

---

This project showcases practical skills in cloud data services, automation, big data processing, and business intelligence.

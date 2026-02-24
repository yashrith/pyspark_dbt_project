# Databricks & dbt Cloud: End-to-End Data Transformation Pipeline

## 📌 Project Overview
This project demonstrates a professional **Analytics Engineering** workflow using a modern data stack. I built a scalable transformation pipeline that converts raw data into business-ready insights.

The project leverages **dbt Cloud** for modeling and orchestration, with **Databricks** providing the high-performance compute and storage via the **Delta Lakehouse** architecture.

---

## 🛠 Tech Stack
* **Data Warehouse:** [Databricks](https://www.databricks.com/) (SQL Warehouses & Compute)
* **Transformation Layer:** [dbt Cloud](https://www.getdbt.com/)
* **Storage Layer:** Delta Lake (ACID compliant tables)
* **Version Control:** GitHub
* **Language:** Jinja-templated SQL

---

## 🏗 Data Architecture & Medallion Strategy
The transformation logic follows the **Medallion Architecture**, ensuring data quality at every stage. 

> **Important Note on Data Storage:** > While the transformation logic (SQL) is version-controlled here in GitHub, the **physical data resides in the Databricks Cloud environment**. The final output datasets are persisted as **Delta tables** within Databricks, which can be exported as **CSV files** for downstream reporting or external stakeholder use.

### 1. Bronze (Raw / Staging)
* Initial ingestion of raw source data.
* Renaming columns for consistency and casting data types.


### 2. Silver (Intermediate)
* Applying business logic, filtering, and joining disparate sources.
* Handling null values and deduplication.


### 3. Gold (Marts)
* Ready for the analysis in gold layer


---

## 🚀 Key Features Implemented
* **Modular Modeling:** Used `ref()` and `source()` functions to build a robust Directed Acyclic Graph (DAG).
* **Data Integrity Testing:** Implemented automated `unique`, `not_null`, and `relationship` tests to ensure high data quality.
* **Documentation:** Automated the generation of a data dictionary using dbt's documentation site.
* **Performance Optimization:** Leveraged Databricks' Photon engine for efficient processing of large datasets.

---

## 📂 Repository Structure
```text
├── models/
│   ├── staging/      # Cleaning & Renaming (Bronze)
│   ├── intermediate/ # Joins & Business Logic (Silver)
│   └── marts/        # Final BI-ready tables (Gold)
├── seeds/            # Static CSV data loaded into Databricks
├── tests/            # Custom data quality assertions
├── dbt_project.yml   # Project configuration & Materialization settings
└── packages.yml      # External dependencies (e.g., dbt_utils)

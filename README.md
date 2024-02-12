##Dynamic ETL Workflow with Azure DataBricks, Delta Lake and ADF
---

### Project Overview

The project focuses on building a real-world data engineering solution using Azure Databricks, PySpark, Azure Data Lake Gen2, Delta Lake, and Azure Data Factory. It involves analyzing and reporting on Formula1 motor racing data.

![Project_Architecture](https://github.com/sameerhussai230/Dynamic_ETL_Workflow_with_Azure_DataBricks_Delta_Lake_and_ADF/assets/85198601/dccb148d-5846-4791-8863-be1ce68bcffa)

---

### Data Source

The data for all Formula 1 races from the 1950s onwards is obtained from an open-source API called Ergast Developer API (https://ergast.com/mrd/). The API provides several tables, and the attributes of each table are described in detail in the F1DB User Guide(https://ergast.com/docs/f1db_user_guide.txt). Each table is present as a single-line/multiline CSV or JSON file in the data folder.
 
The data covers various aspects such as race results, circuits, drivers, constructors, pit stops, lap times, etc. Data sources files are: Circuits (CSV) , Races (CSV) , Constructors (JSON) , Drivers (JSON), Results (JSON), Pitstops (JSON), Lap Times (Split CSV Files), Qualifying (Split JSON Files)
![Data_Source](https://github.com/sameerhussai230/Dynamic_ETL_Workflow_with_Azure_DataBricks_Delta_Lake_and_ADF/assets/85198601/f3aebe6f-ccb4-454c-9d80-0b085bf40312)

---

### Architecture Explanation & Project Working

The project utilizes Azure Databricks, Delta Lake, Azure Data Factory. It involves:

- Connecting Databricks using Service Principal and Keyvault Secrets
- Implementing Incremental Load using Delta Lake upsert concept
- Designing Ingest, Transform, and Process Pipelines

![Resources](https://github.com/sameerhussai230/Dynamic_ETL_Workflow_with_Azure_DataBricks_Delta_Lake_and_ADF/assets/85198601/9493e342-77ab-4052-a813-d7a3dcdea899)

---

###  Data Processing Pipeline Overview

The data obtained from the Ergest Developer API is imported into a raw Azure Data Lake Storage (ADLS) container on Azure. Subsequently, this raw data is processed using Databricks notebooks to ingest it into the ingested raw layer.

Ingested Raw Layer
In this layer, schema is applied to the data and it is stored in the columnar Parquet format. Where applicable, partitions are created, and additional information, such as date and data source, is added for audit purposes.

Transformation for Presentation Layer
The ingested data is then transformed via Databricks notebooks for the presentation layer. In this layer, dashboards are created to meet the requirements for analysis.

Azure Data Factory Integration
Azure Data Factory is utilized for scheduling and monitoring requirements, orchestrating the entire data processing pipeline.

Delta Lakehouse Architecture
To address additional requirements such as GDPR compliance, time travel, and data versioning, the pipeline is later converted into a Delta Lakehouse architecture.

This robust pipeline ensures efficient data processing, from ingestion to presentation, while meeting various compliance and analytical needs.


### Incremental Load using Delta Lake

 Implementing Scalable Code for Incremental Load & Full Load Files using Delta Lake's upsert concept in Azure Databricks.

![Scalable Code for Incremental Load   Full Load Files](https://github.com/sameerhussai230/Dynamic_ETL_Workflow_with_Azure_DataBricks_Delta_Lake_and_ADF/assets/85198601/c7d57e7d-a33d-42b6-aba0-3f04f8b8a03a)

---

### Ingest Pipeline

For Ingesting Data from Raw container to processed container

![Ingestion_Pipeline](https://github.com/sameerhussai230/Dynamic_ETL_Workflow_with_Azure_DataBricks_Delta_Lake_and_ADF/assets/85198601/b842f382-66fc-4286-b81f-a78fedf7ef18)


---

### Transform Pipeline

 Transforming raw Formula1 data into a structured format suitable for analysis using PySpark in Azure Databricks and automating it using ADF.

![Transform_Pipeline](https://github.com/sameerhussai230/Dynamic_ETL_Workflow_with_Azure_DataBricks_Delta_Lake_and_ADF/assets/85198601/f64f203b-8d53-4783-8cc6-192243cc22f6)

---

### Process Pipeline

 Process pipeline responsible for running both Ingest Pipeline and Transform Pipeline with dependency.

![Process_Pipeline](https://github.com/sameerhussai230/Dynamic_ETL_Workflow_with_Azure_DataBricks_Delta_Lake_and_ADF/assets/85198601/dd0231a6-b2af-48c7-a607-0352ec947eac)

---


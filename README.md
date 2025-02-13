

## **🚖 NYC Taxi Data Pipeline – Medallion Architecture with Azure & Databricks 🚀**  

### **📌 Project Overview**  
This project implements a **dynamic data pipeline** using **Azure Data Factory, Databricks, and Delta Lake**, following the **Medallion Architecture (Bronze, Silver, Gold)**. The goal is to **ingest, transform, and analyze NYC Taxi data**, making it ready for analytics and visualization in **Power BI**.

---

## **📁 Architecture Overview**  
### **🔹 Medallion Architecture**
The project follows a structured **three-layer approach**:
1. **Bronze Layer (Raw Data)**
   - Ingests data from the **NYC Taxi API**.
   - Stores raw files in **Parquet format** in **Azure Data Lake Storage (ADLS Gen2)**.
  
2. **Silver Layer (Cleaned Data)**
   - Performs **data transformations** using **Databricks**.
   - Renames columns, extracts timestamps, and filters necessary fields.
  
3. **Gold Layer (Processed Data)**
   - Stores refined data in **Delta format** for optimized querying.
   - Enables **Delta Lake versioning and time travel** for auditing.

---

## **🛠️ Tech Stack & Services Used**  
- **Azure Data Factory (ADF)** – Data ingestion & pipeline automation  
- **Azure Data Lake Storage Gen2 (ADLS Gen2)** – Cloud storage for raw and processed data  
- **Azure Databricks (Apache Spark & Delta Lake)** – Data transformation & analytics  
- **Delta Lake** – Optimized storage with time travel & versioning  
- **Power BI** – Data visualization & reporting  

---

## **📌 Data Pipeline Implementation**
### **1️⃣ Data Ingestion (ADF)**
- Pulled **NYC Taxi Trip Data** from the **NYC Open Data API**.  
- Configured **ADF Linked Services**:
  - **Source:** HTTP API connection.  
  - **Sink:** ADLS Gen2 for storage.  
- Created **datasets** for API and ADLS storage.  
- **Pipeline Activities:**
  - **Copy Activity** → Moves data to the Bronze Layer.  
  - **ForEach Activity** → Iterates over monthly datasets dynamically.  
  - **If Condition Activity** → Manages data processing conditions.

### **2️⃣ Data Transformation (Databricks)**
- Read **Bronze layer** data using **Apache Spark**.
- Cleaned & transformed data:
  - Renamed columns for better readability.
  - Extracted date components (year, month, day).
  - Selected relevant fields for analysis.
- Saved transformed data into the **Silver Layer**.
- Created **Delta Tables** for optimized storage in the **Gold Layer**.

### **3️⃣ Data Analysis & Visualization (Power BI)**
- Connected Power BI to the **Gold Layer** via **Databricks Partner Connect**.  
- Used **Access Token** for a secure connection.  
- Built **interactive dashboards** to analyze **taxi trends, demand, and pricing**.

---

## **🚀 Features & Enhancements**
✔ **Automated Data Pipeline** using Azure Data Factory  
✔ **Scalable Storage** with Data Lake & Delta Lake  
✔ **Real-Time Data Processing** with Apache Spark  
✔ **Delta Lake Versioning & Time Travel** for data integrity  
✔ **Power BI Dashboards** for visualization & insights  

---



## **⚡ Setup & Deployment**
### **🔹 Prerequisites**
- An **Azure Subscription**
- An **Azure Databricks workspace**
- **Azure Data Factory** configured
- **Power BI** for visualization

### **🔹 Steps to Run**
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/NYC-Taxi-Data-Pipeline.git
   cd NYC-Taxi-Data-Pipeline
   ```

2. Set up **Azure Resources**:
   - Create **Azure Data Factory**, **Data Lake**, and **Databricks workspace**.
   - Ensure **ADLS Gen2 hierarchical namespace (HNS) is enabled**.

3. Deploy **ADF Pipeline**:
   - Import JSON configurations from `/pipeline_configs/`.
   - Set up **HTTP and ADLS Linked Services**.
   - Trigger the **Copy Activity**.

4. Run **Databricks Notebooks**:
   - Execute **Bronze → Silver → Gold processing notebooks**.

5. Connect **Power BI**:
   - Use **Databricks Partner Connect** to access Delta tables.

---



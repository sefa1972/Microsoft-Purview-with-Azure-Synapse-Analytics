# Microsoft-Purview-with-Azure-Synapse-Analytics

## Overview
This lab demonstrates how to integrate Microsoft Purview with Azure Synapse Analytics to catalog data assets and track data lineage across your data estate. You'll learn how to:

1. Provision Azure resources including Synapse Analytics and Microsoft Purview
2. Configure access permissions for Microsoft Purview
3. Register and scan data sources in Microsoft Purview
4. Explore cataloged assets and data lineage
5. Integrate Microsoft Purview with Synapse Analytics pipelines

## Prerequisites
- Azure subscription with administrative privileges
- Exclusive access to the Azure tenant (shared lab environments may not work)

## Lab Setup
The lab uses a PowerShell script to provision the following resources:
- Azure Synapse Analytics workspace
- Dedicated SQL pool
- Data Lake Storage Gen2 account
- Microsoft Purview account

## Key Steps

### 1. Resource Provisioning
- Run the setup.ps1 script to create all required resources
- Note the unique suffix generated for your resource names
- Resume the paused dedicated SQL pool in Synapse Studio

### 2. Create Lake Database
- Create a new lake database in Synapse Studio
- Add an external table from CSV data in the data lake
- Query the data using serverless SQL pool

### 3. Configure Microsoft Purview
- Create a Microsoft Purview account
- Assign required roles to the Purview managed identity:
  - Storage Blob Data Reader on the data lake
  - Reader on the Synapse workspace
  - db_datareader on both SQL databases

### 4. Register and Scan Data Sources
- Register two data sources in Microsoft Purview:
  - Synapse workspace (Synapse_data)
  - Data lake storage (Data_lake)
- Run scans on both sources to catalog assets

### 5. Explore Cataloged Assets
- Browse the Purview catalog to view:
  - Files in the data lake
  - Tables in SQL databases
  - Views in serverless SQL pool
- Examine asset properties and schema

### 6. Synapse-Purview Integration
- Connect Purview account in Synapse Studio
- Search Purview catalog directly from Synapse
- Create and run a pipeline to load data
- View pipeline lineage in Purview

## Cleanup
Remember to:
1. Pause the dedicated SQL pool when not in use
2. Delete the resource group when finished to avoid ongoing charges

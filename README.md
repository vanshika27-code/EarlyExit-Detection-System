# 🏢 Employee Attrition Risk & Wellbeing Monitor

An automated HR solution that captures employee feedback, calculates attrition risk using a custom scoring algorithm, and visualizes organizational health via a real-time Power BI dashboard.

---

## 📖 Table of Contents
* [Project Overview](#-project-overview)
* [System Architecture](#-system-architecture)
* [n8n Workflow Logic](#-n8n-workflow-logic)
* [Power BI Dashboard Features](#-power-bi-dashboard-features)
* [Setup Instructions](#-setup-instructions)

---

## 🌟 Project Overview
This project addresses the "Human" in Human Resources by automating the feedback loop. Instead of waiting for annual reviews, this system identifies burnout and dissatisfaction trends as they happen, allowing HR teams to intervene before an employee decides to leave.

### Key Metrics Tracked:
* **Job Satisfaction (1-5)**
* **Work-Life Balance (Hours per day)**
* **Career Growth Opportunities**
* **Managerial Support**

---

## 🏗 System Architecture
The project uses a three-tier architecture:
1. **Data Collection:** Google Sheets acts as the intake form for employee surveys.
2. **Processing Engine:** **n8n** handles the logic, scoring, and routing.
3. **Visualization:** **Power BI** consumes the processed data to generate executive insights.

---

## ⚙️ n8n Workflow Logic

The workflow (`My workflow 7`) is designed for high efficiency and zero manual intervention:

| Node | Function |
| :--- | :--- |
| **Google Sheets Trigger** | Watches for new survey entries in real-time. |
| **Calculate Risk Score** | Applies a weighted formula to calculate a `riskScore` (0-100). |
| **Route by Risk Level** | A conditional branch separating "High" risk from "Low" risk. |
| **Format Alert Message** | Generates a notification payload for the HR team for high-risk cases. |
| **Prepare Data for Storage** | Cleanses the data (handling `null` values) for the final dashboard. |
<img width="1400" height="894" alt="image" src="https://github.com/user-attachments/assets/439aa033-ac07-4ff3-99d9-1e693b95f7c8" />

---

## 📊 Power BI Dashboard Features

The dashboard provides a visual breakdown of the data processed by n8n:

* **Executive Summary:** Displays Total Responses, Average Job Satisfaction, and the total count of High-Risk employees.
* **Risk Level Distribution:** A pie chart showing the percentage of the workforce currently at risk.
* **Career Growth vs. Risk:** A trend line analyzing how perceived growth impacts the average risk score.
* **Granular Logs:** A detailed table listing individual employee emails, their work hours, and specific dissatisfaction triggers.<img width="1383" height="746" alt="image" src="https://github.com/user-attachments/assets/a691d78c-4b3d-415c-a03d-242b6fc6a02e" />


---

## 🛠 Setup Instructions

### 1. n8n Configuration
* Import the provided JSON workflow.
* Connect your **Google Sheets** credentials.
* Set the **Calculate Risk Score** node to match your specific HR weighting criteria.

### 2. Power BI Connection
* Connect Power BI to the Google Sheet (or SQL database) where the `Prepare Data for Storage` node sends information.
* Ensure the following columns are mapped: `email`, `riskScore`, `riskLevel`, `jobSatisfaction`, and `workHours`.

### 3. Execution
* Click **Execute Workflow** in n8n.
* Refresh the Power BI dashboard to see the live data visualization.

---

> **Note:** This project is part of a strategic HR initiative to blend data-driven automation with humane organizational management.

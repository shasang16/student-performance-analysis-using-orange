# student-performance-analysis-using-orange
This Orange Data Mining workflow analyzes student data to identify patterns related to dropout. It includes data preprocessing, feature selection, k-Nearest Neighbors (kNN) for prediction, distance-based student similarity analysis, and k-Means clustering to group students with similar characteristics.


Here is a structured, clean, and easy-to-read version of your guide on how to access and run the Orange Workflow (`.ows`) file.

---

## Understanding the OWS File

A `.ows` file is an **Orange Workflow file**, not a standard executable (`.exe`) program. It must be opened and run using **Orange Data Mining (Orange3)**.

---

## Step-by-Step Guide

### Step 1: Install and Open Orange

1. Download and install **Orange Data Mining** on your computer.
2. Launch the **Orange Canvas** application.

### Step 2: Open the OWS File

Open the workflow in Orange Canvas using either method:

* Go to **File** → **Open** → Select `DATA(1).ows`.
* Double-click the `.ows` file directly (if Windows has associated `.ows` files with Orange).

Once opened, you will see the complete workflow containing widgets such as:

> `CSV File Import` → `Edit Domain` → `Select Columns` → `Data Table` → `Neighbors` / `kNN` / `Predictions` / `k-Means`

### Step 3: Load the Dataset

The workflow was originally saved referencing a specific file (`updated_student_dataset.csv`). Because file paths vary across computers, Orange may prompt you to locate the dataset manually.

1. When prompted, select your updated dataset file: **`updated_student_dataset(2).csv`**.
2. Once connected, Orange will load all **5,001 student records** into the workflow.

### Step 4: Verify the Data

Open the **Data Table** widget to confirm that the student records have loaded correctly. You should see the following attributes:

* **Demographics & Background:** ID, Family Income, Parent Education, Location Type, Peer Pressure Level, Mental Health Issues
* **Academic Performance:** JEE Main Score, JEE Advanced Score, Mock Test Score Average, School Board, Class 12 Percentage, Attempt Count, Coaching Institute, Daily Study Hours
* **Target:** Dropout

### Step 5: Run the Analysis

Orange automatically executes connected widgets once their inputs are ready. You can double-click any widget to inspect its output.

The core analysis pipelines in your workflow include:

* **Similarity Pipeline:** Data Import → Data Preparation → Feature Selection → Distance Calculation → Similar Student Analysis
* **Classification Pipeline:** Data Import → Data Preparation → kNN → Predictions
* **Clustering Pipeline:** Data Import → Data Preparation → k-Means → Clustered Data

---
WARNING

**1. k-Means – “Silhouette scores are not computed for >5000 samples”**
The warning appears because the dataset contains **5,001 samples**, while Orange does not calculate silhouette scores for datasets with more than 5,000 samples. This only prevents the silhouette score from being displayed; the k-Means clustering itself still works normally and the clustering output is not affected.

**2. Predictions – “Instances with missing targets are ignored while scoring”**
This warning occurs because some instances in the dataset have **missing target (dropout) values**. These instances are ignored only while calculating the performance scores. The kNN model still generates predictions for the available data, so the prediction output is not affected.

**3. Neighbors – “Every data instance is same as some reference”**
This warning indicates that every data instance is also present in the reference dataset. Therefore, a data point can be identified as its own nearest neighbor. This is due to the way the reference data is provided and does not prevent the Neighbors widget from finding the specified nearest neighbors.


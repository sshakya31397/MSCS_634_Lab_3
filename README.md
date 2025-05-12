# Clustering Analysis Using K-Means and K-Medoids on Wine Dataset

## Purpose

The purpose of this lab was to explore and compare two clustering algorithms—K-Means and K-Medoids—using the Wine dataset from the `sklearn` Python library. The lab aimed to evaluate how well each method grouped wine samples into clusters based on their chemical attributes,
and how closely these clusters matched the known class labels (wine types). Key evaluation metrics such as the Silhouette Score and Adjusted Rand Index (ARI) were used to quantify clustering performance and help determine which algorithm was more effective for this dataset.

---

## Key Insights

- **K-Means Clustering:**
  - Produced well-defined and compact clusters.
  - Achieved a **Silhouette Score of 0.2849**, indicating moderately good separation between clusters.
  - Reached a high **Adjusted Rand Index (ARI) of 0.8975**, suggesting strong alignment with the actual wine classes.
  - Visualization showed clearly separated groups and effective centroid placement.

- **K-Medoids Clustering:**
  - Produced slightly more dispersed clusters.
  - Silhouette Score and ARI values were somewhat lower than K-Means (exact values based on results).
  - Being less sensitive to outliers, K-Medoids showed more flexibility in cluster shapes but at the cost of less tight separation.
  - Medoids (which are actual data points) provided a more interpretable notion of cluster centers in some use cases.

- **Overall Comparison:**
  - **K-Means** was better suited for this dataset due to well-separated clusters and higher ARI.
  - **K-Medoids** may be preferable in noisy datasets or when centroids must be real observations.

---

## Challenges and Decisions

- **Installing K-Medoids:**  
  `KMedoids` from `scikit-learn-extra` was not directly usable due to environment limitations. As a workaround, the `pyclustering` library was used to implement K-Medoids manually, which required adapting its output into a format compatible with sklearn metrics.

- **PCA for Visualization:**  
  Since the Wine dataset has 13 dimensions, PCA was applied to reduce the features to 2D for easier visualization. This step preserved most of the variance and made it possible to visually assess clustering quality.

- **Label Extraction from pyclustering:**  
  `pyclustering` returns clusters as index lists rather than direct labels. A manual reconstruction of predicted labels was needed for evaluation metrics, which added complexity compared to the simpler API of `sklearn`.

- **Choosing Initial Medoids:**  
  In K-Medoids, the initial medoid indices had to be selected manually. This can affect results, so indices were chosen to be spread across the dataset to avoid local optima.

---

## Conclusion

This lab demonstrated how K-Means and K-Medoids perform in practice on a real-world dataset. While K-Means outperformed K-Medoids on the Wine dataset in terms of both accuracy and compactness, the exercise highlighted the importance of algorithm selection based on data characteristics and real-world constraints.
It also reinforced key clustering evaluation concepts such as Silhouette Score and ARI.

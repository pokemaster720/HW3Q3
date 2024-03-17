# HW3Q3

1. **`KNN_LOOCV_wrapper` function:**
   - **Purpose:** To perform KNN classification on a given dataset with LOOCV, returning the classification accuracy and a matrix of distances between instances.
       
   **KNN_LOOCV_wrapper() Function:**
   This function implements the KNN classifier with LOOCV. Given a dataframe `df`, a list of feature indices `feat`, an array `prior_distances`, and a hyperparameter `k` (number of neighbors):

   - It first initializes a `distances` matrix to zero where each element `(i, j)` will eventually represent the distance between sample `i` and sample `j`.
   
   - It then loops through each row in the dataframe. For each row `j`, it treats that row as the "test" sample and calculates the distance between this test sample and all other samples in the dataframe (the "training" samples).
   
   - The distance calculations are made using the Euclidean distance formula.
   
   - After calculating the distances, the function identifies the `k` nearest neighbors to the test sample and their associated class labels.
   
   - The mode of those labels is then computed to determine which class to assign to the test sample. If there's a majority of `1`s, the mode is set to `1`; otherwise, it's `0`.
   
   - If the predicted label matches the actual label, a `1` is entered into the diagonal of the `distances` matrix; otherwise, it remains `0`.
   
   - Lastly, the accuracy is computed as the number of correct predictions divided by the total number of samples, multiplied by 100 to convert it to a percentage.
   
   - The function returns the computed accuracy and the updated `distances` matrix.       
   - **Process:**
     - Calculates the distances between each test instance and the other training instances using Euclidean distance.
     - Determines the `k` nearest neighbors and calculates the mode of their labels to perform classification.
     - Updates a matrix of distances with the calculated distance values, using diagonal entries to store classification correctness (1 if correct, 0 otherwise).
     - Computes accuracy as the ratio of correct predictions over all instances in the dataset.
   - **Returns:** The classification accuracy percentage and the updated distances matrix.

2. **`sfs` function (Sequential Forward Selection):**
   - Purpose:** To sequentially select the best-performing feature set for the KNN classification.
     
    This function implements the Sequential Forward Selection algorithm:
   
   - It starts with an empty model and iteratively adds features that contribute to the highest increase in accuracy, as determined by the `KNN_LOOCV_wrapper()` function.
   
   - It maintains a list of `best_feat` (initially empty) to keep track of the features selected so far.
   
   - In each iteration, it tries adding each of the remaining features (those not already selected) to the list of `best_feat` and observes the change in accuracy.
   
   - It sorts the obtained accuracy values in descending order and updates the `best_feat` list with the feature that brings the highest accuracy improvement.
   
   - If adding a new feature does not improve the accuracy, the algorithm terminates; otherwise, it adds the feature to the `best_feat` list and continues.
   
   - The function returns the final list of selected features and their corresponding accuracies.

  **Timing and running the SFS:**

   - The code sets up a timer to measure how long it takes to run the SFS algorithm.
   
   - The timer starts, `sfs()` is called with the dataframe `x` (which is assumed to be previously defined), and the timer ends after SFS completes.
   
   - The duration of running SFS is printed out.

**Printing the selected features and accuracies:**

   - It creates a new dataframe `df` with the selected features and their accuracies from the SFS run.
   
   - Prints the LOOCV classification accuracies.
     
3. **Final LOOCV Accuracy:**

   - Finally, the script calls `KNN_LOOCV()` (which is not defined in the provided snippet but is assumed to be another function for KNN with LOOCV) with the dataframe `x` and the list of selected features `test_feat`, outputs the accuracy rounded to three decimal places.
  

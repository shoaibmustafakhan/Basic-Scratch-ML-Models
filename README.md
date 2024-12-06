# Flight Delay Time Prediction using Ensemble Learning

This project focuses on predicting flight delay times using an ensemble learning approach. The flight data was processed to create a classification problem, with delay times binned into eight categories (0–7). A stacking ensemble model was implemented, combining four different classifiers to achieve robust predictions.

---

## Features and Data Engineering

### Selected Features:
- **Departure Information**: Scheduled time, estimated time, and terminal.
- **Arrival Information**: Arrival airport, scheduled arrival time, and terminal.
- **Airline Information**: Airline name and flight number.
- **Delay Information**: Actual delay calculated as the difference between scheduled and estimated departure times.

### Feature Engineering:
- **Delay Minutes**: Calculated as the difference between estimated and scheduled departure times, then binned into eight categories.
- **Missing Values Handling**:
  - Numerical: Filled missing values (e.g., delay minutes) with 0, indicating no delay.
  - Categorical: Filled missing values with "unknown" to ensure data completeness.

---

## Ensemble Learning Methodology

The model employs a **stacking ensemble approach** with the following components:

### Base Models:
1. **Logistic Regression**:
   - Built from scratch using gradient descent and the sigmoid function.
2. **Decision Tree**:
   - Implemented with Gini impurity to determine the best splits.
3. **Support Vector Machine (SVM)**:
   - Implemented from scratch with a linear kernel.
4. **Naive Bayes**:
   - Used Gaussian likelihood for feature distributions.

### Meta-Model:
- **Logistic Regression**:
  - Used to combine the predictions of the base models into the final output.

### Why Stacking?
Stacking leverages the strengths of each base model:
- Logistic Regression handles linearly separable data.
- Decision Trees manage non-linear relationships.
- SVMs are robust for classification tasks.
- Naive Bayes is fast and efficient for probabilistic modeling.

By combining these models, the ensemble improves overall predictive performance.

---

## Evaluation Metrics and Results

### Metrics:
- **Accuracy**: Measures the proportion of correct predictions.
- **F1-Score**: A weighted average of precision and recall, useful for addressing class imbalance.

### Model Performance:
- **Accuracy**: 90.08%
- **F1-Score**: 57.46%

The ensemble achieved high accuracy, demonstrating strong predictive performance. However, the lower F1-score indicates areas for improvement, particularly in handling imbalanced classes or difficult-to-predict instances.

---

## Challenges and Solutions

### Key Challenges:
1. **Overflow in Logistic Regression**:
   - Resolved by adjusting the learning rate and limiting iterations during gradient descent.
2. **Divide by Zero in Naive Bayes**:
   - Avoided by adding a small constant (epsilon) to the variance during likelihood calculations.

---

## Future Improvements
- Hyperparameter tuning for base models.
- Exploring additional ensemble techniques like bagging or boosting.
- Enhancing feature engineering for better class separation.

---

## Conclusion
This project successfully implemented a stacking ensemble model for flight delay prediction, achieving over 90% accuracy. The ensemble approach effectively combined the strengths of multiple classifiers, but further optimization could improve the model's handling of complex and imbalanced cases.

---

## How to Use
1. Clone this repository:  
   ```bash
   git clone [<repository_url>](https://github.com/shoaibmustafakhan/Basic-Scratch-ML-Models)
   ```
2. Install required dependencies:  
   ```bash
   pip install -r requirements.txt
   ```
3. Run the model:  
   ```bash
   python main.py
   ```
4. Evaluate the results using the metrics provided.

--- 

This project demonstrates the power of ensemble learning in handling classification tasks, providing a strong foundation for further research and optimization.

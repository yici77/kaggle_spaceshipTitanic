# Kaggle Spaceship Titanic Competition - score:80.827%

*Details and visualize plots are in notebook*

### Initial setup
**1. Imports packages**

**2. Load data**

**3. Observe essential data information**

**4. Change `Transported` to a numeric feature**

**5. Create features from `Cabin` (`Deck`, `Num`, `Side`)**

**6. Create features from `PassengerId` (`GroupID`, `PersonID`)**

**7. Create `TotalSpend` feature by adding all spending features**

**8. Set `PassengerId` as index**

### Analyze the relationship between `GroupID` and other features and fillna

**1. Check if groups share the same features**
- `Side` and `HomePlanet` are the same within the same group
- `VIP` are mostly the same within the same group


**2. Fill missing values with the same group**
- fill in `Side` and `HomePlanet`

### Analyze `Destination`&`HomePlanet` and fillna
**1. Visualize data with plots to identify relationships**
- visualize by countplot
- set `x="Destination", hue=other features`
- set `x="HomePlanet", hue=other features`

**2. Filling some missing values by examination from plots**
- strong correlation between `HomePlanet` and `Deck`
- deck G only from Earth
- deck B, A, C, T only from Europa
- deck D only from Europa and Mars
- deck F only from Earth and Mars
- Earth has no VIP
- `Side` is mostly half and half

**3. Analyze correlations with p-value and Cramér's V**
- Lower p-value indicates higher correlation.
- Higher Cramér's V indicates stronger correlation.
- high correlation between `Destination` and `HomePlanet`
- high correlation between `HomePlanet` and `Deck`

**4. Fill missing values in `Destination` and `HomePlanet` based on p-value and Cramér's V analysis**
- Fill missing `Destination` values based on the distribution within each `HomePlanet`
- Fill missing `HomePlanet` values based on the distribution within each `Deck`

### Analyze spending features and fillna

**1. Observe that `CryoSleep=True` have no spending**

**2. Observe that passengers under 13 have no spending**

**3. Fill missing values in spending features with 0 for `CryoSleep=True` or `Age` under 13**

**4. Set `CryoSleep` to True for passengers over 13 with zero spending**

**5. Fill missing values in `Age`**
- for passengers are under 13(zero spending and not in `CryoSleep`): fill missing values in `Age` with median
- for other passengers: fill missing values in `Age` with median

### Analyze `CryoSleep` and fillna

**1. Visualize proportion of `CryoSleep` in each deck**
- visualize by barplot
- strong correlation between `CryoSleep` and `Deck`

**2. Fill missing values in `CryoSleep` based on the distribution within each deck**ck"**

### Analyze `VIP` and fillna

**1. Observe that no VIP under 13**

**2. Visualize proportion of `VIP` in each deck**
- visualize by barplot
- strong correlation between `VIP` and `Deck`

**3. Fill missing values in `VIP`**
- `"VIP"=False` for age under 13
- fill missing values in `VIP` by groups (by previous examination)
- fill other missing values in "VIP" based on the distribution within each deck

### Analyze "Deck" and fillna

**1. Visualize data with plots to identify relationships**
- visualize by countplot
- set `x="Deck", hue=other features`

**2. Fill missing values in `Deck` based on the distribution within each `HomePlanet`**
- strong correlaiton between `Deck` and `HomePlanet`

### Analyze spending features again and fillna

**1. Fill missing values in spending columns with median**

**2. Create boxplots to visualize the distribution of spending features**
- Observe that spending features have long tail

**3. Log-transform spending features to reduce skewness**

### Dropping

**1. Remove irrelevant columns (`Cabin`, `Name`, `Num`)**

**2. Drop rows with missing values**

### Encoding

**1. Visualize proportion of `Deck` by `Transported`**
- strong correlation between `Deck` and `Transported`

**2. Perform ordinal encoding on `Deck` based on its `Transported` proportion**

**3. Perform one hot encoding on other object features**

**4. Convert object and bool features into numeric"**

### Model Training

**1. Split train data to train and validation data**

**2. Scale all numerical columns**
- prepare for logestic regression and mlp model

**3. Logestic regression**

**4. Random forest**

**5. CatBoost**

**6. Multi-Layer Perceptron (MLP)**

**7. XGBoost**

**8. Stacking**

*RandomizedSearch first, then GridSearch to find the optimal hyperparameters in every models*

### predice test data
- predict by catboost (the highest accuracy)

### save models


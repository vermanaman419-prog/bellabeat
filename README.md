# 📊 Case Study Report on Bellabeat  
**By Naman Verma**

---

## 🎯 Goal  
To analyze Fitbit fitness tracker data to discover usage trends.

## 🧭 Objective  
Apply insights to Bellabeat products (Leaf, Time, Spring, App) and give marketing recommendations.

---

## ❓ Key Questions  
- What are some trends in smart device usage?  
- How could these trends apply to Bellabeat customers?  
- How could these insights shape Bellabeat's marketing strategy?

---

## 🧹 Data Preparation  
The first step was to load the data and ensure the date column was correctly formatted.

```python
import pandas as pd
import matplotlib.pyplot as plt

daily_activity = pd.read_csv("dailyActivity_merged.csv")
daily_activity['ActivityDate'] = pd.to_datetime(daily_activity['ActivityDate'])

```

## 1.Daily Steps Distribution
```
plt.figure(figsize=(8,5))
plt.hist(daily_activity['TotalSteps'], bins=20, edgecolor='black')
plt.title("Daily Steps Distribution")
plt.xlabel("Steps")
plt.ylabel("Frequency")
plt.show()
```
## 2.Steps vs. Calories Burned
```
plt.figure(figsize=(8,5))
plt.scatter(daily_activity['TotalSteps'], daily_activity['Calories'], alpha=0.6)
plt.title("Steps vs Calories Burned")
plt.xlabel("Total Steps")
plt.ylabel("Calories Burned")
plt.show()
```
## 3.Activity Minutes Breakdown
```
activity_minutes = daily_activity[['VeryActiveMinutes', 'FairlyActiveMinutes', 'LightlyActiveMinutes', 'SedentaryMinutes']]
plt.figure(figsize=(8,5))
activity_minutes.plot(kind='bar', color=['red', 'orange', 'green', 'blue'])
plt.title("Average Daily Activity Minutes Breakdown")
plt.ylabel("Minutes")
plt.show()
```


## 4.Average Steps by Day of Week
```
daily_activity['Weekday'] = daily_activity['ActivityDate'].dt.day_name()
steps_by_day = daily_activity.groupby('Weekday')['TotalSteps'].mean()
steps_by_day = steps_by_day.reindex(['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'])
plt.figure(figsize=(8,5))
steps_by_day.plot(kind='bar', color='purple')
plt.title("Average Steps by Day of Week")
plt.ylabel("Average Steps")
plt.show()

```

## This bar chart compares the mean total steps taken on each day of the week.

**Insight:**  
Activity levels are generally consistent on weekdays, but there is a noticeable spike in average steps on **Tuesday** and **Saturday**.  
**Sunday** shows the lowest average, suggesting users are less active on that day.

![Average Steps by Day of Week](images/steps_vs_caloriesburned.png)
```

```
## 🧠 Insights Summary

- Most users average **7K–10K steps daily**
- Positive correlation: **more steps = more calories burned**
- Majority of time is **sedentary (10–12 hrs/day)**
- **Weekends** tend to have **higher step counts**

---

## 💡 Recommendations for Bellabeat

- 🎮 **Gamify step goals** – Badges & streak rewards for hitting 10K steps
- 🧘 **Promote short daily workouts** – “15 minutes a day” campaigns for sedentary users
- 📆 **Weekend activity challenges** – Boost engagement during leisure time
- 🔥 **Highlight calorie-tracking benefits** – Connect step goals to weight management

---

## ✅ Conclusion

This analysis shows how Bellabeat can use data-driven marketing strategies



# How to Calculate a Time Gap Correctly

Finding the time between two clock readings sounds simple until the interval crosses noon, midnight, or a date boundary. This short guide explains a repeatable method for schedules, timesheets, support logs, delivery windows, and study sessions.

## 1. Put both values on the same timeline

Convert each time to minutes after midnight:

```text
total minutes = (hour × 60) + minute
```

For example, 9:35 AM becomes `9 × 60 + 35 = 575`. A 24-hour value such as 17:20 becomes `17 × 60 + 20 = 1,040`.

If the end time is later on the same day, subtract the start total from the end total. From 9:35 AM to 11:10 AM, the gap is `670 − 575 = 95 minutes`, or 1 hour 35 minutes.

## 2. Handle intervals that cross midnight

When the end total is smaller than the start total, the interval probably continues into the next day. Add 1,440 minutes—the length of a 24-hour day—to the end value before subtracting.

Example: a shift starts at 10:45 PM and ends at 1:15 AM.

```text
start = 22 × 60 + 45 = 1,365
end = 1 × 60 + 15 = 75
adjusted end = 75 + 1,440 = 1,515
gap = 1,515 − 1,365 = 150 minutes
```

The correct duration is 2 hours 30 minutes.

## 3. Keep elapsed time separate from clock time

A clock reading tells you where an event sits in a day. A duration tells you how long it lasted. After subtraction, convert the result back to hours and minutes:

```text
hours = floor(total minutes ÷ 60)
minutes = total minutes remainder 60
```

Avoid writing 1 hour 30 minutes as 1.30 hours. In decimal form, 30 minutes is half an hour, so the result is 1.5 hours.

## 4. Check the input assumptions

Before accepting the answer, confirm four things:

- Are both entries in the same time zone?
- Is the date the same, or does the interval cross midnight?
- Are the values 12-hour or 24-hour times?
- Should unpaid breaks be removed from the elapsed time?

Daylight-saving changes also matter for real timestamps. A wall-clock interval can differ from actual elapsed time when clocks move forward or backward. Use full date-time values with a time-zone-aware system when that level of accuracy is required.

## A quick browser check

For ordinary same-zone calculations, the [Time Gap Calculator](https://webtoolsedge.com/tools/time-gap-calculator) provides a fast way to compare two times without building a spreadsheet formula. It is still worth estimating the answer first, especially for overnight intervals, so an AM/PM mistake is easy to spot.

## Useful test cases

| Start | End | Expected gap |
|---|---|---|
| 9:00 AM | 10:00 AM | 1 hour |
| 11:30 AM | 1:00 PM | 1 hour 30 minutes |
| 10:45 PM | 1:15 AM | 2 hours 30 minutes |
| 8:20 AM | 8:20 AM | 0 hours, unless next day is specified |

The most reliable workflow is simple: normalize the inputs, adjust for the date boundary, subtract, convert the result, and then perform a reasonableness check.

---
title: "Question About Open Office Spreed sheet Formula"
date: 2009-09-08
forum: General Help
---

### Post by chandru155 on 2009-09-08
Hi guys,
       1. The value in one Open Office cell(Say A5) is "01/09/2009 9.30 PM". I want to get the first two characters of that cell and display it in another cell(say A7) as "01". For this, what is the formula? I tried using LEFT. ITs not working. Is there any function like SubString?
        2. How to display the total no of days of the month(month of computer date). For example, if the system date is January means, i want to display in one cell as "31". If its September means, it should display as "30"

---

### Post by P4man on 2009-09-09
Assuming the cell is recognized as a date, then all you need to do is use ```
=day(A5)
```
To get the month use =Month(A5)
To get that for the current date you can use =day(now()) or =month(now())

---

### Post by chandru155 on 2009-09-09
Hi,
    Thanks for answering my FIrst question. What about the second question.Can you write a code to get the total no of days in a month
    like this, 

     If(month==1,3,5,7), total =31
     else if(month=2),total=28
     else total=30
(Dont consider about Leep year)

i want a cell to display the total no of days in a month(month of System date)

---

### Post by P4man on 2009-09-09
Have a look in the function wizard and browse through the date/time category. You'll find useful functions like DAYSINMONTH() which is what you're looking for in this case.

=DAYSINMONTH(now())

will give you the number of days in the current month (system date).

---

### Post by chandru155 on 2009-09-09
Thanks., Thank you very much

---


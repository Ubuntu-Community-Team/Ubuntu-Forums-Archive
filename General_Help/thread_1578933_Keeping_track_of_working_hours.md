---
title: "Keeping track of working hours"
date: 2010-09-21
forum: General Help
---

### Post by MrNatewood on 2010-09-21
I would like to have a way to keep track of my working hours easily.

Insert arrival and finish times and have the difference in decimal.
For example, if I start at 8:00 and finish at 9:30, 1.5 should be added.

I tried to do this with Calc but couldn't figure it out. I set one column to have entrance time, another one to have exit time and a third one with the difference("=B2-C2"). The result is in a timestamp format and not decimal. If I use another cell to say something like HOURS(D2) it rounds the number rather than give a decimal(would give 9 for 9:20:00).

Any ideas on how to do this?

EDIT: solved by doing =24*(B2-C2)

---

### Post by pbrane on 2010-09-21
I know you solved this for yourself, but I don't think that solution is correct. I was able to do this by formatting the cells as 24 hour time ( 13:00 ) and changing the format in the total cell from HH:MM to **HH.MM**.

---


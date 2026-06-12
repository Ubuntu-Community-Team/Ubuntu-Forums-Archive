---
title: "date -v"
date: 2011-03-28
forum: General Help
---

### Post by olivo on 2011-03-28
Dear All, 

I need to manipulated dates, i.e. add and or subtract minutes and hours to the current one. 
on my mac I see option -v for the command date:
             Adjust (i.e., take the current date and display the result of the adjustment; not actu-
             ally set the date) the second, minute, hour, month day, week day, month or year accord-
             ing to val.  If val is preceded with a plus or minus sign, the date is adjusted for-
             wards or backwards according to the remaining string, otherwise the relevant part of
             the date is set.

is there any package I can install to get something similar to option -v for date command in ubuntu?

thanks 
Olivo

---

### Post by nice_like_rice on 2011-03-28
You can do

date --date="+10 minutes"

or whatever

---

### Post by olivo on 2011-03-29
thanks. 
This was the hint I was looking for. 
and 
date --date "-1 hour 2010-07-01 05:40:59" will subtract 1 hour to the time/date in input.

---


---
title: "openoffice calc stop number format detection"
date: 2010-10-22
forum: General Help
---

### Post by quickk on 2010-10-22
Hi Everyone, 

   This thing is driving me crazy.  I absolutely HATE this stupid "feature" in openoffice calc.  I am trying to import a csv file that contains some data for a race.  It just so happens that the final time for the competitors is usually around 58 or 59 seconds.  Sometimes though, the time will be more than 60 seconds, and the result sheet will show a time of 60.45s as 1:00.45. 

For some unknown reason, openoffice Calc decides to convert any cell that has this weird number format to a time, and messes everything up.  I just want it to preserve the cell formatting as a number and not change it to time (so I can manually go and fix the few problems)!   I've wasted hours on this stupid thing.  

Alternatively, I would like to be able to set the column to a time format like:  (M):SS.000  where (M) is an optional minute field, SS is the seconds, and 000 is the milliseconds.  I can't find how to specify an optional part, so when I do M:SS.000 and input a time of 59.342 seconds, openoffice converts this to some stupid thing like 12:28.800.

This is really driving me crazy, and any help would be greatly appreciated.

---


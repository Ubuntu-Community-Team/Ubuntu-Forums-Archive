---
title: "openoffice.org subtract two time fields"
date: 2009-09-29
forum: General Help
---

### Post by meditatingfrog on 2009-09-29
Wanted to create a timesheet spreadsheet.  Don't remember doing anything like this in Excel, but wanted to check to see if it was even possible.  I have two cells, a start time, and an end time, want to automatically calculate the difference.  So, if starttime = 09:00 and end time = 15:00, then 15:00 - 09:00 = 6.00.  Or if starttime = 09:30 and end time = 15:00 then 15:00 - 09:30 = 5.50.  

So far, looks like the data format doesn't exist for the result.  
Tried changing the cell format to number with decimals, no luck.
Also tried multiplying the hourly rate ($8) by the field with the number of hours in time format, and value is erroneous.

---

### Post by Littleweseth on 2009-09-30
Googled 'openoffice.org calc time' and got this forum posting where someone tries to solve your *exact* problem;

[http://www.oooforum.org/forum/viewtopic.phtml?t=1305](http://www.oooforum.org/forum/viewtopic.phtml?t=1305)

The short version of that one is 'use separate columns for hours and minutes'.

I don't think there's a data type that deals with this elegantly. See [http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Calc:_Date_&_Time_functions](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Calc:_Date_&_Time_functions) for a discussion of how date and times are handled in OOo - it's not pretty. :|

If you want to do more of your own research, 'openoffice.orc calc timesheet' was a fertile Google search.

Hope this helps.
- L.

---

### Post by SoftPops on 2009-09-30
Have just tried this out and it seems to be working in OOO Calc V3.0.1
 
If the input cells are time formatted as HH:MM (using "format, cells") and the output cell is formatted as numeric with 2 decimal places. The formula in the output cell needs to be "(endtime-starttime)*24.
 
e.g. if start time is in cell D1 and finish time is in cell E1, the formula needs to be "=(E1-D1)*24". This will give decimal hours. I tried a start time of 09:00, an end time of 14:30 and the result was 5.50, with a start time of 10:10 and an end time of 14:30 it gave 4.33.
 
Hope this helps.
 
[COLOR=blue]For Info: Exactly the same principal/formatting also works in Excel.[/COLOR]

---

### Post by meditatingfrog on 2009-09-30
> **SoftPops said:**
> Have just tried this out and it seems to be working in OOO Calc V3.0.1
 
If the input cells are time formatted as HH:MM (using "format, cells") and the output cell is formatted as numeric with 2 decimal places. The formula in the output cell needs to be "(endtime-starttime)*24.
 
e.g. if start time is in cell D1 and finish time is in cell E1, the formula needs to be "=(E1-D1)*24". This will give decimal hours. I tried a start time of 09:00, an end time of 14:30 and the result was 5.50, with a start time of 10:10 and an end time of 14:30 it gave 4.33.
 
Hope this helps.
 
[COLOR=blue]For Info: Exactly the same principal/formatting also works in Excel.[/COLOR]

Thank you SoftPops, worked for me.

---

### Post by SoftPops on 2009-10-01
Pleased to have been of assistance.

---

### Post by Joe Moren on 2012-08-17
> **SoftPops said:**
> Have just tried this out and it seems to be working in OOO Calc V3.0.1
 
If the input cells are time formatted as HH:MM (using "format, cells") and the output cell is formatted as numeric with 2 decimal places. The formula in the output cell needs to be "(endtime-starttime)*24.
 
e.g. if start time is in cell D1 and finish time is in cell E1, the formula needs to be "=(E1-D1)*24". This will give decimal hours. I tried a start time of 09:00, an end time of 14:30 and the result was 5.50, with a start time of 10:10 and an end time of 14:30 it gave 4.33.
 
Hope this helps.
 
[COLOR=blue]For Info: Exactly the same principal/formatting also works in Excel.[/COLOR]
Works for me in LibreOffice 3.5.4.2 also! Many Thanks, Joe

---

### Post by wildmanne39 on 2012-08-17
Old thread closed.

---


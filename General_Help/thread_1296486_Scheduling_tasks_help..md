---
title: "Scheduling tasks help."
date: 2009-10-20
forum: General Help
---

### Post by Saidear on 2009-10-20
Heya, I recently converted to Ubuntu and I was wondering if this was possible:  I do a daily planner a week in advance, and I would like it if Ubuntu could email a specific page of the planner so that I could print it off at work, then deleted the page out of the .pdf file.  For example: Page 1: Thursday Page 2: Friday Page 3: Saturday Page 4: Sunday Page 5: Monday  Any suggestions?

---

### Post by hurdevan on 2009-10-20
You should be able to configure Evolution mail client to do that for you.

Yea setup Evolution with your mail provider and then click on Calender(Bottom left in Evolution).
Right click on, lets say 7 AM, and make an New Appointment.
Fill in the summery (and anything else you want) then click on Alarms or find it in the menu. You want a select a Custom Alarm then Click Add and you should have everything you need. After a little poking about you should find the option to Send an Email when the alarm goes off. Then back at the Appointment box you need to find the option to set the recurrence. 

After a little bit of exploring then you should find what you need. 

Cheers

---

### Post by Saidear on 2009-10-21
Ok, that solves that part.. but how to seperate the individual pages of the .pdf out?

Thank you for the help by the way!

---

### Post by hurdevan on 2009-10-21
It sounds like the pdf file changes ever week that's why you can't just split it manually once... Right?

OK... I found the program you want...pdftk
To install type:

sudo apt-get install pdftk

After installation is done then to split a file you need to type this command into the terminal.

pdftk A=inputfile.pdf cat A1-1 output putputfile1.pdf

This get page 1 separate...

pdftk A=inputfile.pdf cat A2-1 output putputfile2.pdf

...and this separates page 2.
You will nee to do this for every page so we will make it easier. Lets put it in a script.
basically here is the script:
  
```
#!/bin/sh
#
#Change both of these to the proper path.
#This is the location of the file you want to split
FILE="/home/user/test.pdf"
#this is the Directory in witch you want to save the split file
OUTDIR="/home/user/"

pdftk A=$FILE cat A1-1 output $OUTDIR"day1.pdf"
pdftk A=$FILE cat A2-1 output $OUTDIR"day2.pdf"
pdftk A=$FILE cat A3-1 output $OUTDIR"day3.pdf"
pdftk A=$FILE cat A4-1 output $OUTDIR"day4.pdf"
```

save this as (something).sh someplace in your home folder and then set the permissions to allow this script to run as a program. 
To do that right click, goto Properties, then goto permissions and it should be in there someplace.

When you have that configured then you can schedule this to run early Thursday morning So all that you have to do is get your pdf file(delete the old ones) and rename it(lets say...) test.pdf so that the script can find it. And you will have to make sure that it is in the directory configured in the script.

Anyways you get the point(or you had the point).


Cheers

---


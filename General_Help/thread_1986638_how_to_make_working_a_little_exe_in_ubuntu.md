---
title: "how to make working a little exe in ubuntu"
date: 2012-05-25
forum: General Help
---

### Post by michaelibre on 2012-05-25
Hi everybody,
how can I make working a little exe programm (95,5Ko) in ubuntu 12.04?
where can i find easy documentation and information about how to do it? (little time, no programming)
thank you

---

### Post by roelforg on 2012-05-25
First of all: No .exe's on linux, just binaries (same thing but it's something to pay attention to).
 
Second of all: Not gonna happen. You can't make a program without programming (even if it's just a little).

---

### Post by Erik1984 on 2012-05-25
That's a Windows program, Ubuntu is Linux. You might have some luck with Wine (it can be installed from the software center) Wine can run Windows executables, sometimes works, sometimes not.

---

### Post by nevius on 2012-05-25
> **michaelibre said:**
> Hi everybody,
how can I make working a little exe programm (95,5Ko) in ubuntu 12.04?
where can i find easy documentation and information about how to do it? (little time, no programming)
thank you

Install wine. See if it works in wine.

---

### Post by michaelibre on 2012-05-25
I installed wine (i am in 10.04), it took a time and i launched the program:
it is a program to calculate the exact sunrise and sunset time for any location in the world, you have to fill in information (all this worked fine) and then press a calculate button that takes normally 5sec to process and give the timings but with wine he was processing for 10minuts and i finally forced the shuting down of the computer.
it is such a little program, could it be transformed for ubuntu and be useful for a whole community who may want to change to ubuntu and use this program?

thank you for your help

---

### Post by Erik1984 on 2012-05-25
I would be surprised if there is no Linux alternative for those calculations. Stellarium is in the repositories and should contain such data, however it's a bit overkill if you only want to know when the sun rises :P I use this site for that: [http://www.heavens-above.com/](http://www.heavens-above.com/) set the location to where you are and see 'sun' under 'Astronomy'.

---

### Post by michaelibre on 2012-05-25
hi, this exact program is needed, it is actually for a therapy where exact time (at the second) is needed for each day of the year and with this program you have the whole year in two A4 papers! 
[http://www.homatherapy.org/](http://www.homatherapy.org/)

---

### Post by flemur13013 on 2012-05-25
"Homa therapy" will work just as well by calculating the times with:

> $ rand

---

### Post by samitharansara on 2012-05-25
> **roelforg said:**
> First of all: No .exe's on linux, just binaries (same thing but it's something to pay attention to).
 
Second of all: Not gonna happen. You can't make a program without programming (even if it's just a little).

+1 for this ;)

---

### Post by michaelibre on 2012-05-25
I installed "rand" but it is just to give random numbers....
I ask real help not jokes
Thank you

---

### Post by oldfred on 2012-05-25
In synaptic under sunrise, it get these.

Remind:
> It also features: sophisticated date calculation, moon phases,
sunrise/sunset, Hebrew calendar, alarms, PostScript output, tcl/tk
front-end and proper handling of holidays.


> Wyrd displays reminders on a browsable time table along with a
calendar and lets the user create new timed or untimed reminders.
Using the remind backend, it is possible to convert the calendar to
PostScript for printing and to synchronize it with Palm handhelds.

And two perl based libraries 

libdatetime-event-sunrise-perl
Calculate sunrise and sunset for a given time and place
libdatetime-astro-sunrise-perl
module for computing the time of sunrise and sunset

---


---
title: "How to Set Time in MeerKat?"
date: 2010-12-14
forum: General Help
---

### Post by Sky Aisling on 2010-12-14
Hello,
I just installed MeerKat on a Compaq Presario 2100US with 1 gig of RAM.
How do I set the time correctly?
I checked the Compaq set up screen and time is correct there.
The install asked for my time zone.  I'm in Seattle area so chose Vancouver.
Time now showing in systray is four hours off but can't find any way to re-set it?
Any help would be appreciated.  Thank you

---

### Post by spiky001 on 2010-12-14
Have you tried right clicking on the time then go to preferences

---

### Post by Sky Aisling on 2010-12-14
Yes, there are no options to set the time there.

---

### Post by spiky001 on 2010-12-14
What happens if you type ```
date
```

---

### Post by Sky Aisling on 2010-12-14
Tues Dec 14 06:45:14 PST 2010

Which is what is showing on clock.

---

### Post by Sky Aisling on 2010-12-14
Correct time here is 2:46 pm (give or take a minute)

---

### Post by spiky001 on 2010-12-14
See if this page helps [http://codeghar.wordpress.com/2007/12/06/manage-time-in-ubuntu-through-command-line/](http://codeghar.wordpress.com/2007/12/06/manage-time-in-ubuntu-through-command-line/)

---

### Post by Sky Aisling on 2010-12-14
Thank you, I'm reading it now.

---

### Post by mick222 on 2010-12-14
click on clock under the calender it should say locations click edit and add your location there.

---

### Post by Sky Aisling on 2010-12-14
Thank you, that did it.

[http://codeghar.wordpress.com/2007/12/06/manage-time-in-ubuntu-through-command-line/](http://codeghar.wordpress.com/2007/12/06/manage-time-in-ubuntu-through-command-line/)
**Set Time**

 To change time means to set a new time. To set time in Ubuntu (or any Linux), just run the following command
 sudo date *newdatetimestring*
 where *newdatetimestring* has to follow the format *nnddhhmmyyyy.ss* which is described below
 
[LIST]
[*]*nn* is a two digit month, between 01 to 12
[*]*dd* is a two digit day, between 01 and 31, with the regular rules for days according to month and year applying
[*]*hh* is two digit hour, using the 24-hour period so it is between 00 and 23
[*]*mm* is two digit minute, between 00 and 59
[*]*yyyy* is the year; it can be two digit or four digit: your choice. I prefer to use four digit years whenever I can for better clarity and less confusion
[*]*ss* is two digit seconds. Notice the period ‘.’ before the ss.
[/LIST]
 Let’s say you want to set your computer’s new time to December 6, 2007, 22:43:55, then you would use:
 sudo date 120622432007.55

---

### Post by Sky Aisling on 2010-12-14
For beginners reading this thread:

These commands are done through the 'terminal' **Applications/Accessories/Terminal**
*not*
through your desktop GUI interface (the pretty boxes and colorful words).

In general,  sure seems like there should be a GUI way of changing the date and time.  A lot  of  geeky stuff  just to change date and time.

---


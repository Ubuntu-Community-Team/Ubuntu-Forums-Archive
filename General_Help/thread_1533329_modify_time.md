---
title: "modify time"
date: 2010-07-17
forum: General Help
---

### Post by fgadea on 2010-07-17
I am trying to modify the time in my computer. I go to "sistem/time and date" and it opens a time zone selector. I click in the key icon and I introduce my password and it enables me to change stuff, but this is what happens:

-in "configuration" there are two options: "sinchronize with internet server" and "manual". As I don't want to sinc with internet, I choose manual, but when I change the numbers with the arrow selectors, after a second it turns back to previous setted time.

-looking for this problem in the web I found the "date" operator, so in the terminal window I type 

me@mymachine: ~$ sudo date -u mmddtttt 

being it: month, day, time and minutes, and it asks for my pass, I give it, I press enter and everything is ok, but the time in my machine keeps as allways, and if I go again to "sistem/time and date", everything is as if I have done nothing. 

I use the date operator to see if I changed the date or not, and it gives me the date I wanted to set, but orage keeps showing the previous wrong time. 

This might be a simple problem for others, but I don't know what to do, and I don't know why such a thing is this difficult to do.

Thankyou for any help.

---

### Post by WorMzy on 2010-07-17
Perhaps your BIOS doesn't allow date modification to be done by operating systems. You should be able to change the clock by going into the BIOS settings at boot time and changing them there.

---

### Post by fgadea on 2010-07-18
I checked the BIOS and it seems that it is not that (sistem time reflects what I do through "date -u"). So that also shows that there is no privilege problem not solved with sudo, one of my dubts. The question is why the time manager does not respect the "manual" setting (and I really don't want to sync with internet time, not at all).
Also: is this a xubuntu problem? or is it only mine.
It seems that this is not a common thread in the forum, but I installed the same xubuntu in my girlfriend's netbook and the same time setting problem shows up.
Thanks, WorMzy, for your quick response.

---


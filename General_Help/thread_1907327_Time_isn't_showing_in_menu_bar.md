---
title: "Time isn't showing in menu bar"
date: 2012-01-11
forum: General Help
---

### Post by ghendric on 2012-01-11
I recently upgraded to Ubuntu 11.10 and now the time doesn't show in the top menu bar. The only thing that shows is the word "Time" and if I click it, I only see a calendar and the date. I have the settings set to show the time but it doesn't. I've attached a screenshot. How do I get it to show the time? or Date and time?

Thanks

---

### Post by xc3RnbFO8P on 2012-01-11
Install indicator-datetime from the software center

---

### Post by guestolo on 2012-01-11
I new I seen this problem before, just couldn't remember where 

But then I found the following posted by [ebelhaire]("http://ubuntuforums.org/member.php?u=1470940")
> The update suppresses the file /etc/timezone and this is at the origin  of the problem of "Time" display. The file can be restored with the  command :

**sudo dpkg-reconfigure tzdata**Here's the link
[http://ubuntuforums.org/showthread.php?t=1860622](http://ubuntuforums.org/showthread.php?t=1860622)

---

### Post by ghendric on 2012-01-12
> **guestolo said:**
> I new I seen this problem before, just couldn't remember where 

But then I found the following posted by [ebelhaire]("http://ubuntuforums.org/member.php?u=1470940")
Here's the link
[http://ubuntuforums.org/showthread.php?t=1860622](http://ubuntuforums.org/showthread.php?t=1860622)

Cool! That fixed it! Thanks!

---


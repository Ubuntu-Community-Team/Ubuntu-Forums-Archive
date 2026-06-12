---
title: "time in bios changes"
date: 2012-08-04
forum: General Help
---

### Post by serpentracer on 2012-08-04
hello everyone.  I have a annoying issue with 12.04.  it keeps changing my bios time.  I have the clock set in ubuntu to the correct time but when I shut it down and boot back up the bios clock is set a few hours off again every time. (only happens after I use ubuntu) the battery is not dead.

I also use windows 7 (seperate drive) and that's how I realized the bios time was wrong.   in windows it goes by the bios time.  when I set it correctly in the bios and shut it down it never changes.  it only changes once I boot ubuntu again.

what the heck is going on and how do I correct it?

---

### Post by mcduck on 2012-08-04
Your problem is caused by both Windows and Linux using the system clock from BIOS, but while Windows assumes the system clock is running in your local time, Linux (like most Unlix-like operating systems) assumes the system clock to run in UTC time instead.

Here's a guide for either configuring Ubuntu to consider CMOS time as local time instead of UTC, or for configuring Windows to use UTC. Whichever way you prefer... :)
[https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts]("https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts")

---

### Post by Cheesemill on 2012-08-04
Deleted

---

### Post by serpentracer on 2012-08-04
thanks folks.

---


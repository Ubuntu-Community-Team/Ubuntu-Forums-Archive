---
title: "Time/Timezone problems"
date: 2006-04-10
forum: General Help
---

### Post by jimmyj on 2006-04-10
I noticed people are having similar problems, but I am having completely different ones.

My timezone is properly set to America/Vancouver, but the Date & Time Control Module says my current time zone is UTC. When I reset the timezone and the time, it changes timezones to PDT, but the clock in the bottom RH corner changes to 7 hours in the future. 

$ date
Tue Apr 11 03:42:33 UTC 2006

However, my real time is Mon Apr 10 20:42:33 PDT 2006.

I have looked many places and not seen someone having this problem. Any advice?

---

### Post by jimmyj on 2006-04-11
Got help from an old thread. used apt-get to install timezoneconf and ran sudo dpkg-reconfigure timezoneconf. This fixes the time in the corner, when I alter the time through KDE's panel it screws up again.

Most importantly, mythtv's listings are still 7 hours off. Any suggestions would be welcome.

---

### Post by aysiu on 2006-04-11
Maybe [this](http://ubuntuforums.org/showthread.php?t=6285) will help.

---


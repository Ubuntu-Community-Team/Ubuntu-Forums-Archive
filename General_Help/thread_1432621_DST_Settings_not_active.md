---
title: "DST Settings not active"
date: 2010-03-18
forum: General Help
---

### Post by Jabrouwer on 2010-03-18
I'm running Mint, and my system time has moved forward yet.  I've tried manually changing the time, but it changes back after reboots.  
Here's my zdump output:
```
/etc/localtime  Sun Apr  4 07:59:59 2010 UTC = Sun Apr  4 01:59:59 2010 CST isdst=0 gmtoff=-21600
/etc/localtime  Sun Apr  4 08:00:00 2010 UTC = Sun Apr  4 03:00:00 2010 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Oct 31 06:59:59 2010 UTC = Sun Oct 31 01:59:59 2010 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Oct 31 07:00:00 2010 UTC = Sun Oct 31 01:00:00 2010 CST isdst=0 gmtoff=-21600
CST6CDT         Sun Mar 14 07:59:59 2010 UTC = Sun Mar 14 01:59:59 2010 CST isdst=0 gmtoff=-21600
CST6CDT         Sun Mar 14 08:00:00 2010 UTC = Sun Mar 14 03:00:00 2010 CDT isdst=1 gmtoff=-18000
CST6CDT         Sun Nov  7 06:59:59 2010 UTC = Sun Nov  7 01:59:59 2010 CDT isdst=1 gmtoff=-18000
CST6CDT         Sun Nov  7 07:00:00 2010 UTC = Sun Nov  7 01:00:00 2010 CST isdst=0 gmtoff=-21600
```

How can I get the time to change, whether through corrected DST rules, or just a manual time change?

---

### Post by Jabrouwer on 2010-03-18
Nevermind, I installed tzdata, and then used "sudo dpkg-reconfigure tzdata" to select my time zone (even though I swear linux already knew what time zone I am in) and the time was set right.

---


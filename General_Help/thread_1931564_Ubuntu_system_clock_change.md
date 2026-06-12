---
title: "Ubuntu system clock change"
date: 2012-02-25
forum: General Help
---

### Post by liege102273 on 2012-02-25
I have two hard drives, one with only Win7 and one with only Ubuntu.  When I restart and select the drive with Ubuntu on it, the time is correct for Pacific time.  When I shut down and then restart in Windows on the other drive, the clock is now set to GMT, +8 hours.  

What can I do to keep Ubuntu from changing the time?

Thanks for any help!

---

### Post by HeroOfCanton on 2012-02-25
Linux should in no way affect the time *zone* settings in windows (that I know of). Is it altering the BIOS system time or is it just the zone settings?

Be sure when changing the time in ubuntu (or Windows) you are doing it through the time zone settings and not by actually changing the system time. Then both should sync up properly.

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by liege102273 on 2012-02-25
Thanks!  I went into /etc/default/rcS and changed the "UTC=yes" to "UTC=no" using vi at a terminal.

Problem solved.

---


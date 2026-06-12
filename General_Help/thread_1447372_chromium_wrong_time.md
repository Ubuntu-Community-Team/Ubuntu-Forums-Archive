---
title: "chromium wrong time"
date: 2010-04-05
forum: General Help
---

### Post by nixIT on 2010-04-05
Hello all,

I am running Ubuntu 9.04 and Chromium 5.0.365.0 (42923) Ubuntu.

Last week I noticed when in gmail that the time of all emails and gchat's were off by 5 hours (5 hours ahead), I checked all my time settings in chrome and Ubuntu and they are all correct (GMT-5 for EST).

When I load up Firefox and go into gmail, the time in email and gchat is correct.

Is this a Chrome issue, or a Ubuntu Chrome issue?  Is anyone else experiencing this?

--nixIT

---

### Post by clhsharky on 2010-04-05
HI


I have Chromium 5.0.368.0 (43430) Ubuntu and have not experiencing that problem. Chromium has always fixed its self with in a day or two of any glitches I've experienced through updates.


Sharky

---

### Post by pataphysician on 2010-04-05
i run daily chromium builds and had this problem for about two weeks. updates never fixed it (i'm using 5.0.368.0 (43430) Ubuntu). same as you, i'm on eastern time and was seeing everything in chromium at five hours ahead. it wasn't just at google sites. every site that was trying to use my local time was showing it incorrectly. other browsers and applications were ok.

i found out that my bios clock was set to utc. each time i corrected that, the time would revert when i rebooted. following the last post here

[http://www.tomshardware.com/forum/236531-50-linux-changing-bios-clock](http://www.tomshardware.com/forum/236531-50-linux-changing-bios-clock)

i edited /etc/default/rcS and changed UTC=yes to UTC=no.

so, try editing that file. then reboot and set your bios clock to local time. it should stay that way. i believe doing "sudo hwclock" in a terminal can verify it. alternately, i guess you can boot into linux, then reboot and double-check.

---


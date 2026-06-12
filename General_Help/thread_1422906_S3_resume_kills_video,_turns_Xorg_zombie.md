---
title: "S3 resume kills video, turns Xorg zombie"
date: 2010-03-05
forum: General Help
---

### Post by neurophyre on 2010-03-05
Hello,

I'm running 9.10 on an HP d530 SFF, Pentium 4 2.8GHz HT w/800MHz FSB and 512KB L2, 1.25GB DDR333 RAM, GeForce 440MX.  In the BIOS I have ACPI S3 Video REPOST enabled, as well as ACPI S3 Hard Disk Reset enabled.  Resuming had the same problem with either of these settings disabled as well.

Install graphics driver is nvidia-glx-96, version 96.43.13-0.  To my knowledge, this is the newest driver that supports the GeForce 440MX -- I attempted to upgrade to newer drivers for XBMC before but they do not support the card.

uname -a output:

Linux fahrenheit 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

When I attempt to suspend this machine it suspends fine, and will come back to life when I press the power button.  I then get a hardware (text mode) cursor for a few seconds, then the screen blanks and goes black.  At this point I can ssh into the machine and it is responsive, mostly, but Xorg is taking up 100% CPU and the fan spools up to maximum.  The Xorg process is unkillable -- kill -9 won't do it.  Load avg on the machine is high and it gets freeze-y for a few seconds at a time.

Any tips on getting either suspend or hibernate working would be greatly appreciated.  This is a media box and we'd like the convenience of a quick resume time, but the ability to save electricity when it is not in use.

---

### Post by neurophyre on 2010-03-07
...any howtos I should read that don't involve hacking the realtime clock?  :/

---

### Post by NetDesignate on 2010-12-12
> **neurophyre said:**
> Hello,

I'm running 9.10 on an HP d530 SFF, Pentium 4 2.8GHz HT w/800MHz FSB and 512KB L2, 1.25GB DDR333 RAM, GeForce 440MX.  In the BIOS I have ACPI S3 Video REPOST enabled, as well as ACPI S3 Hard Disk Reset enabled.  Resuming had the same problem with either of these settings disabled as well.

Install graphics driver is nvidia-glx-96, version 96.43.13-0.  To my knowledge, this is the newest driver that supports the GeForce 440MX -- I attempted to upgrade to newer drivers for XBMC before but they do not support the card.

uname -a output:

Linux fahrenheit 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

When I attempt to suspend this machine it suspends fine, and will come back to life when I press the power button.  I then get a hardware (text mode) cursor for a few seconds, then the screen blanks and goes black.  At this point I can ssh into the machine and it is responsive, mostly, but Xorg is taking up 100% CPU and the fan spools up to maximum.  The Xorg process is unkillable -- kill -9 won't do it.  Load avg on the machine is high and it gets freeze-y for a few seconds at a time.

Any tips on getting either suspend or hibernate working would be greatly appreciated.  This is a media box and we'd like the convenience of a quick resume time, but the ability to save electricity when it is not in use.
Did you ever get any feel for what is going on with this issue ?
I have an xw9300 which has very strange behaviour similar to what you are describing (but it is running windows7, not Ubuntu).
I have been fighting with it for some time.

Thanks.
Don

---


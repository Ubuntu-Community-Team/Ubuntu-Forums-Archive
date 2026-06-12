---
title: "Bootchart of Ubuntu 10.10"
date: 2010-11-15
forum: General Help
---

### Post by ravisghosh on 2010-11-15
Here is the bootchart from my machine. 

[http://img695.imageshack.us/img695/893/greenheadmaverick201011.png](http://img695.imageshack.us/img695/893/greenheadmaverick201011.png)

Boot Time: 22 secs (from Grub to Login screen)

Any suggestions to reduce boot time? Can't make any sense of this bootchart.

---

### Post by efflandt on 2010-11-15
"700 RPM SATA"?  I think you are missing a digit.  What do you get  for **sudo hdparm -t /dev/sda**?

---

### Post by a-user on 2010-11-15
i wished my boot time would be so fast. since i switched to the nvidia proprietary drivers it increased from 8 sec to 35 - i have a ssd. but at least i do not boot often.

---

### Post by ravisghosh on 2010-11-16
> **efflandt said:**
> "700 RPM SATA"?  I think you are missing a digit.  What do you get  for **sudo hdparm -t /dev/sda**?

Here is what I'm getting:

[B]shantanu@GreenHead:~$ sudo hdparm -t /dev/sda
[sudo] password for shantanu:

/dev/sda:
 TIming buffered disk reads: 240 MB in 3.00 seconds = 79.96 MB/sec
[/B]

---


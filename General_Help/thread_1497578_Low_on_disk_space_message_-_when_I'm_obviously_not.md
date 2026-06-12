---
title: "Low on disk space message - when I'm obviously not"
date: 2010-05-30
forum: General Help
---

### Post by GlennD09 on 2010-05-30
Hi, complete noob to Ubuntu here, I've had it for a few weeks, no glitches or errors until now.

I just booted it up and it said I had 60mb hard disk space left.
I go onto disk usage analyzer from the message and it reads this

Total filesystem capacity: 41.8 GB (used: 11.8 GB) available 30.0 GB. 

Anyone know why this error message comes up?

---

### Post by GlennD09 on 2010-05-30
bump

---

### Post by drs305 on 2010-05-30
Do you have separate partitions such as a /boot, /home, etc that may be filling up even though your total disk space is still large?

You might take a look at a disk space guide I posted:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

It contains several useful terminal commands to see the status of your disk space (such as "df -Th"), some notes about using Disk Usage Analyzer, and reasons why partitions may be filling up and how to solve the problem.

---

### Post by Ray716 on 2010-05-30
I had the same problem for my system... my main partition was too full, and my bump partition was too small... even though i had almost nothing on my hard drive. re-partitioning things worked for me.  the sugestions made by "drs305" are good ones, and it is what worked with my computer.

Ray

---


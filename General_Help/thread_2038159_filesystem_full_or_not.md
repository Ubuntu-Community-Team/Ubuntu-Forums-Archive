---
title: "filesystem full or not?"
date: 2012-08-06
forum: General Help
---

### Post by Subito Piano on 2012-08-06
Hi! I keep getting notices that my /home folder is full. In terminal:
```
dad@dad:~$ df -l
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1        8169144   4245512   3508656  55% /
udev              955112         4    955108   1% /dev
tmpfs             386148       988    385160   1% /run
none                5120         0      5120   0% /run/lock
none              965360         0    965360   0% /run/shm
/dev/sda3      139719396 132620928       868 100% /home
/dev/sdb1        7808348    195012   7613336   3% /media/LEXAR
```
However, GParted indicates that the partition home is located in has over 6GB free! Any ideas?

---

### Post by marinara on 2012-08-06
it's full.  Ext4 and others reserve 5% of space for the root user so you don't run out of space catastrophically.  

If my above guess isn't right, i donno what is.

---

### Post by Subito Piano on 2012-08-06
Right on.  6.5 gigs is 5% of the total 135 GB partition.  I found a hidden trash file at the highest level of /home, cleaned it out (21 MB!) and now everything is copacetic at 85% full.  Still need to clean old junk out but now things seem to be working.  Thanks for your help!

---

### Post by claracc on 2012-08-06
If you have fixed your problem, please mark the thread as solved with "thread tools" in the right upper part of the page.

---

### Post by 1clue on 2012-08-06
Convention dictates that a partition should be no less than 10% free or you get fragmentation issues and degraded performance.  Personally I think that an actively written volume should be at least 25% free, preferably more.  I think the 10% figure is when degradation becomes noticeable.

---

### Post by Subito Piano on 2012-08-06
oh - THAT's how it's done!

---


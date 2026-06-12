---
title: "Hard disc space missiing, please read the thread"
date: 2010-01-24
forum: General Help
---

### Post by alexandrius on 2010-01-24
HI, i'm very new for Linux so sorry if i sound noob
Nautilus shows that i've 53.4 gb of free space:
[IMG]http://i48.tinypic.com/25fr2h1.png[/IMG]

when Disk Usage Analyser says that, i have 58.0 gb of free space:
[IMG]http://i47.tinypic.com/5f245y.png[/IMG]

WTF?

Thanks :)

---

### Post by r_s on 2010-01-24
Disk analyzer also takes into account all the other partitions mounted . type df in terminal to know how much space linux is actually using.

---

### Post by mcduck on 2010-01-24
Disk Usage Analyzer tells you the amount of free space on the drive itself, Nautilus tells you the amount of free space available to current user.

(5% of disk space on Ext partitions is reserved to root user only, so it doesn't count as available free space for any normal user.)

---

### Post by alexandrius on 2010-01-25
> 5% of disk space on Ext partitions is reserved to root user only, so it doesn't count as available free space for any normal user.)
Thanks, BTW i had only one partition mounted

---

### Post by Doc_Jude on 2010-01-25
I have a similar question
Just got a new T61 off of Ebay, the auction said 250gig HD, I did a complete install of Ubuntu 9.04 and the disk usage analyzer says:
[SIZE=3]
Total filesystem capacity: **220.8 GB** (used: 2.9 GB    available: 217.8 GB)[/SIZE]


does Ubuntu use up 30 gigs of space????


signed, 
***Confused***

---

### Post by underquark on 2010-01-25
Partly the way Kb, Mb, Gb are calculated (x 1000, x 1024 etc.), partly the effect of formating a disk and partly ubuntu.  It is usual with all commonly-used file-systems that the advertised capacity of the disk translates into a significantly leser capacity available.  Even then you will be unlikely to fully use all space as disks are split up into sectors and some files will occupy only part of a sector.
 
Imagine you had a wall and meaured its area as 6 square metres.  Then you calculated the areas of all your books and found that they totalled six square metres.    By the time you put up the shelves and arrange the books you will find that you have many left over.

---

### Post by alexandrius on 2010-01-25
**underquark**
> Imagine you had a wall and meaured its area as 6 square metres. Then you calculated the areas of all your books and found that they totalled six square metres. By the time you put up the shelves and arrange the books you will find that you have many left over.
Thanks for good explanation

---


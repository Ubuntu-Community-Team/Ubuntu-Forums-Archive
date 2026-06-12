---
title: "Partitioning, multi OS and Install"
date: 2010-12-28
forum: General Help
---

### Post by oldschoolboy on 2010-12-28
I am new to Ubuntu, partitioning, and multi-boot.  I have always used windows but am very interested in the Ubuntu.  I have been researching partitioning and need some advise on the amount of partitions and need some advice.

Thinking about partitioning 640 GB drive as follows:

1 - 50 GB - Windows 7
2 - 50 GB - windows XP
3 - 50 GB - AutoCAD, office, windows programs, etc.
4 - 50 GB - File storage for #3
5 - 100 GB - Media (Photos, Music, Video) Mainly pictures
6 - 100 GB - Backup files for #1 and #2
7 - Rest of Drive general storage or other beta OS's

Also have a 30 GB SSD that I was going to use to play around with Ubuntu.

1 - 28 GB - Ubuntu
2 - 2 GB - swap partition

System is as follows:
Windows XP 
Dual Core 6300 @ 1.86 GHz
2 GB Ram
DVD RW
GeForce 9600 GT
Currently 250 GB hard drive unpartitioned (will be switching over when I get comments back on the above)

Anyone know if a good step by step of partitioning and multi-OS booting procedures (how to's)

Thanks for any and all help, comments, or questions

---

### Post by Elfy on 2010-12-28
Whatever you do - install ubuntu last.

The one thing I would say - if you are going to be using specific partitions to store data, that is how it appears - is there a real need for the w7 and XP partitions to be so large?

I also would advise that if you do go for that only have 2 primaries - for W7 and XP then create an extended for all the other partitions. Then if at a later date you want to add a primary you can.

I'm not sure about SSDs - but it might be better to put the swap on the 640Gb drive.

---

### Post by oldschoolboy on 2010-12-28
What would be a good size for the w7 and XP primary partitions? 
Why would you suggest the swap on the 640 GB drive?

---

### Post by Elfy on 2010-12-28
> **oldschoolboy said:**
> What would be a good size for the w7 and XP primary partitions? 
Why would you suggest the swap on the 640 GB drive?

I'm afraid I have no idea - XP is a long time ago now and W7 is an undiscovered country to me. Just put it there as a thought ... 

As far as the swap goes - and SSDs are much too new for me to even think about yet - I was/am under the impression from reading stuff here that it'd be better on the SATA.

Don't take my answers as gospel.

---


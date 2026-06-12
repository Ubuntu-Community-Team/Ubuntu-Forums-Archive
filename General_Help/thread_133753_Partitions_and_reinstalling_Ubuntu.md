---
title: "Partitions and reinstalling Ubuntu"
date: 2006-02-20
forum: General Help
---

### Post by eight_car on 2006-02-20
While learning on how to make my stsem work better, I have messed up a couple things.

I would like to do a clean install and have one question ....

My system has 2 HDD's. One HDD has my root and swp parition, the other HDD has my /home partition.

How do I re-install Ubuntu and be able to access my /home folder as normal? (as in keeping access to all my info stored on it)

---

### Post by shams2 on 2006-02-20
while installation select the custom partition option, in the next window you will see your both hard disks partition tables, select your first hard disk /dev/hda the first line is for the mount point select the mount point for / the second line is to format the partition select that and hit enter to select the format option, for the second hd select the first line and mount as /home and go on to complete your installation.

---


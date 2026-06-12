---
title: "Hard disk free space mismatch"
date: 2012-05-07
forum: General Help
---

### Post by achu91 on 2012-05-07
i am new to Ubuntu. i found a peculiar problem in my 2 pc where i installed Ubuntu 12.04. in one of the PC The hard disk total space is 160GB and the swap space is 4.8GB. so the "\" partition should have at least 155 GB but i have attached 3 screen shot which conatines the output of various options to see the hardsik free space  ,but all the three results  gives me  various free space & total disk space.Kindly guide me if i am wrong in understanding the basics of disk uasge/linux systems .or is it a installation problem?.

Please do reply.

Achuthan.P

---

### Post by oldfred on 2012-05-07
I do not think you have a problem. My 160GB drive shows 149.05GiB in gparted.

Part of the issue is GiB vs. GB.

[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)
It's the difference between gigabytes (GB) and gibibytes (GiB). One gigabyte = 1000 x 1000 x 1000 bytes (base 10). One gibibyte = 1024 x 1024 x 1024 bytes (base 2).

Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).

Some tools now use GiB, and some may use GB, just to add to the confusion.

---

### Post by achu91 on 2012-05-07
i am happy to hear that my installation doesnt have a problem.again i ran gparted it shows my free space as 66GB (screen shot attached).Now i would like to know which is the correct value of free space.whether it is output of gparted,df-h,nautlius etc.please do help me yo understand.

---

### Post by jerome1232 on 2012-05-07
They are both correct. Gparted is counting the 5% of space reserved for root as free space while df -h does not count the 5% of space reserved for root as free space.

The math adds up on my system. For the record GiB is supposed to represent 1024 while GB is supposed to represent 1000, no one pays attention to the standard though.

---

### Post by achu91 on 2012-05-08
so i need to  consider the free space result given by  df -h and work accordingly   and one neednot bother reg the free space result given by gparted right?.

---


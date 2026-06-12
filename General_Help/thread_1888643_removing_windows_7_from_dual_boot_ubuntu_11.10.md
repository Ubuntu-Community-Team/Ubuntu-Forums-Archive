---
title: "removing windows 7 from dual boot ubuntu 11.10"
date: 2011-11-29
forum: General Help
---

### Post by KrisDeniseRiley1 on 2011-11-29
So I am ready to finally get rid of windows 7. I have Windows 7 in the first partition, and would like some ideas for how to wipe it out. I understand how to use gparted, and my first thought was to just wipe out the partition that windows 7 was on. Then I started thinking that it would mess up the MBR so then I would have to run the live disk to get grub installed again. Help........any suggestions?

---

### Post by bsniadajewski on 2011-11-29
What do you want to do with the soon-to-be newly freed space then?

---

### Post by rng on 2011-11-29
I think using gparted to format windows partition will not mess up mbr, because grub would be installed there and its files must be on ubuntu partition.

---

### Post by KrisDeniseRiley1 on 2011-11-29
Im wanting to devote the rest of the space to just my Ubuntu host machine. I run ubuntu server from virtualbox inside of ubuntu 11.10. I just don't want to get too ahead of myself and screw something up. You have any suggestions for devoting my hdd to just my linux system?

---

### Post by rng on 2011-11-29
What are your partition sizes and how much extra space you want? You may simply shrink the windows partition (after defragmenting it from within windows) rather than removing it to get extra space.

---

### Post by KrisDeniseRiley1 on 2011-11-29
Windows 7--- /dev/sda2 is 227 gigs with only 70 used

Ubuntu---/dev/sda3 is 66 gigs with only 23 used

I think that I would like to have about 150 - 200 gigs for Ubuntu

---

### Post by rng on 2011-11-29
You can shrink any of the 2 partitions to make a third partition (ntfs would be the best) to keep you data (documents, pictures, videos, etc) so that if any system crashes, the data is safe on its own partition. Also keep your data backed up regularly because, sooner or later, systems do crash.

---

### Post by bsniadajewski on 2011-12-05
You could also reformat that Windows partition as a new /home partition.

---


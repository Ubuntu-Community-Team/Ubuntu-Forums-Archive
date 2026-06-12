---
title: "help installing multiple distros"
date: 2010-01-19
forum: General Help
---

### Post by tpattgeek on 2010-01-19
I kinda new to Linux, and wanted to install multiple distros on one hd just to get some experience with them.  I'm wanting to try out different distros and DE's, so I think I'm settled on wanting to install Ubuntu, Mandriva (or PCLOS), opensuse, and Linux Mint, all on a 40GB drive, giving a little more than 10GB to one of them to use as my primary Linux OS.  I also have a current XP install on another hard drive that I'd want to leave connected so GRUB will detect it (not touching it at all during OS installs).

After trying several times to get 4 (or even 3) OS' installed on one drive using one GRUB has been a pain, so it looks like I'll have to put each OS' GRUB on it's respective partition and use one OS' GRUB as a primary in the MBR.  With all that being said:

1. any suggestions on the best GRUB to use?  Much difference between Ubuntu 9.10's and Mint 8's?

2. I'm not worried about saving data on a separate /home partition, so could I use one swap partition and a / root for each OS (giving each one about 10GB)?  Would that just mean resizing the previous install's partition and manually creating a 10GB / ?

3. I've read the GRUB 2 guide several times, and when manually adding all of the GRUB's in different partitions to the "main" GRUB, all I need to enter is the title, root entry, and possibly chainloader +1??  This is the area I need the most help in... manually adding entries to GRUB 2... not too worried about Windows because that's usually detected, just adding other distros.


Thank you so much!

---


---
title: "dual boot raid 0 windows pro, kubuntu 9.04, with media partition"
date: 2009-09-08
forum: General Help
---

### Post by linux newb on 2009-09-08
Hi all, after countless hours of pissing around and getting both windows and kubuntu8,10, and 9.04 to dual boot in raid 0, i finally got it. my idea is to have these two operating systems read from and write to an 800 gig media partition that used a fat32 file system on it. i attempted to install it as a fat 32 file system while installing windows, but it only gave me the options of an ntfs, and an ntfs quick format, once windows was installed i attempted again from inside the operating system, once again i could only format to ntfs, while i was edting the partition table from the live cd in 9.04 which is what i ended up getting to work in dual boot in raid 0) and it kept giving me back an error and sayin that it failed to format a fat32 system on the array, but when i did that it made a partition using the empty 800gigs and i can see it in gparted, but it says under filesystem: unknown, and when i right click on it, the option to format it is whited out. but i think it is mounted because there is also the unmount option that is whited out. the only things i can do with my media partition is manage the flags on it, and resize/move it, every other option is whited out. can someone help me please?

---

### Post by linux newb on 2009-09-08
well is there any way to do this through the konsole with fdisk, or is asking about this a lost cause? looking fer the answer sure is

---


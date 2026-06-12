---
title: "Error mounting external drives after 9.10"
date: 2009-11-19
forum: General Help
---

### Post by bobsharp on 2009-11-19
I have two External SATA drives connected to my Ubuntu computer through a Promise SATA300 TX2 card. These drives have been mounting fine for months but after I upgraded to 9.10 only one drive will mount consistently. When I run mount -a I get the following error message: mount: /dev/sdc1 already mounted or /fandfamily busy. However, if I unplug the drive from the esata and plug it back in with USB then rerun mount -a everything works fine (at least for a few days). The system has the same behavior however if I use USB vs. esata at boot. There has to be something that changed with the 9.10 upgrade. Any help you all can give is greatly appreciated.

---

### Post by ZhuaSD on 2009-11-25
This is not a 9.10 problem, this problem happens for many users, if you have a bunch of partitions or drives things can get messed up.

What you need to do is clear out the old mounting data and re-set. Do you have a Windows install from which you could re-set the mount data on the one drive? That might work.

I haven't quite figured out how to get everything working yet.

---

### Post by sedawk on 2009-11-25
If you get the "mounted and busy" error try this:

* Check if /dev/sdc1 is listed as mounted using
  "mount" or "df".

* If you try "sudo umount /fandfamily" you should also
  get a busy message (not not force the unmount!).

* You can use the tool "lsof" to find any processes
  that might be using /fandfamily and prevent you from
  mounting the drive.

* What file systems do you have on the disks (extX/fat32/ntfs)?

---

### Post by bobsharp on 2009-12-12
Thanks for the help.  The error message that I am getting now is: /dev/sdb1 already mount or /fandfamily busy.

---

### Post by bobsharp on 2009-12-12
The only partition on the drive is ext3

---

### Post by bobsharp on 2009-12-12
Sedawk, you were right .dev.sdb1 was being used by fsck.ext3.  How do I prevent this from happening at each boot?

---


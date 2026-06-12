---
title: "Finding the Grub Loader"
date: 2010-05-16
forum: General Help
---

### Post by jedibutler on 2010-05-16
I recently installed Ubuntu Linux (alongside Windows 7) and I found a couple of anomalies since I installed it.  First, my 1 TB USB Hard Drive capacity was cut down to around 500 GB.  Also, the Grub Loader is listing a Windows XP Home option even though it is not installed (although I'm using Microsoft Virtual PC with Windows XP Professional.  I think that the Grub Loader ended up getting installed on my USB Hard Drive because if I disconnect it, the computer won't load the Grub Loader (although I didn't ask for it to be installed there) but I can't seem to figure out exactly where it is.  Is there a way to move the Grub Loader back to the main drive somewhere.  Any advice?  Thanks!

---

### Post by clgy15 on 2010-05-17
So you have a 1TB external hard drive and you install Ubuntu on it? How many hardrives do you have?
 
First off, when you install Grub it dosent install everything you need to boot to the MBR. It only installs a reference point to the files needed to boot. So when you install Ubuntu 10.04 or any other linux, Grub installs a reference point into the MBR to the boot files IN the Ubuntu partition.
Now for the size thing,
Post a list of all your partitions and disks with sizes and we will see whats happening.

---


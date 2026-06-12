---
title: "Completely wipe hard drive and reinstall"
date: 2010-08-15
forum: General Help
---

### Post by soasertsus on 2010-08-15
So in essence, my drive has become a cluster**** of random partitions, multiple Ubuntu installs, and random windows systems. It's gotten so bad that on my entire 250gb system my main Ubuntu install only gets 40gb of memory. Could anybody give me a step by step  guide to do the following:

1. Completely wipe and departition my disc.
2. Install Ubuntu from a backup .tar file
3. Install a 40gb windows 7 partition

---

### Post by russnae on 2010-08-15
you have to be careful. you will make the drive unreadable for windows. I had the same problem. try to use gparted to repartion.

---

### Post by deserthowler on 2010-08-15
> **soasertsus said:**
> So in essence, my drive has become a cluster**** of random partitions, multiple Ubuntu installs, and random windows systems. It's gotten so bad that on my entire 250gb system my main Ubuntu install only gets 40gb of memory. Could anybody give me a step by step  guide to do the following:

1. Completely wipe and departition my disc.
2. Install Ubuntu from a backup .tar file
3. Install a 40gb windows 7 partition

1. Go to [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and read the instructions.  Then download a copy.

2. I have never done this.

3. Make a partition for Windows (probably at the beginning of the disk 40 GB).  Then make a data partition to store the data (160 GB) and format NTFS.  

This should get you started.

Earl

---


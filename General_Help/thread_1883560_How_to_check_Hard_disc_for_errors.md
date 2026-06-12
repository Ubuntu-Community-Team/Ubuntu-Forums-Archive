---
title: "How to check Hard disc for errors?"
date: 2011-11-19
forum: General Help
---

### Post by jsandhu on 2011-11-19
Hi,

I have been using ubuntu for 2 months now, I was a windows user before and occasionally I liked to run disc check for errors but I don't see any utility for it in ubuntu (I am using 11.04 btw), I googled it and all I could find was some command based solutions, isn't there a GUI Utility that can check my Hard Drive, All Partitons for errors?

Thanks

---

### Post by dandnsmith on 2011-11-19
The Windows check disk (chkdsk) basically checks filesystems (NTFS or FAT), but not really the disk itself.
You can do much the same thing with gparted - it has a facility for checking each partition/filesystem.

HTH

---

### Post by jsandhu on 2011-11-19
I couldn't find any option in gparted to check disc partitions for errors. sorry.

---

### Post by efflandt on 2011-11-19
Best us usually the utility from the drive manufacturer if you suspect something is wrong.  Seagate has SeaTools for Seagate and Maxtor drives and WD (wdc.com) has their diagnostic utility. Those can be run from Windows or bootable CD (iso image).

Linux automatically does fsck when it boots after a certain amount of time or number of boots to check its own filesystems.

Any drive reserves error sites to automatically transparently map in place of bad sectors, so if you actually start seeing bad sectors in any OS, that is a bad sign that the drive can only get worse (time for warranty replacement or retiring it).

---

### Post by jsandhu on 2011-11-19
ok, Thanks.

---

### Post by pretty_whistle on 2011-11-19
Even though it checks after however many reboots, there is a tool so you can check your disk in case you feel uneasy. It's  in System -> Administration -> Disk Utility. You can select your  disk and partition and check it by pressing the option 'Check  Filesystem'.

But to run this the disk cannot be mounted so you'd need to use a boot CD and run it from there.

---

### Post by dandnsmith on 2011-11-19
> **jsandhu said:**
> I couldn't find any option in gparted to check disc partitions for errors. sorry.

Curious - I just checked, to see if I was imagining things, and found that selecting a partition and right-buttoning on it will show a *check* option (which, however, is greyed out if the partition is marked as locked, which it is when mounted)

---

### Post by pretty_whistle on 2011-11-19
> **dandnsmith said:**
> Curious - I just checked, to see if I was imagining things, and found that selecting a partition and right-buttoning on it will show a *check* option (which, however, is greyed out if the partition is marked as locked, which it is when mounted)
You're right.  When the disk is mounted it's greyed out.

---


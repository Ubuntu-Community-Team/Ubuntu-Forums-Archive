---
title: "Disk space"
date: 2009-08-15
forum: General Help
---

### Post by lift_test on 2009-08-15
My laptop is dual boot approx 10 gig to Jaunty, 10 to W7 RC and the rest is data for use by both.  I'm running out of space on the W7 partition and need to shrink the data partition to increase the W7.  I added Gparted but when I run it all the options to resize etc are greyed out.  I know I have a CD that will boot into an earlier version of Parted but can't find it.  Do I need to find the CD or can I use the other version within Jaunty?

---

### Post by sigixv on 2009-08-15
did you unmount the partition before trying to change it ?

---

### Post by lift_test on 2009-08-15
> **sigixv said:**
> did you unmount the partition before trying to change it ?

No, sounds like that might be the answer I was looking for, I'll try it.

---

### Post by lift_test on 2009-08-15
Tried unmounting before opening Gparted, still doesn't work.

---

### Post by DaithiF on 2009-08-15
Hi,
if your laptops ubuntu partition is a single partition, then you won't be able to unmount it and run gparted, since of course gparted is on that partition and you can't run a command from an unmounted partition.

Hence the usual way to do this is to boot using a live CD and use gparted from there and use it to shrink the (unmounted) laptop partition.

---

### Post by lift_test on 2009-08-15
> **DaithiF said:**
> Hi,
if your laptops ubuntu partition is a single partition, then you won't be able to unmount it and run gparted, since of course gparted is on that partition and you can't run a command from an unmounted partition.

Hence the usual way to do this is to boot using a live CD and use gparted from there and use it to shrink the (unmounted) laptop partition.

Ubuntu is on it's own partition, I'm trying to resize the large NFTS partition that both OS's use for data.  I did unmount the partition but any disk changing options are still greyed out when that partitionis highlighted.

---

### Post by lswb on 2009-08-15
Sometimes if Windows is not shut down cleanly gparted and some other linux tools will have trouble accessing an NTFS partition later. Try starting windows, and running scandisk or checkdisk or whatever the windows tool is called for checking and repairing the disk. Running a full defrag on the NTFS partition from Windows is also a good idea.

---

### Post by yeeeev on 2009-08-15
Did you try the Gparted Live CD? [http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.5-2/gparted-live-0.4.5-2.iso/download](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.5-2/gparted-live-0.4.5-2.iso/download)

---


---
title: "System hangs on boot because of unmountable swap partition"
date: 2010-04-17
forum: General Help
---

### Post by Objekt on 2010-04-17
So my Ubuntu 9.10 install has been hanging on boot lately.  At first I thought it was a problem with the 2.6.31-20 kernel, because that is the default boot option in GRUB2.  It seemed things worked fine if I instead chose the 2.6.31-19 kernel, but I had that hang yesterday too.

I also had 2.6.31-20 boot just fine yesterday.  Once.  Next time I tried it - system hang.

What I mean by "hang" is, I would see the GRUB OS selection screen (I have 2 versions of Windows and 2 versions of Ubuntu on this machine), select the first choice (Ubuntu with the 2.6.31-20 kernel), see the "pulsating white Ubuntu logo" briefly, then a bunch of scrolling text, then...blank screen.  Then nothing.

I let it sit for a few minutes to a few hours when it did this, but nothing further happened.

Then yesterday, I decided to let it sit the whole time I was at work, approximately 9 hours.  I came home to a screen with the white Ubuntu logo and the following error message:
```
One or more of the mounts listed in /etc/fstab cannot yet be mounted: 
swap: waiting for UUID=3fba81a3-de14-4f56-9e7b-ace95d933a0e
/proc/bus/usb: waiting for none
Press ESC to enter a recovery shell.
```

I dutifully pressed ESC and got a basic CLI, but didn't know what to do.  I tried pressing CTRL+D to give mounting another try, but it didn't work the second or third time either.

So it looks like I have a disk partition that refuses to mount sometimes.

Gparted for some reason wouldn't tell me the UUIDs of swap partitions.  They also don't show up in /dev/disk/by-uuid.  Using the bootinfo script, I found out that 3fba81a3-de14-4f56-9e7b-ace95d933a0e is the 4 GB swap partition associated with my Ubuntu 9.10 install.

The disk that partition is on is rated "healthy" by Disk Utility, with only a few bad sectors.  The HDD is about 7 years old, so it's in remarkably good shape.

What could cause this swap partition to not mount during boot, and how do I fix it?

---

### Post by Objekt on 2010-04-20
I "solved" the problem by commenting out the line in fstab which mounted my swap partition.  Ubuntu now boots fine, with any kernel I care to use.

While Ubuntu (and Linux in general) can live without a swap file, this is an ugly solution and does not address the root of the problem.  I am unwilling to mark this thread "solved" until I find out what was really going on & fix it.

I don't understand how a swap partition can become unmountable.  Isn't swap essentially raw disk space, without a file system as such?  Certainly, fsck doesn't work on a swap partition.  I don't know that reformatting the swap partition would help matters.

FWIW, the disk (a Hitachi DeskStar 160 GB, SATA 1.5 Gb/s model) is fairly healthy.  It's around 5 years old, and so has a few bad sectors, but nothing to worry about according to Disk Manager.

---

### Post by oldfred on 2010-04-20
Did you do any partitioning edits or changes. Some changes may cause the UUID to change or if mounting using sdax= then changes to partitions may change the swap partitions number (x).

To see UUID
sudo blkid

and compare/copy UUID to 

gksudo gedit /etc/fstab

---

### Post by Objekt on 2010-04-20
No changes to the partition setup.  System just started hanging one day.  No idea why, except it apparently had a problem with the swap partition.

I've been running without the swap partition.  I just reformatted it, and now it has a different UUID.  I updated the UUID in fstab and uncommented the line mounting it.  I'm going to reboot & see whether the problem's fixed.

If not, I guess I'll go back to running without a swap partition.

update:
System booted succesfully several times since I reformatted the swap partition.  I now have a swap partition again.  Go figure.  I guess this one is solved.

---


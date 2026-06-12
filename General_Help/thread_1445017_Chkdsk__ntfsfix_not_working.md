---
title: "Chkdsk / ntfsfix not working"
date: 2010-04-02
forum: General Help
---

### Post by altjx on 2010-04-02
I have ntfs progs installed and I'm trying to run a chkdsk similar utility for my flash drive. I think it's going bad because when I was dragging driver files to it earlier for another PC, it was empty when i went on that computer, and showed empty when i plugged it back up to this machine

so i ran sudo fdisk -l to list the devices and it shows /dev/sdd1 as the flash drive. when I run ntfsfix /dev/sdd1, i get this
```
Refusing to operate on read-write mounted device /dev/sdd1.

```

---

### Post by dcstar on 2010-04-02
> **altjx said:**
> I have ntfs progs installed and I'm trying to run a chkdsk similar utility for my flash drive. I think it's going bad because when I was dragging driver files to it earlier for another PC, it was empty when i went on that computer, and showed empty when i plugged it back up to this machine

so i ran sudo fdisk -l to list the devices and it shows /dev/sdd1 as the flash drive. when I run ntfsfix /dev/sdd1, i get this
```
**Refusing to operate on** read-write **mounted device** /dev/sdd1.

```

You cannot do these things on mounted partitions - unmount it first.

---

### Post by altjx on 2010-04-02
> **dcstar said:**
> You cannot do these things on mounted partitions - unmount it first.

Unmounted, now it says 
```
Failed to determine whether /dev/sdd1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

```

---

### Post by dcstar on 2010-04-02
> **altjx said:**
> Unmounted, now it says 
```
Failed to determine whether /dev/sdd1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

```

Use the Partition Editor (gparted) to check it, it could well be a faulty USB drive now.

---

### Post by altjx on 2010-04-02
> **dcstar said:**
> Use the Partition Editor (gparted) to check it, it could well be a faulty USB drive now.

The "Check" feature is unavailable (greyed out) when I try to right click the partition on the USB drive

---

### Post by dcstar on 2010-04-02
> **altjx said:**
> The "Check" feature is unavailable (greyed out) when I try to right click the partition on the USB drive

Is it mounted?

---

### Post by altjx on 2010-04-02
> **dcstar said:**
> Is it mounted?

Yeah, if I unmount it, it doesn't show in GParted at all. I refreshed the devices and it goes to only show the internal hard drive

---

### Post by Mark Phelps on 2010-04-02
Unfortunately, despite common folklore to the contrary, ntfsfix is NOT a Linux version of chkdsk.  If you check their documentation, they even admit that themselves.

That's because while ntfsfix can fix SOME NTFS errors, it can't fix all of them.

If it can't fix your drive, you will have little choice other than to plug that drive into an MS Windows box and run "chkdsk" from there.

---

### Post by dcstar on 2010-04-03
> **altjx said:**
> Yeah, if I unmount it, it doesn't show in GParted at all. I refreshed the devices and it goes to only show the internal hard drive

Did you use gparted to unmount it?

---

### Post by colorprint on 2010-04-07
> **Mark Phelps said:**
> 
That's because while ntfsfix can fix SOME NTFS errors, it can't fix all of them.

ntfsfix not fixing any errors at all. It only marks the filesystem as 'dirty' (and when you will boot Windows after this, chkdsk will be running)
[http://linux-ntfs.org/doku.php?id=ntfsfix](http://linux-ntfs.org/doku.php?id=ntfsfix)

---

### Post by dragonfly41 on 2011-03-21
This is an old thread but I have a similar problem trying to fix an NTFS partition in which Windows Vista and Ubuntu 10.10 are installed in dual boot mode (wubi installation).

I can dual boot into Ubuntu o.k. (demo mode) but I can't boot all the way into Vista.   

I can only get so far in Vista in safe mode (loading drivers) before it hangs and then goes to the Grub dual boot menu.

Windows Vista
Ubuntu.

I thought I could try  ntfsfix on the bootable partition containing Windows Vista but I get this error ..

"refusing to operate on read-write mounted device /dev/sda3"

I can see from this thread that the partition has to be unmounted before running ntfsfix .. but surely this will stop Ubuntu (wubi) which is in that partition (shared with Windows).

How can I repair the MBR for that partition while I have Ubuntu running and unable to unmount the partition?

This is the tutorial I am following.

[http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)

My internal CD-RW device does not work so I'm trying to get a DOS bootable USB setup so I can transfer Vista installation files onto it and then repair Vista.   

I can't start with a Vista reinstallation at this stage since I have to go through an orderly migration from Windows apps to Ubuntu.   

Repair is my aim right now.

---


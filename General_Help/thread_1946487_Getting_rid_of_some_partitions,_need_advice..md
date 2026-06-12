---
title: "Getting rid of some partitions, need advice."
date: 2012-03-24
forum: General Help
---

### Post by Sarteck on 2012-03-24
Right, so here's my current partitioning scheme:

[IMG]http://i42.tinypic.com/12490f7.png[/IMG]

I want to get rid of the two NTFS Partitions entirely (/dev/sda1 and /dev/sda3).  The extended partition has my [x]Ubuntu on it, which I want to keep.



Do I have to make the Ubuntu a primary partition?  Do I have to do anything special so that it's recognized as the boot parition?  I have a SuperGrubDisk downloaded and about to be burnt, because I'm expecting there to be SOME kind of trouble in that area, but if you guys can tell me what to expect, that'll make things a lot easier. :)

---

### Post by cortman on 2012-03-24
You can go ahead and delete the two Windows partitions, and expand the existing Xubuntu partition to include the empty space. You don't need to change the Xubuntu partition at all.
To make sure your Xubuntu partition is bootable, right click the partition in GParted and select "Manage Flags". Check the "boot" flag.

---

### Post by Bucky Ball on 2012-03-24
+1. You need to make sure the Win partitions are unmounted to do this. If unsure, boot from the LiveCD, Try Ubuntu and do it with Gparted there. You will need to do it this way to extend the Xubuntu partition anyway so boot from the LiveCD and do it all at the same time.

Pretty straightforward ...

---

### Post by Sarteck on 2012-03-24
All righty then.  I'm deleting the twp NTFS partitions, resizing the extended partition and moving it left, then resizing the ext4 partition to have it fill the unused space.

It's got about 45 minutes left (out of 60) with the bulk of the time spent moving the ~80GB to the beginning of the disk (I guess, anyways).  When that's done, I'll set the extended partition (or is it the ext4 one inside the extended?) to bootable.

I'll write back when it's done.

---

### Post by Bucky Ball on 2012-03-24
Set the / partition (where the Ubuntu OS is; dev/sda5 in you Gparted screenshot) to bootable. I'm not sure that that is going to work, though, as Grub is probably installed on the Windows partition (first partition) so even if the Ubuntu partition is set to boot it has no bootloader. Doesn't matter; you can reinstall grub to / later.

---

### Post by Sarteck on 2012-03-24
Surprisingly enough, it seems that just setting it as boot worked fine.  There was some message about "keys" and "s for skip or M or manual", but I just skipped it and everything started fine.

I the realized it was because I had manually mounted one of the NTFS partitions in /etc/fstab, so I went and commented that line out, rebooted, and everything went hunky-dory.




Weird, I was so sure I'd have a bunch of boot problems, lol.

---

### Post by Bucky Ball on 2012-03-25
Excellent news! Please mark thread as 'Solved' from 'Thread Tools at top right. ;)

---


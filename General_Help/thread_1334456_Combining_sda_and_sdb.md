---
title: "Combining sda and sdb"
date: 2009-11-22
forum: General Help
---

### Post by Garofoli on 2009-11-22
Hey guys,
I have two separate 300gb hard drives inside my laptop and I'm hoping to be able to combine them to the point where my computer recognizes it as only one hard drive. I'm trying to use gparted but it recognizes my /dev/sda and /dev/sdb/ as two separate devices and I'm stumped as how to combine them. Any help would be greatly appreciated. Thank you!

---

### Post by jalm111 on 2009-11-22
> **Garofoli said:**
> Hey guys,
I have two separate 300gb hard drives inside my laptop and I'm hoping to be able to combine them to the point where my computer recognizes it as only one hard drive. I'm trying to use gparted but it recognizes my /dev/sda and /dev/sdb/ as two separate devices and I'm stumped as how to combine them. Any help would be greatly appreciated. Thank you!

You need a raid solution.  I'd suggest not doing this as I've had nothing but problems trying to get mine running... still booting off the CD since grub has no clue how to install itself with the raid array enabled.

---

### Post by Cheesemill on 2009-11-22
You could use LVM, but this would require you to reinstall your system.

---

### Post by Garofoli on 2009-11-22
> **jalm111 said:**
> You need a raid solution.  I'd suggest not doing this as I've had nothing but problems trying to get mine running... still booting off the CD since grub has no clue how to install itself with the raid array enabled.

Could you explain how I could do this? I'll do anything but reinstall the operating system. Thank you.

---

### Post by ibuclaw on 2009-11-22
> **Garofoli said:**
> Could you explain how I could do this? I'll do anything but reinstall the operating system. Thank you.

Firstly, you'll need the Alternative CD so setup any advanced partitioning.

But before we digress:
1) Have you backed up your data?
2) Have you a contingency plan? Or a restore/recover procedure in place should one of the disks fail?

LVM may be nice, but there is no backup feature.
RAID may be nice also, but it is no backup facility either.

---

### Post by Garofoli on 2009-11-22
> **tinivole said:**
> Firstly, you'll need the Alternative CD so setup any advanced partitioning.

But before we digress:
1) Have you backed up your data?
2) Have you a contingency plan? Or a restore/recover procedure in place should one of the disks fail?

LVM may be nice, but there is no backup feature.
RAID may be nice also, but it is no backup facility either.

I have all my data backed up, but it would simply be an inconvenience to reinstall it. I have Ubuntu and Windows 7 disks to reinstall if it does go haywire, so I'm set. Thank you.

---


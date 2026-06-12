---
title: "Dualbooting - which partition should have &quot;boot&quot; flag?"
date: 2009-11-14
forum: General Help
---

### Post by Br3nn4n on 2009-11-14
I'll try to keep this simple. Go ahead and slap me, but my CD drive for this laptop is just BARELY dead enough that it won't read a CD, so I can't use Gparted except while the computer is running off the HDD (which isn't a very viable idea right?)

So I got this floppy disc called PUAD which is supposed to be a boot disc...but doesn't for some reason. But I can still access it through doing CTRL+ALT+F1 and typing "parted", which loads parted from the floppy drive.

My partition table looks like so:

```
(parted) p
Model: ATA TOSHIBA MK2018GA (scsi)
Disk /dev/sda: 20.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  10.0GB  10.0GB  primary   ntfs         boot
 2      10.0GB  20.0GB  10.0GB  extended
 5      10.0GB  19.7GB  9689MB  logical   ext3
 6      19.7GB  20.0GB  313MB   logical   linux-swap

```

So, obviously I have a 20GB HDD.

1 is a Windows XP install.
2 is Ubuntu 9.04

When I boot I get GRUB and I have successfully set up a dualbooting system, but I want to rid of the Windows partition to make space for my beloved Ubuntu. :)

The Windows partition currently has the boot flag. ***If I delete it, will the computer not know what to do at boot?*** I was thinking I can just set the boot flag to #2 or #5 (sorry I'm still pretty damn new to this linux stuff.) I want to just have Ubuntu on there and resize the Ubuntu partition to use the whole drive.

What can I do / how do I do this? :popcorn: to whoever can help :D

---

### Post by mj10c on 2009-11-14
In my experiences messing with GRUB and dual booting I believe you don't need any partition marked as boot, but if you wanted to mark one then go ahead and mark the one that contains the boot files, i.e. the partition with /boot inside.

---

### Post by Br3nn4n on 2009-11-15
Alright, sounds good. How can I find which partition has the boot files?

I'm assuming it is the one with the boot flag (the Windows partition). Can I safely just delete that Windows partition to free up the space? (And should I then mark the Linux w/ the boot flag?)

Thanks for your help

---

### Post by mikewhatever on 2009-11-15
Run **sudo fdisk -l** and look for the boot star. In your case, it should be the first one, since it is the only primary partition on the drive. I don't think a logical partition can be marked as a boot partition.

---

### Post by mdurham on 2009-11-15
I believe the boot flag is a dos/windows concept and has nothing to do with Linux.

---


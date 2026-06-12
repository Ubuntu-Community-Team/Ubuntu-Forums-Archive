---
title: "Windows Will Not Boot (Grub)"
date: 2005-01-31
forum: General Help
---

### Post by carlc on 2005-01-31
Windows will not boot from Grub. When I chose it from the bootloader menu, it displays the first part of the grub entry and then stops.


Any help would be greatly appreciated!


Here is the windows entry in Grub:

title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Here is my partition table:

Disk /dev/hda: 40.9 GB, 40982151168 bytes
16 heads, 63 sectors/track, 79408 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       40641    20482843+   c  W95 FAT32 (LBA)
/dev/hda2           40642       78415    19038096   83  Linux
/dev/hda3           78416       79408      500472    f  W95 Ext'd (LBA)
/dev/hda5           78416       79408      500440+  82  Linux swap

Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2        7476    60042937+   f  W95 Ext'd (LBA)
/dev/hdc5               2        7476    60042906    b  W95 FAT32

---

### Post by carlc on 2005-01-31
I came accross this thread:

[http://ubuntuforums.org/showthread.php?t=13355](http://ubuntuforums.org/showthread.php?t=13355)

so I tried this command:

sudo sfdisk -d /dev/hda | sudo sfdisk --no-reread -H255 /dev/hda

and received this message:

Warning: HDIO_GETGEO says that there are 16 heads

Disk /dev/hda: 79408 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Warning: The partition table looks like it was made
  for C/H/S=*/16/63 (instead of 79408/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 516096 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+  40640-  40641-  20482843+   c  W95 FAT32 (LBA)
/dev/hda2      40641   78414   37774   19038096   83  Linux
/dev/hda3      78415   79407     993     500472    f  W95 Ext'd (LBA)
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5      78415+  79407     993-    500440+  82  Linux swap
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/hda1   *        63  40965749   40965687   c  W95 FAT32 (LBA)
/dev/hda2      40966128  79042319   38076192  83  Linux
/dev/hda3      79042320  80043263    1000944   f  W95 Ext'd (LBA)
/dev/hda4             0         -          0   0  Empty
/dev/hda5      79042383  80043263    1000881  82  Linux swap
Warning: partition 2 does not start at a cylinder boundary

sfdisk: I don't like these partitions - nothing changed.
(If you really want this, use the --force option.)

 :confused: 

So, I left things as is, hoping to get some expert advice.


###I do not have a burning desire to boot windows except for being able to use winrar and dvdshrink!

---

### Post by carlc on 2005-01-31
Well, I found this thread:

[http://ubuntuforums.org/showthread.php?t=9099&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=9099&highlight=dual+boot)

With this advice:
> 
Sounds like the drive geometry issue has hit you. Was thought to be
fixed in Warty, but seems like it still shows up for some people for
some reason (me included). See
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1566](https://bugzilla.ubuntu.com/show_bug.cgi?id=1566) .

A long explanation of the cause and a fix is here:
[http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/) . While referencing Fedora, it applies to
Ubuntu as well. The core of the repair is here:

1) Try changing from AUTO to LBA mode in your BIOS for your hard drive.

2) Follow the instructions in the LWN article and use the sfdisk -d
/dev/hda | sfdisk --no-reread -H255 /dev/hda commands to reset the drive
geometry.

No promises that this is your problem, but if it is, one of the two
above should work.

HTH,

Bob

And it worked!  :)    

The sad part was that when windows booted it ran scandisk on my 2nd hd that I use to store mp3, etc., so who knows what damage was done there.?

---


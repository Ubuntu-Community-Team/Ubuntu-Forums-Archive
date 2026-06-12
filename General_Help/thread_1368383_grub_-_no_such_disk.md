---
title: "grub - no such disk"
date: 2009-12-30
forum: General Help
---

### Post by rennie21 on 2009-12-30
i posted this in another area, but it might be more appropriate here...

ok, so despite 2 years of linux I know next to nothing about how to troubleshoot problems... I went back to windows about a year and a half ago. I kept one of my old hard drives with ubuntu on it, but never actually used it for anything but transferring old files off of. I always intended to get the OS going again for blender rendering (dual booting was the goal). Well, I tried and failed miserably.

**Hard drives/OS, before:**

400 gb hard drive partitioned... (this is the primary hard drive)
100 gb partition ntfs (WINDOWS xp pro)
300 gb partition ntfs (no OS)

40 gb hard drive ext (Ubuntu 8 )

40 gb hard drive FAT (no OS)

I downloaded the current version of Ubuntu, 64bit yesterday (I have a core 2 quad). I ran the install and chose to overwrite the 40 gb hard drive that already had ubuntu installed on it. FYI, the boot loader from when I was using this hard drive, I assume was inactive or on one of my old disks, as it wasn't popping up when I started my computer. I used all of the default options when installing. Later I realize this chose (hd0) as the location for the boot loader, I assume grub2.

**So after install the hard drives/OS should have been:**

sda
400 gb hard drive partitioned... (this is the primary hard drive)
100 gb partition ntfs (WINDOWS)
300 gb partition ntfs (no OS)

sdb
40 gb hard drive ext (Ubuntu 9)

sdc
40 gb hard drive FAT (no OS)

**Upon restart, I got the error:**

GRUB loading.
error: no such disk
grub rescue>

I searched the forums to come up with a solution, but didn't really find anything I understood or that worked. I tried reinstalling choosing both sda and sdb as the location for the boot loader. Niether of these worked either.

**The existing setup of hard drives/OS is:**

sda
400 gb hard drive partitioned... (this is the primary hard drive)
100 gb partition ntfs (WINDOWS)
300 gb partition ntfs (no OS)

sdb
40 gb hard drive ext (Ubuntu 9)

sdc
40 gb hard drive FAT (no OS)

The last place I tried to install the boot loader was on sda.


typing "ls" after the "grub rescue>", i get:

(hd0), (hd0,2), (hd0,1)

trying to do "set root=(...)" for all the combinations I can think of: I either get "no such disk", "no such partition", or "unknown filesystem"


Also of note, when I go to the bios/startup boot menu, the only options are my 400gb hard drive or my cd drive. The other drives don't appear. Could it be something in my bios or the way I installed my hard drives? They mount ok from the livecd, so I assume not...


Any ideas what I should do?
Do I need to remove all of the grubs I've installed all over the place? I assume I put it in the wrong place initially, then in the right place, but the wrong place grub needs to be deleted, but then again, I'm a complete linux idiot...

Please help!! I can't start windows or ubuntu anymore, my computer is a footstool right now.

Thanks!

---

### Post by hal8000 on 2009-12-30
As you can boot from the live CD post the output of

sudo fdisk -l

Possibly what is missing is that no partition is marked as active.
This is not too important with grub as grub command makeactive can
change this but a partition needs to be active for windows to load.

With Grub 2, partitions start counting from 1, not 0 as in previous
grub (legacy) version. Its possible that grub has failed to auto-detect some of the partitions.

---

### Post by rennie21 on 2009-12-30
Here is the output...:

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f1bb5bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102406311    7  HPFS/NTFS
/dev/sda2           12750       48641   288302490    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000e41b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4865    39078081    b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

---

### Post by rennie21 on 2009-12-31
SOLVED

unfortunately, this was anticlimactic... I appreciate the vigor with which the community began to attack this problem, but:

The actual problem had nothing to do with Grub2, Grub legacy, ubuntu or my old and new installs.

My BIOS wasn't set to identify my other 2 hard drives. Once I set this Grub started right up.

LiveCD back on the shelf.

Thanks again for trying to help!

---

### Post by Llamano on 2009-12-31
Hello,

I am totally new to both Linux and Ubuntu and this is my first attempt to install it. Unfortunately I received an identical error message, but the solution is not as simple. Just a quick note to all, because I cannot boot into either XP or Ubuntu to access the net (livecd boot doesn't recognize my wireless drivers) ths entire post is done from my iPhone. 
Here is the posting from the sudo fdisk command mentioned earlier in this thread. Due to extreme typing limitations on my iPhone, it probably won't be frmatted the way it appears onscreen. 

(note: I have my internal 120gb drive, where windows is installed, and an external 1tb drive, where ubuntu and a whole bunch of my windows data resides)

disk /dev/sda: 120.0 gb, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
units=cylinders of 16065 *512 = 8225280 bytes
disk identifier: 0xe686f016

Device Boot.         Start.       End.    Blocks.    Id.   System
/dev/sda1           1.               6.          48163+.  de.    Dell Utility
/dev/sda2.   *.       7.             13725.  110197867+  7. HPFS/NTFS
/dev/sda3.            13727.      13987.   2096482+. f.  W95 Ext'd (lba)
/dev/sda4.            13988.      14593.   4867695.  db.   CP/M / CTOS / ...
/dev/sda5.             13727.      13987.  2096451.  dd.  Unknown

Disk /dev/sdb: 1000.2 gb, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x81611240

Device Boot.        Start.     End.     Blocks.        I'd.   System
/dev/sdb1.             1.        108777. 873751221.  7.    HPFS/NTFS
/dev/sdb2.          108778.  121601. 103008780. 5.   Extended
/dev/sdb5.         108778.    121074. 98775621.   83. Linux
/dev/sdb6.        121075.    121601.   4233096.   82. Linux swap/Solaris

there is the entire record of what is going on. I tried all the 'stub grub' or '$ grub' commands to type into the terminal followed by the find command that I have seen in other forums. The stub grub or $ grub commands don't work from booting from livecd or from the initial prompt that I get when my computer starts up, and the finds command universally fails from both these platforms as well. I'm really afraid that I will have to pop my ancienne XP Installation disk back in to restore my computer to a workable state. I'd really just rather fix this, without destroying the existing data on my external HD (the one where Linux was installed). 

Any help is seriously appreciated, but please remember I cannot copy and paste. This post took an insane amount of time to type.

---


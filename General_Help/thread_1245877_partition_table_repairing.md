---
title: "partition table repairing"
date: 2009-08-21
forum: General Help
---

### Post by neophyte_7 on 2009-08-21
I have been trying to add more space to my root partition because it is running ou of disk space......so I tried freeing some space from windows partition using gparted.....

Now here is the funny part...Gparted is displaying the entire HDD as a single unused partition and is not indicating individual linux and windows partitions....

The problem seems to that two partitions are beginning with same cylinder value:
I am giving output of fdisk -l here:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              10        1315    10485760    7  HPFS/NTFS
/dev/sda2   *        1315        9147    62914560    7  HPFS/NTFS
/dev/sda3            **9148**       19458    82815716    f  W95 Ext'd (LBA)
/dev/sda4   *     [COLOR=DarkOrange] 19131 [/COLOR]       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda5            **9148 **       9755     4883728+  83  Linux
/dev/sda6            9756       19130    75302912    7  HPFS/NTFS
/dev/sda7           [COLOR=DarkOrange]19131 [/COLOR]      19458     2620416   dd  Unknown


and the output of gparted from command line also seems to be fishy:

>gksudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
Can't have overlapping partitions.

---

### Post by neophyte_7 on 2009-08-21
Earlier I had a problem when I used to type fdisk -l, it had showed the partitions are not in order....with the help of some commands(I dont remember now..!! ) i had sorted it out....and changed some numbers near hda(0,4) in menu.lst to get the grub working again.....

So I think thatmight also be a cause of this problem.....I have linux and windows vista installed on the HDD...


thanks in advance for help, guys...!!

---


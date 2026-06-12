---
title: "Dual boot with Win 7"
date: 2009-08-01
forum: General Help
---

### Post by ndrake86 on 2009-08-01
ok so i went through the pain in the boot of trying to dual boot windows 7 and ubuntu 9.04
I set up my GRUB file as recomended for a dual boot (please keep reading at bottom rest of question there thank you very much for any help)

[I]t[B]itle        Windows 7, chainloader (on /dev/sdb1)
rootnoverify    (hd1,0)
makeactive
chainloader    +1

### BEGIN AUTOMAGIC KERNELS LIST


## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        64d2095b-9213-452c-b1bb-3b565769f314
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=64d2095b-9213-452c-b1bb-3b565769f314 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        64d2095b-9213-452c-b1bb-3b565769f314
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=64d2095b-9213-452c-b1bb-3b565769f314 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        64d2095b-9213-452c-b1bb-3b565769f314
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=64d2095b-9213-452c-b1bb-3b565769f314 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        64d2095b-9213-452c-b1bb-3b565769f314
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=64d2095b-9213-452c-b1bb-3b565769f314 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        64d2095b-9213-452c-b1bb-3b565769f314
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST[/B]
[/I]
** removed some extra data.
also when here is my fdsik -l

[I][B]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8423ee2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           2      121601   976752000    5  Extended
/dev/sda5               2      121601   976751968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x569ea82e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391    7  HPFS/NTFS
/dev/sdb2              14       30042   241207942+   7  HPFS/NTFS
/dev/sdb3           30043       60437   244147837+  83  Linux
/dev/sdb4           60438       60801     2923830    5  Extended
/dev/sdb5           60438       60801     2923798+  82  Linux swap / Solaris[/B][/I]


so here is where i am stuck I have the option to load win 7 and when I do it stalls, stuck saying "starting up..." and never does.  I have tried everything I could think of and could find in the forums and online but still to no avail.  Also also my partition for linux is (hd1,3) when starting up it says it starting from (hd0,2)  which is certainly not where ubuntu is as seen above from the fdsik -l, I wonder if this could be the collperate; does this mean I installed the Grub on the wrong hard drive ( i say this because on the fdisk there is a * uunder boot next to /dev/sda2 which would be (hd0,2).  I am new to this but thought that i did everything correct if anyone could help that would be amazing 

Nick

---

### Post by merlinus on 2009-08-01
What is the boot order of hdds in bios?  If sdb is first, then grub booting linux from (hd0,2) is correct -- first hdd in boot order, third partition.

And if that is the case, change this

[I]t[B]itle        Windows 7, chainloader (on /dev/sdb1)
[COLOR=Red]rootnoverify    (hd1,0)[/COLOR]
makeactive
chainloader    +1

to this

[/B][/I][I]t[B]itle        Windows 7, chainloader (on /dev/sdb1)
[COLOR=Red]rootnoverify    (hd0,0)[/COLOR]
makeactive
chainloader    +1[/B][/I]

---


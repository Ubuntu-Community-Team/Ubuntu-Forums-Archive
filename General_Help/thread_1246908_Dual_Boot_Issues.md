---
title: "Dual Boot Issues"
date: 2009-08-22
forum: General Help
---

### Post by aineo on 2009-08-22
I am running a dual boot setup with Windows XP and Ubuntu 7.04.  When I tried to boot my machine to Windows I received "Error 5: Partition Table is invalid or corrupt."  I am able to boot into Ubuntu successfully.  From Ubuntu, I ran  fdisk -l and received the following output:

_______________________________________________________________________
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2           24040       24321     2265165    f  W95 Ext'd (LBA)
/dev/sda3            3825       11473    61440592+  83  Linux
/dev/sda4           11474       24039   100936395    b  W95 FAT32
/dev/sda5           24040       24321     2265133+  82  Linux swap / Solaris

Partition table entries are not in disk order
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8355       21809   108066550    7  HPFS/NTFS
/dev/sdb2           13454       25063    93249292+   f  W95 Ext'd (LBA)
/dev/sdb3            8355       16710    67109888    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sdb4            8355       16710    67109888    0  Empty
Partition 4 does not end on cylinder boundary.
__________________________________________________________________________

Any ideas on what is going on here or how I can fix it?

---

### Post by P4man on 2009-08-22
Looks like basically your windows drive is hosed.
You can try testdisk to see if it can recover anything:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

if you got important data on that windows drive you want to save, I would advice you to make a byte copy of the drive with dd to an external drive first;  so that if you mess up with testdisk, at least you aren't making it worse.

---

### Post by aineo on 2009-08-22
Thanks for the reply.  Fortunately, there is nothing that cannot be replaced on that drive that has not been backed up recently.  Of course, there is always that data that isn't quite worth the trouble of backing up, but you still hate to lose it.

Now, off to read about testdisk.

---

### Post by prshah on 2009-08-22
> **aineo said:**
> 
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)
how I can fix it?

You can just load up fdisk, give it the single command "w" (which stands for write) and it will correct the invalid flag on your partition.

However, you _may_ lose data this way. Unlikely, but you do so at your own risk.

I cannot hazard a guess as to how this has occurred unless you have tried some kind of partition / backup restoration.

---

### Post by aineo on 2009-08-22
I plan on doing the fdisk with the flag w later, but that doesn't seem to be what is causing my issues with Windows, unless I am misreading this, which is entirely possible.  As I understand it (keep in mind, I am a complete and total novice), ubuntu is on the hda drive and XP is on the hdb drive.  The invalid flag seems to be on the hda drive.  Am I understanding that right, or am I missing something?

---

### Post by P4man on 2009-08-22
I misread.. but you seem to having issues on both disks.
The first one, sda has these errors:

> Partition table entries are not in disk order

But thats just a FYI, its not a real error.

> Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

This does indicate an error, but should be easy to solve (press W). And it relates to your swap partition

Then there is  sdb  drive:

> 
Device Boot Start End Blocks Id System
/dev/sdb1 * 8355 21809 108066550 7 HPFS/NTFS
/dev/sdb2 13454 25063 93249292+ f W95 Ext'd (LBA)
[B]/dev/sdb3 8355 16710 67109888 0 Empty
Partition 3 does not end on cylinder boundary.[/B]
[B]/dev/sdb4 8355 16710 67109888 0 Empty
Partition 4 does not end on cylinder boundary.[/B]

as well as the error grub gives you. 

What partition is windows installed on?

Your partitioning looks like an utter mess btw :)

---

### Post by aineo on 2009-08-22
Windows is installed on (I think) sdb1.  

I really don't use Ubuntu on this PC anymore, but I am thankful it is there now.  I have another machine, which I am now using, running Jaunty.  Not that any of that matters, but I really don't care if the Ubuntu partition on this computer works or not.

There is more to this story, as there always is.  For the last several months this PC has not given me the option to boot into Ubuntu, but has booted directly into XP.  Then this error started.  I don't really know why it stopped giving the option to boot into Ubuntu, and honestly I didn't care as I had Ubuntu on the other box.  I do find it odd that it is now giving me the option to boot back into Ubuntu.

Between the last time I shut used the computer (6 days ago) and the day I first tried to reboot it (2 days ago), nothing was deliberately changed.  In fact, I don't even really install much new software on the XP box as I am trying to fully migrate to Ubuntu.

That may be more information than anyone wants or needs, but I thought some of it may be helpful.  I am running testdisk right now and seeing if I can recover with it.

---

### Post by aineo on 2009-08-22
Well, I consider myself lucky.  Testdisk has fixed it where I can boot into XP.  Now I need to get serious about getting off of XP altogether.

---

### Post by jheaton5 on 2009-08-22
> **aineo said:**
> Well, I consider myself lucky.  Testdisk has fixed it where I can boot into XP.  Now I need to get serious about getting off of XP altogether.

I was in your position.  But unlike you I was not able to recover my windows install and had no system disk.  I went to Ubuntu/Debian dual boot cold turkey.  I'll never go back.

---


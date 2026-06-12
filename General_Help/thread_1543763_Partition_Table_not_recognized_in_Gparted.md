---
title: "Partition Table not recognized in Gparted"
date: 2010-08-01
forum: General Help
---

### Post by Zero7 on 2010-08-01
Here is the story. I upgraded Windows to 7 from Vista. My Acer laptop had a recovery partition with Vista on it. I don't know, what I was thinking, after the update I deleted the recovery partition. Then got in to problem that Partition Table is deleted. Recovered the partition and partition table with LiveUSB and gpart. 

So laptop was working again in about 30mins. Now I see the following issue.

Laptop boots and works fine both in Ubuntu (default OS) and Win7.
In Disk Utility the partitions are shown as in attachment.
In Gparted the disk is not recognized as partition table is not recognized (so I guess)
Output of fdisk is here for ref;
```
home@home-laptop:~$ sudo fdisk -l
[sudo] password for home: 
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: invalid flag 0x802f of partition table 7 will be corrected by w(rite)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x893c1445

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490412   83  Linux
/dev/sda2            1307        7707    51416028    7  HPFS/NTFS
/dev/sda3            7708       11650    31672117    f  W95 Ext'd (LBA)
/dev/sda4           11651       30401   150617407+   7  HPFS/NTFS
/dev/sda5            7708        9032    10643031   83  Linux
/dev/sda6            9033       11393    18964701   83  Linux
/dev/sda7   ?      152896      288579  1089878006   be  Solaris boot
home@home-laptop:~$ 

```

I would like to merge the sda1 with sda4 if possible. Also I lost SWAP partition. 
Will these issues cause any problem?

---

### Post by oldfred on 2010-08-01
You cannot merge sda1 with sda4 as they are not adjacent. You can just make it /data partition and put data into it.

this occasionally fixes issues and is worth trying, you just type the letters - x, f etc not the 'use option':
you do the following :
sudo fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

see this for more info:
man fdisk

---

### Post by Zero7 on 2010-08-01
Thanks Oldfred. I got the following output:
```
home@home-laptop:~$ sudo fdisk -l
[sudo] password for home: 
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x893c1445

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490412   83  Linux
/dev/sda2            1307        7707    51416028    7  HPFS/NTFS
/dev/sda3            7708       11650    31672117    f  W95 Ext'd (LBA)
/dev/sda4           11651       30401   150617407+   7  HPFS/NTFS
/dev/sda5            7708        9032    10643031   83  Linux
/dev/sda6            9033       11393    18964701   83  Linux
/dev/sda7   ?      152896      288579  1089878006   be  Solaris boot
home@home-laptop:~$ sudo fdisk /dev/sda
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.


Expert command (m for help): r

Command (m for help): p

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x893c1445

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490412   83  Linux
/dev/sda2            1307        7707    51416028    7  HPFS/NTFS
/dev/sda3            7708       11650    31672117    f  W95 Ext'd (LBA)
/dev/sda4           11651       30401   150617407+   7  HPFS/NTFS
/dev/sda5            7708        9032    10643031   83  Linux
/dev/sda6            9033       11393    18964701   83  Linux
/dev/sda7   ?      152896      288579  1089878006   be  Solaris boot

Command (m for help): v
Logical partition 7 not entirely in partition 3
Total allocated sectors 2664019175 greater than the maximum 488397168

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.

```

After reboot also, Gparted does not show the disk partitions and says that the disk is unallocated.
One basic doubt, do I have to run the above commands from LiveCD?

---

### Post by oldfred on 2010-08-02
Now I see your sda7 is totally outside the range of the sectors that the drive has.

Testdisk ususally then is the best tool. Do you really have a solaris boot or is it just mislabeled as well?

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by efflandt on 2010-08-02
It looks like somebody or something might have tried to set partition 7 based on sectors when units at the time were cylinders (was that swap?).  So its location and size are beyond the end of the disk (hence the errors).

So the first thing I would do is remove partition 7 and recreate it with default start at 11394 and default end (probably 11650) and proper type (82 for swap).

You should not try to alter partitions on a disk you are running from, which may have been why gparted refused to run.  So that would best be done from a live CD.  However, Vista or Win7 can shrink or grow (not move) their own partition using Computer Management on a running system and that is generally considered the safest way to shrink or expand partitions for those.

If you are going to be juggling partitions, it would be best to back up anything you do not want to lose.  And have printed instructions for restoring grub2 because it may not be able to find its other files if they move.

Moving partitions can take a long time (many hours), so you may want to do that overnight.  It is okay for the screen to go into standby, but make sure that Power Management settings do not put your computer to sleep.

---

### Post by Zero7 on 2010-08-02
Thak you Oldfred and efflandt.

I used testdisk and just followed the steps. Now the problem is resolved. Appreciate your help.

testdisk is amazing. So easy to use :)

---


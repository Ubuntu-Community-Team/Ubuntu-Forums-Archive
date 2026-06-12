---
title: "Gparted interruption! HELP HELP HELP"
date: 2009-11-09
forum: General Help
---

### Post by manij on 2009-11-09
Hi,

My son interrupted my gparted function before it finished the operations and now the I'm not able to boot from this partition!

All the data is there. I simply can't touch the drive with Gparted or qtparted

I'm guessing the MBR is fried. 

Is there any way to fix this? Help please help please!

Here is the sudo fdisk -l output from my install on the other drive. 

The drive with the problem, is sdb

Here is the sudo fdisk -l output
[B][I]
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x665aeff9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19452   156248158+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84788478

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5024    40355248+  83  Linux
/dev/sdb2            5025        5288     2120580   82  Linux swap / Solaris
/dev/sdb4            5289       14593    74742412+   b  W95 FAT32

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec260083

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    b  W95 FAT32[/I][/B]

Here is the sudo parted /dev/sdb print output

[B][I]Model: ATA WDC WD1200JD-00H (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  41.3GB  41.3GB  primary  ext3            boot
 2      41.3GB  43.5GB  2171MB  primary  linux-swap(v1)
 4      43.5GB  120GB   76.5GB  primary  fat32[/I][/B]

---

### Post by aquavitae on 2009-11-09
I think you forgot to add the fdisk output. What operations were you doing? If the problem is just the partition table, it might be possible to fix it manually, or to use a tool that scans the drive for filesystems.  I can't remember what the tools is called offhand though.

---

### Post by praveenthivari on 2009-11-09
I think u can copy the data using the live CD and then do the installation again giving ubuntu to use the entire drive. Once it is installed u can make partitions again.
May be it's crude way doing things but may help u. There may be better way though.

---

### Post by manij on 2009-11-09
> **aquavitae said:**
> I think you forgot to add the fdisk output. What operations were you doing? If the problem is just the partition table, it might be possible to fix it manually, or to use a tool that scans the drive for filesystems.  I can't remember what the tools is called offhand though.

I have the output for fdisk -l and parted also 

can you gimme some help?

---

### Post by Bjalf on 2009-11-09
Boot from Windows setup CD, choose Rescue mode, run fixmbr?
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Edit: Apparently it's not supposed to be used on systems with multiple operating systems.

---

### Post by Primefalcon on 2009-11-09
What **exactly** were you doing in the gparted operation, resizing a data partition or?

note: **don't fixmbr** if you want to keep ubuntu/grub

---

### Post by manij on 2009-11-09
> **Primefalcon said:**
> What **exactly** were you doing in the gparted operation, resizing a data partition or?

note: **don't fixmbr** if you want to keep ubuntu/grub

Yes I was resizing partitions!

---

### Post by Primefalcon on 2009-11-09
> **manij said:**
> Yes I was resizing partitions!
oh god, well use a live disk and see if your files are still there and back up what you can, but the odds are the partitions you were dealing with are damaged beyond repair.....

I'd advise to back up what you can and redo those partitions and reinstall, gparted can be a bad thing to stop

---

### Post by manij on 2009-11-09
> **Primefalcon said:**
> oh god, well use a live disk and see if your files are still there and back up what you can, but the odds are the partitions you were dealing with are damaged beyond repair.....

I'd advise to back up what you can and redo those partitions and reinstall, gparted can be a bad thing to stop

Good thing I backed up all the data before I started this and have partimage backups.

<SIGH>

---

### Post by Primefalcon on 2009-11-09
> **manij said:**
> Good thing I backed up all the data before I started this and have partimage backups.
<SIGH>
Well you have more common sense than I have most of the time in these matters then.... as my wife constantly atests

---

### Post by manij on 2009-11-09
> **Primefalcon said:**
> oh god, well use a live disk and see if your files are still there and back up what you can, but the odds are the partitions you were dealing with are damaged beyond repair.....

I'd advise to back up what you can and redo those partitions and reinstall, gparted can be a bad thing to stop

Is there anything I can do to rescue it? The info all seems to be there. I was doing changes to the FAT 32 partition


anything I can do B4 I I say screw it and start over with the partimage backup?

---

### Post by P4man on 2009-11-09
You could run [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). its in the repo;s and you can run it from a livecd session. But when you say you cant "touch it" with gparted, does that mean you cant see the partitions? Or just that they are locked?

---

### Post by manij on 2009-11-09
> **P4man said:**
> You could run [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). its in the repo;s and you can run it from a livecd session. But when you say you cant "touch it" with gparted, does that mean you cant see the partitions? Or just that they are locked?

I'm able to mount the partitions on my other install and transfer files. 

gparted was able to read the partitions when they were mounted. When I unmount them,  it keeps scanning the drive forever looking for the partitions

---

### Post by aquavitae on 2009-11-09
> **P4man said:**
> You could run [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). its in the repo;s and you can run it from a livecd session. But when you say you cant "touch it" with gparted, does that mean you cant see the partitions? Or just that they are locked?
I think testdisk is the tool I was thinking of.  There are two stages to resizing a partition - resizing the partition itself, and resizing the filesystem.  So it depends where it stopped.  If it was stopped while resizing the filesystem, I don't know what sort of state it will be in, but if it had was just resizing the partition then it should be easy to recover using testdisk.

---

### Post by artmendez on 2009-11-09
Using testdisk will surely help if the problem was that gparted was only interrupted.
You may want to do the operation as root.

It has worked for me.

Good luck!

saludos.

---

### Post by artmendez on 2009-11-09
Yep.. testdisk should help.

---

### Post by manij on 2009-11-10
It runed out I only messed up the FAT32 data partition which I had already backed up.

i simply deleted that partition and everything hunky dory

Thanks for you help!

---


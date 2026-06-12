---
title: "I screwed up a hard drive partition with ms-sys, how can I fix it?"
date: 2009-11-04
forum: General Help
---

### Post by magnificentbird on 2009-11-04
So - Windows XP crapped out on me a few days ago. I was unable to fix it or enter windows in any way so I installed Ubuntu to try and plug at it. The good news is, I really like it and I think I'm going to keep using it.

The bad news is, I'm inexperienced with it and probably did something really stupid. 

**I was fiddling with the program ms-sys to try and help my harddrive with Windows on it boot up so I could get that started again. I read in some forums as to how to set up the partition. **

This is what I did (I renamed the folder for ms-sys "ham" to make it easier to type): 

[INDENT]j@j-desktop:~/Desktop/ham$ sudo ms-sys --mbr /dev/sdb2
/dev/sdb2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record
j@j-desktop:~/Desktop/ham$ sudo ms-sys -f --mbr /dev/sdb2
Windows 2000/XP/2003 master boot record successfully written to /dev/sdb2
j@j-desktop:~/Desktop/ham$ 
[/INDENT]
Sdb2 is the partition of my big hard drive that had Windows on it. It also has a lot of files that I REALLY don't want to lose, and I am worried that I might have.

I think in doing a force write on the drive - I screwed up the partition because now I can't mount it in Ubuntu. 

First I tried to mount it :

[INDENT]j@j-desktop:~$ sudo mount /dev/sdb2
mount: can't find /dev/sdb2 in /etc/fstab or /etc/mtab

sudo mount /dev/sdb2 mnt/sdb2
mount: mount point mnt/sdb2 does not exist
[/INDENT]

I started Gnome Partition Editor to see what it looked like and it said this : 

[INDENT]/dev/sdb2 : size 462.40 gb, Flags: Boot Status: Not mounted 
First Sector : 96390, Last Sector : 969827984
total sectors: 969731595
Warning: Unable to detect file system! Possible reasons are : -the file system is damaged, The File system is unknown to GParted, There is no file system available
[/INDENT]
I did a : sudo fdisk -l, it says this:

[INDENT]Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6       48163+  de  Dell Utility
/dev/sdb2   *           7       60369   484865797+   7  HPFS/NTFS
/dev/sdb3           60371       60801     3462007+  db  CP/M / CTOS / ...

I also did a :  sudo fdisk /dev/sdb2

It says:
The number of cylinders for this disk is set to 60363.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
[/INDENT]
I went into expert command and typed v (verify the partition table)

[INDENT]Expert command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 2.
Partition 3 does not end on cylinder boundary.
Total allocated sectors 1701990412 greater than the maximum 969731595
[/INDENT]
Then I did an expert command : p (print the partition table)

[INDENT]Expert command (m for help): p

Disk /dev/sdb2: 255 heads, 63 sectors, 60363 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 63 111  45  368 101  51  371  218129509 1701990410 72
Partition 1 does not end on cylinder boundary.
 2 73 115  32   67 114  44  299  729050177  543974724 74
Partition 2 does not end on cylinder boundary.
 3 74 111  32  114 115  52  353  168653938          0 65
Partition 3 does not end on cylinder boundary.
 4 00   0   0    0   0   0    0 2692939776      51635 00
[/INDENT]

**Is there any help someone can give me to fix this partition? It booted fine into ubuntu until I screwed with it and ms-sys. I'd be very grateful as its got a lot of things on it I don't want to lose. **

Thanks a lot!

---

### Post by magnificentbird on 2009-11-04
One thing to add: In viewing the GParted file : There is an unallocated part to the HD of about 7.84 MiB

Its First Sector is : 969827985
Its Second Sector is : 969844049

I'm thinking it might be what was starting up from ms-sys.

---


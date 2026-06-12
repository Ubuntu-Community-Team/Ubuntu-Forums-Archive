---
title: "Installed new SSD, lost all partitions on HDD"
date: 2012-09-07
forum: General Help
---

### Post by OstensiblyFeet on 2012-09-07
Tonight I installed an SSD in my Ubuntu 12.04 machine with the intention of ultimately copying my installation to it, and hopefully having everything working that bit faster.

To do the installation I had to swap a few of the SATA cables around for various reasons, and after booting found that BIOS could no longer see my installation hard drive. I checked how secure all the cables were, and swapped some around again, and then managed to get BIOS to detect it, only to receive the "error: no such partition / grub rescue" prompt.

I booted from a live CD of Ubuntu and ran Gparted only to find my hard drive with my Ubuntu installation on (as well as a Linux Mint installation) is now displaying as having no partitions and is all unallocated space. It previously had at least two, it might have had some other empty ones.

I'm thinking this is a corrupt disk drive, although it seems bizarre I've had no issues until what appears to be a complete failure, and Gparted doesn't highlight bad sectors. It does however have a flag next to the "unallocated" space which says "Can't have a partition outside the disk!" - And it also says:

Last sector: 976773167
Totals sectors: 976773168

Are my partitions really gone or does anyone know if this is recoverable?

Thanks a lot in advance.

---

### Post by cryptotheslow on 2012-09-07
Did you actually commence the installation to the SSD at any point?

First step would be to put the SATA cables back the way they were before you started, leaving the SSD out of the mix for now. There's a very very slim chance it is some anomalous difference between the various SATA controllers that is causing a misreading of your partitions (unlikely).

Then boot up into the LiveCD and post back the results to these commands:
```

sudo parted -l /dev/sda
sudo fdisk -l

```

If you know your disk is something other than /dev/sda then use the relevant device in that command above.

---

### Post by OstensiblyFeet on 2012-09-08
Thanks a lot for the reply. No I didn't get to installing anything on the SSD. Although when I booted up with the Live CD and used departed to check on the HDD (and discovered it came up with no partitions and all unallocated space), I formatted the SSD to ext4 whilst I was there.

I don't know what the exact SATA configuration was before. To (hopefully) avoid confusion I've taken out the SSD and I've also disconnected the SATA cable from a PCI card I have which provides SATA/IDE expansion slots which I previously wasn't using.

I now have attached:

SATA 1: Operating system HDD (with Ubuntu, Linux Mint, swap partition but now reading as unallocated)

SATA 2: DVD Re-writer

SATA 3: Nothing

SATA 4 and 5: Storage HDDs, 1 TB each

I THINK I had the operating system HDD on SATA 1 before but I can't be certain. This configuration still shows the operating system HDD as having no partitions and all space unallocated. The code results are here:

```
ubuntu-studio@ubuntu-studio:~$ sudo parted -l /dev/sda
Error: Can't have a partition outside the disk!                      	 

Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End 	Size	Type 	File system  Flags
 1  	1049kB  1000GB  1000GB  primary  ext4


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End 	Size	Type  	File system  Flags
 4  	1049kB  1000GB  1000GB  extended
 5  	2097kB  1000GB  1000GB  logical   ntfs


Model: WD 20EADS External (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End 	Size	Type 	File system  Flags
 1  	1049kB  2000GB  2000GB  primary  ext4


Model: WD Ext HDD 1021 (scsi)
Disk /dev/sde: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End 	Size	Type 	File system  Flags
 1  	1049kB  2000GB  2000GB  primary  ext4


Model: Seagate FreeAgentDesktop (scsi)
Disk /dev/sdf: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End 	Size	Type 	File system  Flags
 1  	32.3kB  1000GB  1000GB  primary  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                      	 

Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdg: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos

Number  Start   End 	Size	Type 	File system  Flags
 1  	1049kB  3001GB  3001GB  primary


Model: BUFFALO External HDD (scsi)
Disk /dev/sdh: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End 	Size	Type 	File system  Flags
 1  	32.3kB  1000GB  1000GB  primary  ext4
```

```
ubuntu-studio@ubuntu-studio:~$ sudo fdisk -l
Warning: extra link pointer in partition table 5
omitting empty partition (6)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa989ee32

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sda1   *      	63	81915434	40957686   83  Linux
/dev/sda2    	81915435   245768191	81926378+  83  Linux
/dev/sda3   	245770238   976771071   365500417	5  Extended
/dev/sda5   	659034495   918179009   129572257+   5  Extended

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069fd9

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sdb1        	2048  1953523711   976760832   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x688fb999

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sdc4        	2048  1953523711   976760832	5  Extended
/dev/sdc5        	4096  1953523711   976759808	7  HPFS/NTFS/exFAT

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f5681

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sdd1        	2048  3907028991  1953513472   83  Linux

Disk /dev/sde: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ebe6

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sde1        	2048  3907024895  1953511424	7  HPFS/NTFS/exFAT
Note: sector size is 4096 (not 512)

Disk /dev/sdg: 3000.6 GB, 3000590401536 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566016 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00115253

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sdg1         	256   732566015  2930263040	7  HPFS/NTFS/exFAT

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c2a6

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sdh1          	63  1953520064   976760001   83  Linux

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4da84fa1

   Device Boot  	Start     	End  	Blocks   Id  System
/dev/sdf1          	63  1953520064   976760001   83  Linux


```

Note I am using an Ubuntu Studio Live CD because it was the closest to hand, but my main operating system is Ubuntu 12.04 - the one that has disappeared along with Linux Mint KDE 12 (although not so bothered about that).

Thank you so much for any help!

---

### Post by cryptotheslow on 2012-09-08
Well it looks like your installation is still there on /dev/sda but there is a problem with the partition table. That problem is what will be causing gParted to show nothing at all.

It should be possible to manually correct the partition table or possibly use Testdisk to do it (you can install it in your Studio Live CD with "sudo apt-get install testdisk"). There's a walkthrough here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I'm no expert in this area but there are others that frequent this forum who are and should be able to advise you better on how to proceed.

Whatever you do don't write to or re-partition that drive in the meantime.

---

### Post by oldfred on 2012-09-08
Testdisk may work, but let me suggest this first. Often fixes broken tables, where testdisk can restore  missing partitions or restore old ones  and sometimes the errors  may look the same.

If this will let you do anything on sda:
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by OstensiblyFeet on 2012-09-08
Awesome! You have no idea how happy I am to hear that.

I will try this in the next day or so. Hopefully I can fix this issue and I'll update this thread to Solved when appropriate.

Thanks again!

---

### Post by cryptotheslow on 2012-09-08
Go with oldfred's fixparts recommendation over mine, he's much more experienced in this stuff :)

---

### Post by OstensiblyFeet on 2013-01-17
So I forgot to update this thread, but anyway I did eventually fix the disk using fixparts, although I can't remember the specifics now. Thanks for all help. Updating this to Solved.

---


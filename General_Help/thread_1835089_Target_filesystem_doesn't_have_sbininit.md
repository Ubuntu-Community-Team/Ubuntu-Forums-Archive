---
title: "Target filesystem doesn't have /sbin/init"
date: 2011-08-28
forum: General Help
---

### Post by BloomingNutria on 2011-08-28
Hi Guys,

I am very new to Linux so please bear with me. I just installed an update to my Ubuntu 10.04, and upon restart the system will not boot. I get the following error when it tries to mount the file system: Target filesystem doesn't have /sbin/init.

I tried recovery mode on the grub and also a memory test with no success. So I booted from the live cd. 

fdisk -l returns the following:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e360d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      120378   966931456   83  Linux
/dev/sdb2          120378      121602     9828353    5  Extended
/dev/sdb5          120378      121602     9828352   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4f6c4f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris


I tried fsck, but it says this:

sudo fsckubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?


I have no idea what to do now. Can someone please help me?

Many thanks.

Oh, and I tried gparted too with the same result about the zero length partition. And I should also mention that this same thing happened to me a month ago when I lost power to my computer and tried to reboot, but that time gparted fixed it.

---

### Post by jerrrys on 2011-08-28
i think you should give testdisk a try.  to see if it can do a repair.  others have used it to a deeper extent, but i find that the auto mode has worked for me in the pass.  plus it takes about 30 seconds to give you the results.

now bad news...testdisk site is down right now, this is not the norm.

so here's my first attempt to post a file strolling screen shot of the site.

[ATTACH]201000[/ATTACH]

edit:  well, so much for the screenshot

---

### Post by BloomingNutria on 2011-08-28
I will try it when the site comes back up. Thanks.

---

### Post by jerrrys on 2011-08-28
try #2

>[IMG]zotero://attachment/639/testdisklogo_clear_100.png[/IMG]  TestDisk, Data Recovery
  [TestDisk]("http://www.cgsecurity.org/") is OpenSource software and is licensed under the terms of the [GNU Public License]("http://www.gnu.org/licenses/gpl.html") (GPL). 
**TestDisk** is a *powerful* free data recovery software! It was primarily designed to help **recover lost partitions** and/or **make non-booting disks bootable again** *when* these symptoms are caused by *faulty software*, certain types of *viruses* or *human error* (such as *accidentally* deleting a Partition Table). Partition table recovery using TestDisk is really easy. 
TestDisk can 
 
[LIST]
[*] Fix partition table, recover deleted partition
[*] Recover FAT32 boot sector from its backup
[*] Rebuild FAT12/FAT16/FAT32 boot sector
[*] Fix FAT tables
[*] Rebuild NTFS boot sector
[*] Recover NTFS boot sector from its backup
[*] Fix MFT using MFT mirror
[*] Locate ext2/ext3 Backup SuperBlock
[*] Undelete files from FAT, NTFS and ext2 filesystem
[*] Copy files from deleted FAT, NTFS and ext2/ext3 partitions.
[/LIST]
 TestDisk has features for both novices and experts. For those who  know little or nothing about data recovery techniques, TestDisk can be  used to collect detailed information about a non-booting drive which can  then be sent to a tech for further analysis. Those more familiar with  such procedures should find TestDisk a handy tool in performing onsite  recovery. 
 **  Operating systems **

 **TestDisk** can ***run*** under 
 
[LIST]
[*] DOS (either *real* or in a Windows 9x DOS-box),
[*] Windows (NT4, 2000, XP, 2003, Vista),
[*] Linux,
[*] FreeBSD, NetBSD, OpenBSD,
[*] SunOS and
[*] MacOS
[/LIST]
 Source files and precompiled binary executables are available for DOS, Win32, MacOSX and Linux from the [download]("http://www.cgsecurity.org/wiki/TestDisk_Download") page 
 **  Filesystems **

 TestDisk can **find lost partitions** for all of these file systems: 
 
[LIST]
[*]BeFS ( BeOS )
[*]BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
[*]CramFS, Compressed File System
[*]DOS/Windows FAT12, FAT16 and FAT32
[*]Windows exFAT
[*]HFS, HFS+ and HFSX, Hierarchical File System
[*]JFS, IBM's Journaled File System
[*]Linux ext2 and ext3
[*]Linux LUKS encrypted partition
[*]Linux RAID md 0.9/1.0/1.1/1.2
[LIST]
[*]RAID 1: mirroring
[*]RAID 4: striped array with parity device
[*]RAID 5: striped array with distributed parity information
[*]RAID 6: striped array with distributed dual redundancy information
[/LIST]
 
[*]Linux Swap (versions 1 and 2)
[*]LVM and LVM2, Linux Logical Volume Manager
[*]Mac partition map
[*]Novell Storage Services NSS
[*]NTFS ( Windows NT/2000/XP/2003/Vista/2008 )
[*]ReiserFS 3.5, 3.6 and 4
[*]Sun Solaris i386 disklabel
[*]Unix File System UFS and UFS2 (Sun/BSD/...)
[*]XFS, SGI's Journaled File System
[/LIST]
 **  Documentation **

 
[LIST]
[*] How to get TestDisk
[LIST]
[*] [Download]("http://www.cgsecurity.org/wiki/TestDisk_Download") - Binary executables and source files are available for DOS, Win32, MacOSX and Linux.
[*] [TestDisk compilation]("http://www.cgsecurity.org/wiki/TestDisk_Compilation")
[*] [TestDisk and Live rescue cd]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")
[/LIST]
 
[*] Working with special media
[LIST]
[*] [ Recover Damaged Hard Disks (bad sectors)]("http://www.cgsecurity.org/wiki/Damaged_Hard_Disk")
[*] [Disk image]("http://www.cgsecurity.org/wiki/Media_Image")
[*] [CD-R/CR-RW/DVD...]("http://www.cgsecurity.org/wiki/CDRW")
[/LIST]
 
[*] Using TestDisk
[LIST]
[*] [OS specific notes]("http://www.cgsecurity.org/wiki/OS_Notes")
[*] [TestDisk Step by Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") to recover lost partitions and repair damaged FAT/NTFS boot sector
[*] [Running the TestDisk Program ]("http://www.cgsecurity.org/wiki/Running_TestDisk")
[*] [ Undelete files and directory from FAT12, FAT16 and FAT32 filesystem]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT")
[*] [Undelete files from ext2 filesystem]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2")
[*] [Undelete files from NTFS partition]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS")
[*] [Recovery examples ]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples")
[*] [Scripted run]("http://www.cgsecurity.org/wiki/Scripted_run")
[*] [Support]("http://www.cgsecurity.org/wiki/Support")
[/LIST]
 
[*] [After using TestDisk ]("http://www.cgsecurity.org/wiki/After_using_TestDisk")
[*] Technical Notes
[LIST]
[*] [Intel Partition Table]("http://www.cgsecurity.org/wiki/Intel_Partition_Table")
[*] [Microsoft Fdisk]("http://www.cgsecurity.org/wiki/Microsoft_Fdisk")
[*] [SMART]("http://www.cgsecurity.org/wiki/SMART_Monitoring") monitoring
[*] Norton [GoBack]("http://www.cgsecurity.org/wiki/GoBack")
[*] [Current Limitations]("http://www.cgsecurity.org/wiki/Current_Limitations")
[/LIST]
 
[*] [How to help ]("http://www.cgsecurity.org/wiki/HowToHelp")
[*] [TestDisk & PhotoRec In The News]("http://www.cgsecurity.org/wiki/In_The_News")
[*] [TestDisk Team]("http://www.cgsecurity.org/wiki/TestDisk_Team")
[/LIST]
 To recover lost pictures or files from digital camera or harddisk, run the [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") command. 
  TestDisk home: [http://www.cgsecurity.org]("http://www.cgsecurity.org/").
Christophe GRENIER [EMAIL="grenier@cgsecurity.org"]grenier@cgsecurity.org[/EMAIL]
<

---

### Post by BloomingNutria on 2011-08-29
Wow, it actually fixed it. I was dubious at first, because I couldn't figure out how to get the filesystem utilities to work. For some reason it wasn't giving me the option for boot repair as it says it should here:[ http://www.cgsecurity.org/wiki/Running_TestDisk]("http://www.cgsecurity.org/wiki/Running_TestDisk"). The options just weren't there. I was about to post again asking you about the auto mode you mentioned (since I couldn't find anything about that either), but I thought I should try treating it as though it were a lost partition, even though it was not. It worked! Thank you!

---

### Post by jerrrys on 2011-08-30
its surprising what test disk will do, please mark your post as solved

---


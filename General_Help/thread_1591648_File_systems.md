---
title: "File systems"
date: 2010-10-09
forum: General Help
---

### Post by Tn91 on 2010-10-09
Thinking about running Ubuntu as my OS but trying to get a better understanding of how it works first. Could somebody kindly explain to me what it means by swap partititon and how ext3, ext4 and jfs actually work different NTFS FAT etc. 
Thx.

---

### Post by ubunterooster on 2010-10-09
A SWAP partition is used like RAM when there is not enough RAM, but is a lot slower. 

FAT
The FAT file system is relatively straightforward technically and is supported by virtually all existing [operating systems]("http://en.wikipedia.org/wiki/Operating_system") for [personal computers]("http://en.wikipedia.org/wiki/Personal_computer"). This makes it a useful format for [solid-state]("http://en.wikipedia.org/wiki/Solid-state_drive") [memory cards]("http://en.wikipedia.org/wiki/Memory_card") and a convenient way to share data between [operating systems]("http://en.wikipedia.org/wiki/Operating_system").


EXT3
Although its performance (speed) is less attractive than competing Linux filesystems such as [JFS]("http://en.wikipedia.org/wiki/JFS_%28file_system%29"), [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS") and [XFS]("http://en.wikipedia.org/wiki/XFS"), it has a significant advantage in that it allows in-place upgrades from the ext2 file system without having to [back up]("http://en.wikipedia.org/wiki/Backup") and restore data. Ext3 also uses less CPU power than ReiserFS and XFS.[[5]]("http://en.wikipedia.org/wiki/Ext3#cite_note-4") It is also considered safer than the other Linux file systems due to its relative simplicity and wider testing base.


EXT4 
It was born as a series of [backward compatible]("http://en.wikipedia.org/wiki/Backward_compatibility") extensions to ext3 meant to extend storage limits and add other performance improvements.[[1]]("http://en.wikipedia.org/wiki/Ext4#cite_note-Mathur-0") However, other [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") developers opposed accepting extensions to ext3 for stability reasons,[[2]]("http://en.wikipedia.org/wiki/Ext4#cite_note-1") and proposed to [fork]("http://en.wikipedia.org/wiki/Fork_%28software_development%29")  the source code of ext3, rename it as ext4, and do all the development  there, without affecting the current ext3 users. This proposal was  accepted, and on 28 June 2006, [Theodore Ts'o]("http://en.wikipedia.org/wiki/Theodore_Ts%27o"), the ext3 maintainer, announced the new plan of development for ext4

The ext4 filesystem can support volumes with sizes up to 1 [exabyte]("http://en.wikipedia.org/wiki/Exabyte") and files with sizes up to 16 terabytes[[8]]("http://en.wikipedia.org/wiki/Ext4#cite_note-7"). The current [e2fsprogs]("http://en.wikipedia.org/wiki/E2fsprogs") can only handle a filesystem of 16 [TB]("http://en.wikipedia.org/wiki/Tebibyte"),[[9]]("http://en.wikipedia.org/wiki/Ext4#cite_note-8") but support for larger drives is under development.


JFS
**Journaled File System** or **JFS** is a 64-bit [journaling filesystem]("http://en.wikipedia.org/wiki/Journaling_filesystem") created by [IBM]("http://en.wikipedia.org/wiki/International_Business_Machines"). It is available as free software under the terms of the [GNU General Public License]("http://en.wikipedia.org/wiki/GNU_General_Public_License") (GPL). There are versions for [AIX]("http://en.wikipedia.org/wiki/AIX_operating_system"), [eComStation]("http://en.wikipedia.org/wiki/EComStation"), [OS/2]("http://en.wikipedia.org/wiki/OS/2") and [Linux]("http://en.wikipedia.org/wiki/Linux") [operating systems]("http://en.wikipedia.org/wiki/Operating_system"). [HP-UX]("http://en.wikipedia.org/wiki/HP-UX") has another, different filesystem named JFS that is actually an OEM version of [Veritas Software]("http://en.wikipedia.org/wiki/Veritas_Software")'s [VxFS]("http://en.wikipedia.org/wiki/VxFS").

NTFS
 NTFS has several improvements over FAT and HPFS ([High Performance File System]("http://en.wikipedia.org/wiki/High_Performance_File_System")) such as improved support for [metadata]("http://en.wikipedia.org/wiki/Metadata_%28computing%29")  and the use of advanced data structures to improve performance,  reliability, and disk space utilization, plus additional extensions such  as security [access control lists]("http://en.wikipedia.org/wiki/Access_control_list") (ACL) and [file system journaling]("http://en.wikipedia.org/wiki/Journaling_file_system").

---

### Post by srs5694 on 2010-10-09
As a practical matter, Linux requires a Linux-native filesystem (currently meaning ext2fs, ext3fs, ext4fs, ReiserFS, XFS, JFS, or Btrfs) on which to store most of its system files and the users' home directories. Likewise, Windows requires a Windows-native filesystem (currently meaning NTFS, although in the past FAT was acceptable) for its boot partition. You can use NTFS, FAT, or (with appropriate drivers in Windows) ext2fs or ext3fs on a data-exchange partition for sharing files with both OSes in a dual-boot configuration.

The reason each OS requires its own native filesystem is that OSes are built with assumptions about the filesystems they use. For instance, Linux assumes that files have associated owners, groups, and Unix-style permissions. Linux native filesystems provide these features, but NTFS and FAT (among others) don't. Similarly, NTFS provides features that Windows needs but that Linux native filesystems don't provide.

---

### Post by nemilar on 2010-10-09
Windows doesn't use a swap partition by default, but it does have an equivalent concept of a page file, which is used for the same exact thing - moving contents from RAM to disk, in order to free up RAM for other use, or because there is simply not enough RAM to go around.  Of course, disk is significantly slower than RAM, so when you do "hit swap" (on Windows this is called a "page fault"), you see the performance hit.

Linux can be configured to use a swap file (the Windows default), and Windows can be configured to use a swap device (the Linux default).  The reason a device might be preferable is that whereas a file can become fragmented (and thus slow down access even more), a partition cannot.

---


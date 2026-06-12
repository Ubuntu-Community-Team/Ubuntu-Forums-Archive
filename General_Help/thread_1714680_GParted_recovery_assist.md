---
title: "GParted recovery assist"
date: 2011-03-25
forum: General Help
---

### Post by BobonD on 2011-03-25
I wish to clean up my fast running out of space system. Had one very large partition containing Ubuntu 9.04 files/information, then running Ubuntu 10.10, and made an attempt to repartition sda1 (above mentioned partition) using GParted. cleared all the data in SDA1 but the attempt extended into SDA2. Thus and so I began to reinstall, using an old ISO. Moved through the steps to where the partitions are re-established, stopped and thought I had better get some help, just maybe I have a way to recover the lost information.
  Currently typing on an XP (MSdose). Can someone assist?

  Hope there enough information. Thanks in advance.

Bob

---

### Post by garvinrick4 on 2011-03-25
Post a screenshot of gparted, take the screenshot in Applications/Accessories/screenshot
and use the paperclip to browse and uploade screenshot to Message box.

```
There is a package called testdisk that can be used: Post the screenshot and a
user adept in using testdisk will be along:
Package: testdisk                        
New: yes
State: not installed
Version: 6.11-2
Priority: optional
Section: universe/admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 4,735 k
Depends: e2fslibs (>= 1.41.0), libc6 (>= 2.11), libcomerr2 (>= 1.01), libjpeg62
         (>= 6b1), libncursesw5 (>= 5.7+20100313), libntfs10 (>= 2.0.0),
         libuuid1 (>= 2.16)
Description: Partition scanner and disk recovery tool
 TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
 It works with :
 * DOS/Windows FAT12, FAT16 and FAT32 
 * NTFS ( Windows NT/2K/XP ) 
 * Linux Ext2 and Ext3 
 * BeFS ( BeOS ) 
 * BSD disklabel ( FreeBSD/OpenBSD/NetBSD ) 
 * CramFS (Compressed File System) 
 * HFS and HFS+, Hierarchical File System 
 * JFS, IBM's Journaled File System 
 * Linux Raid 
 * Linux Swap (versions 1 and 2) 
 * LVM and LVM2, Linux Logical Volume Manager 
 * Netware NSS 
 * ReiserFS 3.5 and 3.6 
 * Sun Solaris i386 disklabel 
 * UFS and UFS2 (Sun/BSD/...) 
 * XFS, SGI's Journaled File System

```

---

### Post by deeroot on 2011-03-25
Having trouble "Extracting" TestDisk, into ./      ...  Must have dropped it somewhere other than "/". Just guessing and since I'm back to wireless now on the Ubuntu, how does Test Disk see the HD? Things are starting not to make sense.  ??

---

### Post by deeroot on 2011-03-25
This is what's not making sense to me. I've back on the Ubuntu computer, via a 9.04 ISO. Trying to Extract to the Home Directory,,, on the ISO, don't think so, can't burn to the DVD. Can't extract to the HD, because there isn't anyway to see the 10.10 Ubuntu I hope is still there.

  What is it I am not doing/understanding. Thanks

Confused, but still chugging along
\Bob

---

### Post by oldfred on 2011-03-25
Testdisk is in the repository. Just download from synaptic on the liveCD.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by garvinrick4 on 2011-03-25
> **deeroot said:**
> This is what's not making sense to me. I've back on the Ubuntu computer, via a 9.04 ISO. Trying to Extract to the Home Directory,,, on the ISO, don't think so, can't burn to the DVD. Can't extract to the HD, because there isn't anyway to see the 10.10 Ubuntu I hope is still there.

  What is it I am not doing/understanding. Thanks

Confused, but still chugging along
\Bob
Make sure universe repository like in previous post.
```
sudo apt-get install testdisk
```
```
sudo testdisk
```
follow instructions with arrows and enter key.

---

### Post by deeroot on 2011-03-25
Oldfred,

   Thanks, have the file "TestDisk" down. Will run and let you know. Appreciate your help.

Bob

---


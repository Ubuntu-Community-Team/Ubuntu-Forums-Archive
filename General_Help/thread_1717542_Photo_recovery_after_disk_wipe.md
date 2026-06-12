---
title: "Photo recovery after disk wipe"
date: 2011-03-30
forum: General Help
---

### Post by thelastprimate on 2011-03-30
I recently installed ubuntu and completely wiped the disk with windows and everythingelse on it and now it seems I forgot to save a few important photos.:(
If anyone could help instruct me on how I can recover those it would be greatly appreciated. Unfortunately, I am a beginner so laymans terms would be the best.:)
Thanks guys I'll love you forever

---

### Post by garvinrick4 on 2011-03-30
In ubuntu live cd (install cd using Try UBuntu)
install a package called testdisk:
```
sudo apt-get install testdisk
```
Below is package description:
```
Package: testdisk                        
New: yes
State: installed
Automatically installed: no
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
 .
 PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for following files and is able to undelete them :
 * Sun/NeXT audio data (.au) 
 * RIFF audio/video (.avi/.wav) 
 * BMP bitmap (.bmp) 
 * bzip2 compressed data (.bz2) 
 * Source code written in C (.c) 
 * Canon Raw picture (.crw) 
 * Canon catalog (.ctg) 
 * FAT subdirectory 
 * Microsoft Office Document (.doc) 
 * Nikon dsc (.dsc) 
 * HTML page (.html) 
 * JPEG picture (.jpg) 
 * MOV video (.mov) 
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3) 
 * Moving Picture Experts Group video (.mpg) 
 * Minolta Raw picture (.mrw) 
 * Olympus Raw Format picture (.orf) 
 * Portable Document Format (.pdf) 
 * Perl script (.pl) 
 * Portable Network Graphics (.png) 
 * Raw Fujifilm picture (.raf) 
 * Contax picture (.raw) 
 * Rollei picture (.rdc) 
 * Rich Text Format (.rtf) 
 * Shell script (.sh) 
 * Tar archive (.tar ) 
 * Tag Image File Format (.tiff) 
 * Microsoft ASF (.wma) 
 * Sigma/Foveon X3 raw picture (.x3f) 
 * zip archive (.zip)

rick@rick-HP:~$ 

```

---

### Post by Rubi1200 on 2011-03-30
Photorec, which comes bundled with Testdisk, should help:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Be aware though that it often recovers files but not with the original file name so you will need to sort them out afterwards.

---

### Post by thelastprimate on 2011-03-31
Forgive me for my ignorance, but could someone give me a walkthrough of how to install this testdisk.
I tried before I started this thread but do not understand

---

### Post by coffeecat on 2011-03-31
> **thelastprimate said:**
> Forgive me for my ignorance, but could someone give me a walkthrough of how to install this testdisk.

In Ubuntu? Simply open Ubuntu software centre or System > Admimistration > Synaptic and mark it for installation. The package manager will do the rest. Thereafter both testdisk itself (which you do not need for file recovery) and photorec are started from the terminal. If you look at Rubi1200's link, there is a link within it to "Photorec step by step", under the "Other topics" heading.

---


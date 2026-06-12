---
title: "Damaged Partition"
date: 2011-05-05
forum: General Help
---

### Post by blacksilvershewolf on 2011-05-05
How do I fix a damaged partition with ubuntu?
What happened was hubby was installing Ubuntu side by side with XP and the hard drive froze at last so he was forced to shut it down manually. He tried reformatting but it says the hard drive is damaged but when you go to Ubuntu it says theres no OS BUT XP works.

---

### Post by garvinrick4 on 2011-05-05
##With Ubuntu live Cd (using Try Ubuntu) with internet connection
you can download and install testdisk and give
it a go.
```
sudo apt-get install testdisk
```
```
sudo testdisk
```

##This is the package:
```
rick@rick-HP:~$ aptitude show testdisk
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


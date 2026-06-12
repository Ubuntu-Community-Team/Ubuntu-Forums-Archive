---
title: "Recover formatted partition, please help"
date: 2009-12-20
forum: General Help
---

### Post by eltama on 2009-12-20
Hi, I made a big mistake, I was trying to reinstall Windows 7 because it was giving me lots of errors and by mistake, instead of formatting the first partition, I formatted the second, where I have all the media I've been accumulating for years.
I realized immediately and I turned off the computer and started it using the Ubuntu live CD, hopping to be able to recover the data.

I had a look at [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"), but it's not very helpful because the problem is not just that the partition was deleted, but Windows created a new file system. I am starting to loose my faith :(

With gparted I can see the new partition, but that's not what I want. testdrive does not find any lost partition and gpart allows me to modify some parameters, but I don't think that it will help.

Is there any chance to recover the data or should I just hit myself hard and move on?

---

### Post by cholericfun on 2009-12-20
just to make you be patient:

there definatly is a way 

however its not something i can help you with.
i've seen threads with such issues here before though and they 
were solved more or less.

---

### Post by coffeecat on 2009-12-20
> **eltama said:**
>  testdrive does not find any lost partition

Do you mean testdisk? Testdisk is for recovering lost partitions, so you are right that it won't help when a new filesystem has been created. But it comes with photorec which will help in your situation - depending on the file types you want to recover. Here's the package info from Synaptic:

> TestDisk checks the partition and boot sectors of your disks.
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
 It searchs for
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
 * zip archive (.zip)I used it once when the Mandriva installer reformatted my NTFS data partition (my fault entirely). The main problem is that you will get thousands of files with obscure file names and you will have to sort through them and rename them yourself.

I have to log off now - late here - but if you search the forums and/or google you'll find howtos for using photorec.

Good luck!

---

### Post by Leppie on 2009-12-20
you can also try Hiren's boot cd, it has many handy recovery tools.

---

### Post by eltama on 2009-12-20
Thanks for the answers!
First of all, I meant testdisk.

I read other threads and already found out about PhotoRec and Hiren's Boot disc.

I will first try to recover what I care most with photorec and then try to recover the whole partition with the rescue disk.
But I will do it tomorrow, enough mistakes for one day ...

---

### Post by Leppie on 2009-12-20
you may want to create an image of the partition you want to recover. you can then see if you can recover stuff from the image, without damaging the actual partition.

---

### Post by eltama on 2009-12-21
I thought about creating a raw image but the partition is almost 700GB and I only have 300GB free on an external disk. I've been a bad guy this year, so Santa won't leave a new hard disk under the tree.

I left photorec running during the night and it completely filled the external drive, which I was expecting, but I wanted to see what it did.
The result is not very encouraging.

Since there is no partition table it recovers the files in completely random order and with auto-generated names. Organizing hundreds of GBs of photos, videos, music and documents from that mess is impossible.
What is more, most of the files it recovers are useless or broken (most videos do not work).

---

### Post by kilee on 2009-12-21
Photorec is the best, but ytry first to recover your partition with testdisk. If you write the partition again you'll see your hdd just the way it was.

You can use [http://partedmagic.com/](http://partedmagic.com/), a livecd that has all you need to recover the partition and the files.

Follow this tutorial STEP BY STEP

[http://www.broes.nl/2008/01/restore-an-apple-partition-map/comment-page-1/#comment-4985](http://www.broes.nl/2008/01/restore-an-apple-partition-map/comment-page-1/#comment-4985)

I recovered an hfs+ partition, but you can recover any partition.
This way you wont have to rename all your files (as with photorec)

Good luck!!

a

---

### Post by eltama on 2009-12-21
I don't think that testdisk can help me in this case because I don't have to recover the partition table, the table is fine. If I had just deleted the partition it would be easy to recover with testdisk (I've done it before), but I have formatted the partition, which means that the file table was overwritten.

testdisk has an option to "Fix MFT using MFT mirror" and "Rebuild BS" which could help, but they didn't in my case.

I am now running GetDataBack from Hiren's boot cd, but it will take more than 2 hours to scan the whole partition. I'll post my findings later.

Thanks for the comments, and of course any suggestion is welcomed. If I get my data back I promise to do a detailed HOWTO.

---

### Post by kilee on 2009-12-21
Sorry to hear that!

Good luck!

give a try the partedmagic cd.
PS if nothing works,it is christmas, ask Santa for your data!  ;)

---

### Post by eltama on 2009-12-21
I think I will recover my data!
After more than two hours of scan, GetDataBack recovered the original tree structure and I can copy the data somewhere else.

I have been moving my music collection for 2 hours now. There was only one error with a duplicate file, but it seems harmless because the duplicate was empty. I have not been able to test the integrity of the data yet, but all looks fine.

It will take really long to move all I want and I am running out of space, but I will manage. What matters is that I won't loose all my data.

---


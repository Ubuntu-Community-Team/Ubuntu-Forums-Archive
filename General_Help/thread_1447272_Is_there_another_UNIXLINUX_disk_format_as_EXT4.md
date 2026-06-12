---
title: "Is there another UNIX/LINUX disk format as EXT4?"
date: 2010-04-05
forum: General Help
---

### Post by frenchn00b on 2010-04-05
Hello,

I would like to use something else as EXT2/EXT3/EXT4 for my linux harddisk. 
Is there some big names that let the disk to be fixed if damaged during mounted ? Or what are the bsd alternatives?[http://en.wikipedia.org/wiki/List_of_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems)

---

### Post by frenchn00b on 2010-04-05
Why are we still using ext3 or ext4, since those filesystems are out of date, and better can be done, really. 


wikipedia:
 > Disadvantages
[edit] Delayed allocation and potential data loss

Delayed allocation poses some additional risk of data loss in cases where the system crashes before all of the data has been written to the disk. (Note that these allocation semantics, by design, can only corrupt the contents of files, and are thus unrelated to other implementation bugs that can result in corruption of filesystem metadata.[11])

The typical scenario in which this might occur is a program replacing the contents of a file without forcing a write to the disk with fsync. Problems can arise if the system crashes before the actual write occurs. In this situation, users of ext3 have come to expect that the disk will hold either the old version or the new version of the file following the crash. However, the ext4 code since Linux kernel version 2.6.28 will often clear the contents of the file before the crash, but never write the new version, thus losing the contents of the file entirely.

Altering this behavior by using fsync more often could lead to severe performance penalties on ext3 filesystems mounted with the data=ordered flag (the default on most Linux distributions). Given that both file systems will be in use for some time, this complicates matters enormously for end-user application developers. In response, Linux kernels 2.6.30 and newer detect the occurrence of these common cases and force these files to be allocated immediately. For a small cost in performance, this will significantly increase the chance that either version of the file will survive the crash. This new behavior is enabled by default, but can be disabled with the "noauto_da_alloc" mount option.[12]

The new patches have become part of the mainline kernel 2.6.30, but various distributions chose to backport them to 2.6.28 or 2.6.29. For instance Ubuntu made them part of the 2.6.28 kernel in version 9.04&#8212;Jaunty Jackalope.[13]
[edit] 

---

### Post by mikewhatever on 2010-04-05
Out of date, really? Would you like a new file system every other week?:)

---

### Post by frenchn00b on 2010-04-05
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

I think that JFS is more reliable than EXT4. IBM, one pay for those servers, and are quality. IBM have great servers, so JFS shall be a good bet, ought it isnt? :p

JFS = HIGHLY RELIABLE 
EXT4 = not reliable, but fast

---

### Post by chriswyatt on 2010-04-05
This is an old article, at a quick glance I can't see any mention of EXT4.

---

### Post by frenchn00b on 2010-04-05
The guy explains well the problem with linux and EXT3... so another mor e reliable filesystem ?


[http://bbs.archlinux.org/viewtopic.php?id=56019](http://bbs.archlinux.org/viewtopic.php?id=56019)
> Ditto. That's been my only real complaint against JFS--I hadn't found a working defragger. I'll check it out by manually doing dependencies, tonight. A more minor complaint being that I don't see any options to change the log size after formatting (my / is small, but has more than it needs for /, so maybe could use a bigger one).

So far (definitely more than 10 abrupt shutdowns due to wall power), recovery after bad shutdowns has been ideal. I've yet to lose, or find corrupted, files on my disks. I've had config files I was editing, and FF sessions, get rolled back. EXT3, even in journal mode, has caused loss of an entire partition (twice before in wirteback, so I got anal; but, then it did it with journaled mode!). fscking and testdidking only copies, even finding the alternate superblocks...only small amounts of files recovered. If I lose the ability to boot, or maybe fully login, but still have most of my data intact, easily accessible from a working computer, I'll manage. It will also allow me to stay cheap, and not get a UPS big_smile.

I intentionally have fairly slow drives, and have not noticed any FS performance differences between EXT2, EXT3, RFS, or JFS, as long as I use Deadline w/ JFS.

P.S. no file is currently above fidefrag's threshold, so *shrug*. I guess I'll just have to wait a few months to really see.
P.P.S. de-fragged several files on my backup drive, also JFS. Yay.

---

### Post by chriswyatt on 2010-04-05
I googled about and found this article, it only mentions boot performance though:

[http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/](http://izanbardprince.wordpress.com/2009/03/28/comparing-boot-performance-of-ext3-ext4-and-xfs-on-ubuntu-jaunty/)

Near the end of the article it also mentions JFS and ReiserFS.

There was a big Phoronix article which goes into more detail but I couldn't be bothered to look through it.

---

### Post by chriswyatt on 2010-04-05
Deleted.

---

### Post by mikewhatever on 2010-04-05
> **frenchn00b said:**
> [http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

I think that JFS is more reliable than EXT4. IBM, one pay for those servers, and are quality. IBM have great servers, so JFS shall be a good bet, ought it isnt? :p

JFS = HIGHLY RELIABLE 
EXT4 = not reliable, but fast

Great. Hope jfs is new enough for you.):P

---

### Post by capscrew on 2010-04-05
The Linux file system of the future is BtrFS.  See [**_here_**]("http://www.google.com/search?q=btrfs+file+system&btnG=Go!").

---

### Post by iponeverything on 2010-04-05
> **capscrew said:**
> The Linux file system of the future is BtrFS.  See [**_here_**]("http://www.google.com/search?q=btrfs+file+system&btnG=Go!").

Lots of cool features in BtrFS. I have been watching it for a while.

---

### Post by Zill on 2010-04-05
FWIW I have had problems in the past with Ext3 and its mysterious inodes and I never figured out what to do with those files in Lost & Found :-(

I changed my systems over to ReiserFS and have never regretted it.  It seems to be a rock-solid filesystem that tolerates power outages flawlessly.

It is a shame that development of ReiserFS seems to have halted for "legal reasons".  However, I will continue to use it as long as it is available.

As always, YMMV!

---


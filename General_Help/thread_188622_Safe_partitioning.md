---
title: "Safe partitioning?"
date: 2006-06-04
forum: General Help
---

### Post by sasherm13 on 2006-06-04
Is it possible to partition a drive without damaging the data?  What is the best Linux partitioning tool to use?

I currently have an ntfs drive and want to create a second partition on the drive using ext3 so that I can move the data from the ntfs partition to the ext3 partition and then reformat the ntfs part to ext3.  This way I can change my drive from ntfs to ext3 without having to burn everything to dvd.

---

### Post by taurus on 2006-06-04
Boot with the LiveCD and use gparted to resize your harddrive then.  Even though it's safe, ALWAYS backup your data just in case something might go wrong...  ;)

---

### Post by mannheim on 2006-06-04
There are other threads on this forum which suggest that the safest way to deal with ntfs is to use a tool in Windows, such as "Partition Magic" if you have access to a copy (it costs money).  Let Partition Magic resize your NTFS partition to make space for a new partition. Create a new partition using the tools in Windows XP. Then run the installer.

For examples of other peoples problems with the installer and parted, see [here]("http://ubuntuforums.org/showthread.php?t=186395"). I'm sure that Windows tools can mess up as well, however. So whatever you do, follow taurus's advice, and back up.

---

### Post by rcarring on 2006-06-04
Make sure that the version of Partition Magic is at least version 8.

---

### Post by aysiu on 2006-06-04
[QUOTE=sasherm13]Is it possible to partition a drive without damaging the data?[/quote] Yes, as long as there's unused space available for the new partition > What is the best Linux partitioning tool to use? [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142). I've found it's worth downloading PCLinuxOS just to have DiskDrake.

---

### Post by grsing on 2006-06-04
Partition Magic has worked well for me, too.

---

### Post by az on 2006-06-04
I did a poll a few months back and most people have less probelms using the linux partitioning tools.  Just use the installer - it is as safe as partitionnig can be.  No need to third-party tools.

Most people dual-boot with windows and most of those people just use the installer's partitioner without any problems.

---


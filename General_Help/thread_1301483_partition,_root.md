---
title: "partition, root?"
date: 2009-10-26
forum: General Help
---

### Post by Gorlist on 2009-10-26
Good day, quick question im slightly confused on. Ive got a second partition (ext4) for general use, though im finding I have to be root/sudo to be able to use it?

Secondly I was going to use a smaller FAT32 partition to share files between windows 7 and ubuntu, such as emails so they can be accessed from both systems using Thunderbird, however is their anything I should be watching out for.

Best Regards!

---

### Post by 7raTEYdCql on 2009-10-26
Weird that an entire partition is protected. Normally atleast /home/username should be open for user usage, without sudo interfering.

With regard to your second question, ext4 can access your windows folders easily without an issue. While installing ubuntu you do get an option to export your windows stuff to ubuntu(eg internet explorer, etc). This will enable you to sync a few applications on the two Operating systems.

---

### Post by mcduck on 2009-10-26
> **Gorlist said:**
> Good day, quick question im slightly confused on. Ive got a second partition (ext4) for general use, though im finding I have to be root/sudo to be able to use it?

Secondly I was going to use a smaller FAT32 partition to share files between windows 7 and ubuntu, such as emails so they can be accessed from both systems using Thunderbird, however is their anything I should be watching out for.

Best Regards!

Is the partition on an internal drive? How (and where) have you mounted it, or is it automounted?

The simplest solution is to just create a directory in that drive and change that directory's ownership to your user. Another way is to give the whole drive right ownership at mount time, by configuring that in /etc/fstab (in this case you'll also need to change the ownership of the mount point itself).

What comes to the FAT partition, there shouldn't be any problems. But keep in mind that FAT and NTFS don't support ownerships and permissions as they are handled in Unix/Linux systems, so you can't use those file systems for any system directory (or even your home). If you need to backup any files there and still keep their ownership & permissions instact you can compress the files into .tar.gz or .tar.bz2 format before moving to the FAT partition.

---

### Post by Gorlist on 2009-10-26
its automounted, right will edit fstab :) 

Ah, that maybe a problem then in regards to fat32 and lack of user permissions and what not. Previously I use to read/write directly to my ntfs windows install for Opera, however predominately now using ubuntu. 

May instead use ext3 for the format and try out something like:

[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

Thanks again,

---


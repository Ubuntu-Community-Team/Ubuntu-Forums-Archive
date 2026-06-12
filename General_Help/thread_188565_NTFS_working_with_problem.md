---
title: "NTFS working with problem"
date: 2006-06-04
forum: General Help
---

### Post by sasherm13 on 2006-06-04
Okay, I used Fuse to mount my NTFS hard drive and it worked great.  I can now read and write to my NTFS drive.  However, I have hit a snag.  I cannot seem to delete from the drive.  When I try to delete a file I get the error

"Error 'Generic error' while deleteing ...'

Does anyone know how to fix this?  Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1	/mnt/ntfs	ntfs-fuse	auto,gid=1001,umask=0007	0	0

---

### Post by OffHand on 2006-06-04
Writing to NTFS is still buggy and considered dangerous. 
It's very well possible you end up with corrupted data or data loss.

---

### Post by sasherm13 on 2006-06-04
Okay, it turns out that I can delete items, I just have to use shift+delete.  Meanwhile, I am going to try to backup my data and reformat the drive to ext3 to avoid any future problems.  How do access the partitioner in Dapper?  Is it possible to partition the drive withoutt destroying the data?

---

### Post by Azurlune on 2006-06-04
You can either use gparted, which is in the repos, or get the gparted live cd, which you can find at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) . the live cd is the latest version, plus, if you boot into it, you can mess around with your other, mounted drives if you wish.

---

### Post by OffHand on 2006-06-04
[QUOTE=sasherm13]Okay, it turns out that I can delete items, I just have to use shift+delete.  Meanwhile, I am going to try to backup my data and reformat the drive to ext3 to avoid any future problems.  How do access the partitioner in Dapper?  Is it possible to partition the drive withoutt destroying the data?[/QUOTE]
Formatting without losing all your data is not possible. I would make a back up either way.
Better be safe than sorry.

---

### Post by chameleon_789 on 2006-06-04
I don't think you can reformat a drive and keep the files (although I recall somehow doing it before, I think that was with fat32 to NTFS). 
You can resize a partition using the free space on the drive however, leaving you with an unformatted free space which you can format with any fs, and then copy the files you want over. Not sure how useful that is or if it applies to your situation but I thought I'd mention it anyway.

---

### Post by mlind on 2006-06-04
How stable is that fuse-ntfs anyway? I'd like to modify some id3 tags of my mp3's
on ntfs share, but I dunno if it's wise..

---


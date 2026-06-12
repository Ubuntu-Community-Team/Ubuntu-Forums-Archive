---
title: "Trouble growing Ubuntu partition"
date: 2010-08-18
forum: General Help
---

### Post by JohnReid on 2010-08-18
Hi,

I downloaded and created a live GPartEd CD so that I could shrink my Windows partition and grow my Ubuntu one. I managed the first part but when I try to grow my extended Ubuntu partition to the left, it complains about not being able to satisfy the constraints. There doesn't seem to be much more information in the error message than that. I make sure I had swapoff whilst trying this.

Here's the output of 'fdisk -l':
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2   *          18         279     2097152    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             279        6397    49149534+   7  HPFS/NTFS
/dev/sda4           13387       30401   136672987+   5  Extended
/dev/sda5           13387       29705   131082336   83  Linux
/dev/sda6           29706       30401     5590588+  82  Linux swap / Solaris

```

I'm on Ubuntu 9.10:
Linux john-dell 2.6.31-22-generic #61-Ubuntu SMP Wed Jul 28 02:02:56 UTC 2010 x86_64 GNU/Linux

Thanks for any help,
John.

---

### Post by oldfred on 2010-08-18
You cannot move partitions that are inside the extended outside of the extended. So all you have to do is move the extended partition first to include the unallocated then you can move the logical partition inside the extended.

I try not to move partitions left if at all possible. Be sure to have good backups and recognize it may take a long time as it has to copy & verify all data in the partition. I prefer to create a new partition and use it as /home or a /data and then link it into the linux partition. I have several 20-25GB root partitions for different versions of Ubuntu but link in the same data in all.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by JohnReid on 2010-08-18
> **oldfred said:**
> You cannot move partitions that are inside the extended outside of the extended. So all you have to do is move the extended partition first to include the unallocated then you can move the logical partition inside the extended.

I try not to move partitions left if at all possible. Be sure to have good backups and recognize it may take a long time as it has to copy & verify all data in the partition. I prefer to create a new partition and use it as /home or a /data and then link it into the linux partition. I have several 20-25GB root partitions for different versions of Ubuntu but link in the same data in all.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
If I understand you correctly I did try to do what you say. I had unallocated space in front of the extended partition. In GPartEd I did "move/resize" and tried to include the unallocated space into the extended partition. I was then going to add it to the logical partition inside the extended but GPartEd could not manage the first step.

---

### Post by oldfred on 2010-08-18
Unless it is not right next to the extended it should work. Did you swap off as gparted may use the swap partition and if it is in the extended then the entire extended is in use. (small lock symbol is in use).

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by JohnReid on 2010-08-24
The unallocated space is right next to the extended. Is this a problem?

The small lock symbol is not there. I put swapoff.

Any ideas?

---

### Post by oldfred on 2010-08-24
It sounds like it should work. If you want post a screenshot of gparted. Applications, accessories, take screenshot.

---

### Post by JohnReid on 2010-08-31
Where do I save a screenshot if I can't write to the disk? Where can I get more specific help? You have given me very general pointers to things related to my problem.

---

### Post by oldfred on 2010-08-31
Boot with the Ubuntu liveCD. (I do not remember id the gparted CD has screen shot as standard)

Start up gparted with System,  Administration Gparted

If you have more than one drive in upper right corner select your drive.

In applications, Accessories, Take Screenshot 

It will probably just save to desktop. Use Firefox and login here and in the edit panel above the message is a paperclip. Click on that and in the window find the screenshot and upload it.

---


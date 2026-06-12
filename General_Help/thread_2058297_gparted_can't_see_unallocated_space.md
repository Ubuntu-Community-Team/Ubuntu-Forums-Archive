---
title: "gparted can't see unallocated space?"
date: 2012-09-15
forum: General Help
---

### Post by webcomm on 2012-09-15
I am trying to set up dual boot w/ windows 7 and ubuntu.  I have windows 7 installed and ubuntu on a flash drive.  In the windows disk management tool, I see I have a 68 GB block of unallocated space and 39 GB RAW.  Do I install ubuntu in one of these locations?  

When I boot into ubuntu on my flash drive and open gparted (or run the installer), ubuntu can't see the unallocated space or RAW space.  Instead it sees a 618 GB ntfs partition that seems to lump togeter the RAW space, unallocated space and a 488 GB ntfs partition.  Please have a look at the attached images of the windows disk management tool and gparted and let me know what my next step might be.

Thanks

---

### Post by oldfred on 2012-09-15
You have converted to dynamic partitions which do not work with Linux.

Normally those that have converted back had just created the dynamic and there still was a one for one relationship from physical to logical. Not sure with all your partitions if it is even possible to convert back. 

Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

---

### Post by webcomm on 2012-09-16
Post 96 in the first link seems to have worked for me.  I now have basic partitions.  You can see in the attached gparted screenshot that I am deleting sda4 to create unallocated space.  I then want to use about 30 GB of that unallocated space to install ubuntu, and then use the rest of the space for storage (to be shared by windows and ubuntu).  When I create the 30 GB partition, should that be a primary or extended partition?  The [article I'm following]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") doesn't say.  Or should I first turn the entire unallocated space into an extended partition and then divide that into the ubuntu partition and storage partition?  Thanks

---

### Post by oldfred on 2012-09-16
Use all the unallocated as the extended partition. Then you can create as many logical partitions as you want or need.

What it does the error on sda1 say in gparted? Click or right click on the red circle exclamation point.

---

### Post by webcomm on 2012-09-17
Please see attached screenshot of the errors.  Thanks.

---

### Post by oldfred on 2012-09-17
Did you create sda1 & sda4 and they are not formatted? But sda4 should not be formatted, but an extended which gparted should then see.

You want the sda4 to be the extended partition, not a primary. As an extended then you can create logical partitions inside it.

---

### Post by webcomm on 2012-09-17
Thanks.  I don't think I created sda1, but to be honest I don't recall.  I started working on this a couple months back and then put it aside.  I don't know why I would have created sda1, if I did.  I figured it was something that came with the computer.

---


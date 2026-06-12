---
title: "Question: Samba &amp; local hard disk partitions"
date: 2006-03-08
forum: General Help
---

### Post by ras on 2006-03-08
Those who use multiple partitions and multiple operating systems, Windows and Ubuntu that is, know that to share files between the two OS's on the same computer, an option is to create a FAT32 partition for this purpose.  

My question is:
Can Samba be used to mount, read & write, a local, non-FAT partition, ie NTFS, on the same hard disk as the Linux OS?  In other words, can one access a NTFS partition via Samba & smbfs using Linux on the same hard disks as the Linux partitions in much the same way as one would do over a network?

Thanks.

ras

---

### Post by Prospero2006 on 2006-03-08
Well, it sounds to me like you have a dual boot computer.
In that case, I'd suggest  editing your /etc/fstab to mount the partition at boot. 

Pros

---


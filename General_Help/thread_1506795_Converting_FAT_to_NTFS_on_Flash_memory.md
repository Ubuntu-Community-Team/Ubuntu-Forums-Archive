---
title: "Converting FAT to NTFS on Flash memory"
date: 2010-06-10
forum: General Help
---

### Post by FredVanH on 2010-06-10
Hi.
1.  Will a flash memory converted to the NTFS file system from FAT work in UBUNTU 10.4
     (I know that, in general, NTFS is required for files larger than 4GB, which is why I want it;  and that it's a little slower)?
2.  What's the best (easiest) way to convert on an UBUNTU machine?
Thanks for any help,
Fred

---

### Post by dcstar on 2010-06-10
> **FredVanH said:**
> Hi.
1.  Will a flash memory converted to the NTFS file system from FAT work in UBUNTU 10.4
     (I know that, in general, NTFS is required for files larger than 4GB, which is why I want it;  and that it's a little slower)?
2.  What's the best (easiest) way to convert on an UBUNTU machine?
Thanks for any help,
Fred

Ubuntu will not convert this, use a Windows machine or wipe out the partition and create a fresh NTFS one using gparted.

---

### Post by Chronon on 2010-06-10
> **FredVanH said:**
> Hi.
1.  Will a flash memory converted to the NTFS file system from FAT work in UBUNTU 10.4
     (I know that, in general, NTFS is required for files larger than 4GB, which is why I want it;  and that it's a little slower)?
2.  What's the best (easiest) way to convert on an UBUNTU machine?
Thanks for any help,
Fred

You have other options too:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

You don't mention what you usage pattern will be, so I can't say more.

---

### Post by FredVanH on 2010-06-10
Thanks, DCStar & Chronon!  I'm using it for a truecrypt container which will be read mostly in Ubuntu but possibly some in Windows.   It looks like Gparted worked for the NTFS.  I got rejected later because I had picked "No file system" over ext2 & ext3 (I was looking for NTFS but I guess that's a different attribute).  Anyway, I started over and this time selected Ext2 and it's cranking out the truecrypt container as I speak.  Hoping for the best.
I appreciate your replies!
Thanks,
Fred

---


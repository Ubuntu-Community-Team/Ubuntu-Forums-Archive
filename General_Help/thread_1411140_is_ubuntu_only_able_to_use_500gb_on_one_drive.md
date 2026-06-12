---
title: "is ubuntu only able to use 500gb on one drive?"
date: 2010-02-19
forum: General Help
---

### Post by badperson on 2010-02-19
I installed 2 1tb drives, and used the 2nd drive as a samba share. When viewing the shared folder from windows and hitting "properties" it said the size of the drive was 500gb. Do i need to create another partition on the drive to be able to use it? 
bp

---

### Post by dcstar on 2010-02-20
> **badperson said:**
> I installed 2 1tb drives, and used the 2nd drive as a samba share. When viewing the shared folder from windows and hitting "properties" it said the size of the drive was 500gb. Do i need to create another partition on the drive to be able to use it? 


Without knowing all the details of what you formatted it as, we have no idea.

---

### Post by 3rdalbum on 2010-02-20
Ubuntu supports drives bigger than what you can fit into your computer. It certainly supports 1TB and 2TB hard drives.

It looks like your drive is actually 500 GiB, or that possibly you've partitioned it into only one 500 GiB partition.

What does Disk Utility tell you about the drive? (System > Administration > Disk Utility)

---

### Post by gspat on 2010-02-20
Windows has an annoying habit of only showing the disk space of the / partition under samba...

My 1TB drives always say 13.x GB free (or no free space is given)

This is due to the SMB spec as written by Microsoft.

---


---
title: "Partitioning hard-drive"
date: 2009-07-17
forum: General Help
---

### Post by user328 on 2009-07-17
Hey,

I want to install Windows 7 on my current machine, since I will be install ubuntu on another one. But looks like my hard drive needs NTFS partition which I currently do not have. So I have a 596.17 GB hard-drive that I want to turn into NTFS instead of using ext3. How can I change the format, or at least create a 500 GB partition, and then turn the other 96 GB into ntfs when I will get windows working?
Please describe me how to do it step by step, since i am really new to linux.
Thanks in advance

---

### Post by devosion on 2009-07-17
If you dont plan on installed anything else on the drive you may be better off formatting the drive to ntfs via the Windows 7 installer or a Ubuntu Live CD and gparted. But if you want to dual-boot at some point you should shrink you current installation, or start from scratch, and allocate one section of the drive to ext3, or your choice of file system for linux, and the other section to ntfs.

---

### Post by user328 on 2009-07-17
Windows 7 doesn't offer that. But I will see it on ubuntu cd.
Thanks

---


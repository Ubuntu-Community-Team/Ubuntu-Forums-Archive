---
title: "Ubuntu Live 10.04 files on USB into a folder?"
date: 2010-07-17
forum: General Help
---

### Post by Stache777 on 2010-07-17
Hi guys,

I'm new here, so please excuse me if I do something I shouldn't have.

I am currently running 32-bit Windows 7 Ultimate, with a VMWare 32-bit Windows XP virtual machine, and I know how to use both OS's fluently.

I have a 16 GB FAT32 USB drive which I use for document storage, to run portable applications, and to boot Ubuntu.

I recently installed Ubuntu 10.04 Live onto my USB with a 2 GB rw casper storage file. I would like to find a containment option where I can put all the Ubuntu system files currently exposed on my flash drive, into a folder, or a partition, where one click access to them is not available. When they are in this folder/partition I would still like to be able to boot from the USB.

I tried simple drag and drop of files/folders into a new folder within the USB drive, but I had a SYSLINUX error when I tried to boot from the USB. As soon as I removed the Ubuntu files from the folder I created, I was able to boot from the USB sans problems.

These files don't have to be encrypted or hidden, I would just like them to be in a folder or some other container where they are not accessible as soon as you open the USB drive.

Thank you all for your help....

Stache

---

### Post by dcstar on 2010-07-17
> **Stache777 said:**
> 
.........
These files don't have to be encrypted or hidden, I would just like them to be in a folder or some other container where they are not accessible as soon as you open the USB drive.

Thank you all for your help....

Stache

Use gparted to shrink the FAT partition on the USB to make room for a new partition (FAT or NTFS) that you can use for that purpose.

---

### Post by Stache777 on 2010-07-18
dcstar,

Thank you very much!

I will try this methhod and post back if my problem is solved.

Another quick question, I have an NTFS drive but I want a part of it formatted as FAT32. Will this program make it possible to do that?

Thanks,

Stache

---


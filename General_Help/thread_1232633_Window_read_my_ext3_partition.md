---
title: "Window read my ext3 partition"
date: 2009-08-05
forum: General Help
---

### Post by AquaFusion on 2009-08-05
I been trying to fins program that would read my primary OS, Ubuntu 8.10 with ext3 file system. I tired a few program like IFS drive, DiskInternal Linux Reader, explore2fs, they said the partition is there, and i can see it, but it wont list the file i had in ext3. I tired to double click my ext3 partition with those program, it just stuck at ext3, it showing blank partition but i know the files in that partition is really there because i recently check my Ubuntu to make sure it still there and it is. IFS drive designed for ext2, so i have to use other two program but still the same result.  A few thing you should know, im not sure if it really count. I had the Ubuntu 8.10 installed first, then Window XP installed second. So im not sure if maybe why the window programs like Linux Reader can see the partition but wont able to show me the file inside it?  I am hoping you can help me with this because there is some file i wish to transfer file from my ext3 to NTFS that wouldnt fit in my 2GB flash drive

---

### Post by merlinus on 2009-08-05
You can easily transfer files from linux to ntfs, but you will have to make sure the ntfs partition is mounted.

```
sudo fdisk -l
```will identify the partition.

---


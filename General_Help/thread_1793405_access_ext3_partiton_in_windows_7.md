---
title: "access ext3 partiton in windows 7"
date: 2011-06-29
forum: General Help
---

### Post by trnkumarchawla on 2011-06-29
I am currently using ubuntu 10.04,I want to access ext3 or any partition supported on linux in windows 7.
Is there any way,i want to use partition as any other drive in windows.

---

### Post by andrewthomas on 2011-06-29
If you want to be able to read and write data to a partition from linux and windows you are not going to be able to use ext. 

 Your best bet is to use a shared ntfs partition.

---

### Post by prodigy_ on 2011-06-29
> **andrewthomas said:**
> If you want to be able to read and write data to a partition from linux and windows you are not going to be able to use ext.
Now that's simply not true:
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

NTFS is a more common solution but it has its troubles as well. For example, it's easy to forget that NTFS itself doesn't enforce Windows filename restrictions. You may end up with what looks like a Windows native partition and yet has files not accessible from Windows.

---

### Post by oldfred on 2011-06-29
I always hesitate to write into another system's system partition with a reversed engineered driver. I prefer the shared data partition. 

I use NTFS since that driver was considered pretty good at the time I converted from FAT32 for my shared. You should set any system partition as read only to avoid issues.

---

### Post by amjjawad on 2011-06-29
If I were you, I wouldn't let Windows to mess around with any Linux Partition. Yes, there is a way but NO, I don't recommend it.

The best approach is to create a shared NTFS partition so that both OS's can access it.

---

### Post by Mark Phelps on 2011-06-29
> **trnkumarchawla said:**
> want to use partition as any other drive in windows.

Simply NOT possible.  While it's true that you CAN mount the partition and access it read/write -- it will not work "as any other drive in windows" because it will not handle permissions the same as an NTFS partition would.

As oldfred has already suggested, and my own experience has confirmed the hard way, it's best NOT to mess around with other filesystems.  

If you want to share data between Ubuntu and Windows, you would do better formatting a partition as NTFS.

---


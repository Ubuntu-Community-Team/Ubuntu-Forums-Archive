---
title: "How to increase the disk space or Merge two partitions"
date: 2011-07-09
forum: General Help
---

### Post by krishnik on 2011-07-09
Hi, 

I have 320 GB hard drive and i have alloted 10 GB for ubuntu. Now i want to increase the space. Because i have only 1.3 GB left. I have a partition which is formated into NTFS. I have some data in that partition. Can i move some space from this partition to ubuntu file system to increase the space?

Krishnik

---

### Post by rizzeh on 2011-07-09
Partitions can be resized using gparted tool. Before resizing, boot into windows and run windows disk defragmenter tool on partition you wish to resize. Also, do back up of all important files as resizing can go wrong. Once the disk is defragged and backed up, boot Ubuntu Live CD and use gparted to resize.
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by wildmanne39 on 2011-07-09
Hi, here is a guide on partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by krishnik on 2011-07-09
Thank you rizzeh. Thanks for the reply. I will try that.

---

### Post by krishnik on 2011-07-09
Thank you [wildmanne39]("http://ubuntuforums.org/member.php?u=508533"). Thats an excellent article.

---

### Post by wildmanne39 on 2011-07-09
> **krishnik said:**
> Thank you [wildmanne39]("http://ubuntuforums.org/member.php?u=508533"). Thats an excellent article.Hi, your welcome just be careful with partitions it only takes one little mistake to cause big problems.

---

### Post by Rayaz on 2011-07-09
And DO Backup;)

---


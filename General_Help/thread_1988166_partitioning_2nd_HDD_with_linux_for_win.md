---
title: "partitioning 2nd HDD with linux for win"
date: 2012-05-27
forum: General Help
---

### Post by flaafee on 2012-05-27
hey guys,

so, basically, i have a dual boot system. i have windows in my first hard drive and ubuntu in the second hard drive. unfortunately, i need more disk space for windows. i was thinking of cutting the ubuntu HDD in half since i barely have data in it.

im wondering if i can use gparted in ubuntu to split the HDD and in doing so, making the other half an NTFS partition. would windows recognize it if i partition it like that? or do i have to run a live CD/USB with gparted in it and do it from there?

i appreciate any suggestions :)

---

### Post by malakar.subhendu on 2012-05-27
i think it should be ok. gparted can do the job u are telling about.

---

### Post by wilee-nilee on 2012-05-27
Yes gparted will do it from a live cd, windows will see it, if a NTFS partition.

---

### Post by flaafee on 2012-05-27
so i have to use a gparted live CD/USB to partition the second hard drive? i cant just log in ubuntu and use gparted from there? just making sure.

---

### Post by oldfred on 2012-05-27
Your install of Ubuntu does not have gparted as you cannot use it on mounted partitions. You could install it and use it only on other drives.

So you have to use liveCD and probably have to swapoff also as swap may auto mount. LIveCDs like to find & use swap to speed things up.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by flaafee on 2012-05-27
well, right now i have gparted installed in ubuntu 12.04 but i will do the live CD as suggested. thank you for everyone's help. i appreciate it :D

---


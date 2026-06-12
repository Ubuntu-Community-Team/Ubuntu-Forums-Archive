---
title: "Windows not working"
date: 2010-03-05
forum: General Help
---

### Post by Kenta92 on 2010-03-05
I had a small partition of Ubuntu and a big one with Windows XP.
After some months i got friendly with ubuntu and wanted to resize the partitions (Ubuntu big, Windows small).
My disk was defragmented (like 0.1%), but after i resized the WIndows partition it is not working anymore.
I tried with the recovery CD but it made some problems with Grub, so i fixed it with the LiveCD and i can access Ubuntu now.
When i opened Gparted, i found this:

[http://img715.imageshack.us/img715/5008/immaginejg.jpg](http://img715.imageshack.us/img715/5008/immaginejg.jpg)

Windows is FAT16 (it was NTFS!) and it can't mount it (before trying to fix the MBR i could see the files inside). There's a weird label too.

So, what i am supposed to do now? The recovery CD of windows should help me, but i can't resize with Gparted and I need more free space for fixing with the utilities of the CD.

---


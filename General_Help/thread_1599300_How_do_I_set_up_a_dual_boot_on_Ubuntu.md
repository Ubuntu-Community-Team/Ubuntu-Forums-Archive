---
title: "How do I set up a dual boot on Ubuntu?"
date: 2010-10-17
forum: General Help
---

### Post by kroni_hunter on 2010-10-17
Most guides I find explain how to dual boot if you start with a Windows OS.  I actually installed Ubuntu first and now want to add Windows.  I'm very unfamiliar with Ubuntu which is why I want to have both OS while I make the transition.  I know I need to set up a partition but do not know how to do that.  Can anyone help me please?

---

### Post by fbobraga on 2010-10-17
this can help: [https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by ivarn on 2010-10-17
install windows and then you can use Auto Super Grub to update the grub list.
You'll find auto super grub on download.com.

---

### Post by kroni_hunter on 2010-10-17
So how do I set up the partition?  I tried reading the guide but I still don't get it.

EDIT:  I've got the Live CD loaded but nothing happens.  I can't unmount the partition because even though the disk in there I don't know how to get it to do anything.

---

### Post by ivarn on 2010-10-17
boot the win7 cd, start the installation and choose advanced when it asks you where you want your windows 7 installed, when the partition window pops up, click new.
Since you don't have a NTFS partition I think it will make one on its own if you don't add a new one manually.

---

### Post by kroni_hunter on 2010-10-17
I put in the Win7 CD but it will not start.  I tried clicking setup.exe and got an error

---

### Post by oldfred on 2010-10-17
Windows needs either a primary NTFS partition or free space and an available primary partition to install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)


Install CD/DVD not starting is a different issue. Are you rebooting with the CD drive set as first in boot order. Just trying to launch exe from CD will not work.

---


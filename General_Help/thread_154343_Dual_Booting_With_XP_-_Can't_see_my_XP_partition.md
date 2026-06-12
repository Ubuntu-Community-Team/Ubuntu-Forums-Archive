---
title: "Dual Booting With XP - Can't see my XP partition"
date: 2006-04-02
forum: General Help
---

### Post by Clayt0n on 2006-04-02
I just finished installing Ubuntu Linux and I can't figure out how to see the files on my  Windows partition. I can't see them when I go into "Places >> Computer" and I don't have any icons on the desktop that read "hd1" or anything like that. Please help ASAP. I would love to figure this out before bed. :) 

Grace and Peace,
Clayt0n

---

### Post by Felix21685 on 2006-04-02
hey clayton.. im a newb so please dont expect alot from me but i think i might know how to help you :)

here try this:
found at [http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

[Note] 	

Assuming that /dev/hda1 is the location of the Windows partition (NTFS) and the local mount folder is: /media/windows

   1.

      Read How do I check disk space and view the partition table?
   2.

      								sudo mkdir /media/windows 
      								sudo cp /etc/fstab /etc/fstab_backup 
      								sudo gedit /etc/fstab

   3.

      Append the following line at the end of file

      /dev/hda1 /media/windows ntfs umask=0222 0 0

   4.

      Save the edited file (sample/fstab_automountntfs)
   5.

      Read How do I remount /etc/fstab without rebooting?

make sure you use for example sda1 which was my sata drive instead of just sda..
thats why i couldnt get mine to work..after that it worked.

---

### Post by nanotube on 2006-04-02
yo felix, you got it about right.
ubuntu does not mount ntfs partitions by default, you have to do it yourself. and even when it does mount them, it can only safely read stuff, not write it. (but there are other drivers that can do the writing, after you fiddle around with it some more...)

---

### Post by Felix21685 on 2006-04-03
yeah i read that you can write to FAT partitions just not NTFS.

---

### Post by Sef on 2006-04-03
Windows and Linux can read and write to FAT 32 or ext 2.  NTFS is Microsoft's file system, and you know how much they like to share their technology with others.

---


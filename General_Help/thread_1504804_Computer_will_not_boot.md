---
title: "Computer will not boot"
date: 2010-06-08
forum: General Help
---

### Post by okayneil on 2010-06-08
So, yesterday I deleted a partition on my computer which did not have a file system on it, it was for music. This morning I woke up to an error, not a valid file system (or something like that) and gave me the grub rescue menu. 

I dual boot my machine with win 7 and ubuntu 10.4. Both partitions containing those file systems are still there. Im thinking its a grub problem?

Help would be awesome right now.

[IMG]http://i.imgur.com/Y3He8.png[/IMG]

---

### Post by elliotn on 2010-06-08
If u deteted grub then its better u reinstall grub

---

### Post by okayneil on 2010-06-08
> **elliotn said:**
> If u deteted grub then its better u reinstall grub

I have tried to but I cant, i keep getting weird warnings like error 15 file not found

---

### Post by Jahocolips on 2010-06-08
If you're using Grub 1

Boot from live CD go into your file system and check the menu.lst file and verify that grub is trying to boot from the right hard drive.

cd /boot/grub/

edit menu.lst and make sure boot: is the hard drive with your operating system.

Grub 2 is a bit more complex, might need advice from someone else.

edit: This is what you want... [http://ubuntuforums.org/showthread.php?t=1428476&page=1](http://ubuntuforums.org/showthread.php?t=1428476&page=1)

---

### Post by okayneil on 2010-06-08
Fixed it myself, thanks guys :)

---


---
title: "Dual-Boot Installation"
date: 2011-02-19
forum: General Help
---

### Post by cZal_Bu on 2011-02-19
I'm trying to dual boot Ubuntu 10.04 with Windows XP on my computer. I have 3 internal hard drives; C: (Windows) D: (Storage) and E: (Hopefully Ubuntu). I recently got a book for Christmas that talks all about the OS and it came with a CD that supposedly has the Ubuntu Install on it. I have tried to boot from the CD, but that does not work for some odd reason. And, yes, I did change the BIOS settings. I've tried downloading Ubuntu from the Internet but the download stops. Same thing happened when I tried to install from the CD. I don't understand why they would have an Install CD then make me download the OS anyways... :x I've tried a number of things, but if anyone could help me, it would be much appreciated!

---

### Post by dino99 on 2011-02-19
how to prepare your hdd:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

where to get ubuntu:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

when burning it, always choose the slowest speed

and more help following the links below

---

### Post by oldfred on 2011-02-19
dino's links are good.

Another with screen shots of the install process with tons of detail.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by IWantFroyo on 2011-02-19
Put the live cd in the drive, and press esc.
Use this guide to help you:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I recommend trying acpi=off on your live cd
If that works, type pci=noacpi while your selection is highlighted.

---

### Post by cZal_Bu on 2011-02-19
Okay, thanks for all the good help everybody! I'm still not entirely sure what I need to do, though. Do I really need to partition the drive even though it's empty? Can I just burn the .iso file to a CD using Nero Express then install it from there?

---

### Post by elfuego on 2011-02-19
Dont get scared - just follow the links provided and you will be fine. And to answer your question, yes, you do need to partition the drive even though its empty :-) Linux usually needs at least 2 partitions: root partition, marked as slash symbol '/', and swap area, which is usually ~2x your system RAM.

---


---
title: "Dual XP with preinstalled Ubuntu small Questions"
date: 2011-03-07
forum: General Help
---

### Post by sfm on 2011-03-07
I have been using Ubuntu for a couple of days. I want to install XP on the laptop also and have a dual boot.

I will>
1) back up everything (under "/") using Simple Back and back up MBR on separate hard drive
2) install XP
3) replace MBR since it will probably be not working for Ubuntu
4) be able to use Ubuntu or XP depending on what I choose via boot

Questions>
1) Am I forgetting anything?
2) Where can I find the MBR? 
3) If I back up everything in "/" will all my programmes still work? ie will MBR be most likely the only thing I need to replace after XP install?
4) Do I need to worry about grub/grub2 or is that have to do with MBR

Docs I will use:
Mbr#MBR Back-Up and Replacement [URL="https://help.ubuntu.com/community/DualBoot/Mbr#MBR%20Back-Up%20and%20Replacement"]https://help.ubuntu.com/community/DualBoot/Mbr#MBR%20Back-Up%20and%20Replacement
[/URL] 
Installing Windows After Ubuntu [URL="https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu"]https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu
[/URL] 
I will probably have more questions later.

---

### Post by b0b138 on 2011-03-07
Backing up the mbr isn't necessary. When you install xp, it will install its own bootloader, which can't boot linux. So yes, boot to a live cd and restore grub2 [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Don't forget to use gparted to create/resize a partition for windows, unless you already have one.

---

### Post by sfm on 2011-03-07
I tried to partition my internal drive where I would install xp and where I already have Ubuntu installed using gparted, but I must unmount the drive it tells me in order to partition it.
This is what it looks like>
[IMG]http://tinypic.com/r/1htuhf/7[/IMG] [http://tinypic.com/r/1htuhf/7](http://tinypic.com/r/1htuhf/7)

[IMG]http://i54.tinypic.com/1htuhf.png[/IMG]

Unmount whilst running in ubuntu? I don't think that sounds safe, but I do not know. Or should I run in Live CD (actually USB) and unmount from there? Then proceed to partition and install XP, fix grub2?
[IMG]http://tinypic.com/r/1htuhf/7[/IMG]

---

### Post by b0b138 on 2011-03-07
Yes, A partition must be unmouted to resize.

Yes, do it from the live usb.

Once there, you'll be able to go on there and just right click and select resize, and move it around or type the numbers in.

---


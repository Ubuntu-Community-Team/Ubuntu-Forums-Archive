---
title: "MAJOR HELP NEEDED! I REALLY FKd UP THIS TIME?!"
date: 2011-06-23
forum: General Help
---

### Post by ksaul on 2011-06-23
I was recently dual booting with Windows 7, and Ubuntu 10.04 and GRUB was my dual-boot menu.

Well just now I decided since I was no longer using ubuntu on this machine and had it installed on my other computer - that I would remove it from my windows machine. 

Well the way I went about removing ubuntu was through the `Computer Disks` manager in Windows 7 and I deleted the partition that was being used by Ubuntu. There was another partition I did not recognized that was 11gbs (NOT NTFS) and i deleted that aswell.

I rebooted - and now GRUB still tries to load, but it goes to a command prompt type screen that says 
```

GRUB Loading.
error: no such partition
grub rescue>
```
and Windows will no longer load, I do not even have the option to allow it to load.  I tried typing 'help' but it says its not a recognized command.

I tried to find my windows 7 disk but can not find it, I do have an ubuntu 9.04 disk if that will help - but what I am trying to do is just dedicate this to a windows computer.

PLEASE someone help me here, my computer is completely useless at this point and have a lot of valuables on the windows side of the machine =(

---

### Post by ubume2 on 2011-06-23
I read the other day, that there are rescue cd's that can be downloaded. Do a google search for Windows 7 rescue CD. But you would have to get access to a computer with an internet connection.

I've rescued my Windows XP years ago with the XP cd.  Command was something like fixmbr.


Don't know how much space you have on your HD, but that Ubuntu would be handy to have available when Windows breaks, even if you don't use Ubuntu.  A reinstall would also allow you to boot Windows.  8 gig for / and 1-2 gig for swap partition.

---

### Post by ksaul on 2011-06-23
> **ubume2 said:**
> I read the other day, that there are rescue cd's that can be downloaded. Do a google search for Windows 7 rescue CD. But you would have to get access to a computer with an internet connection.

I've rescued my Windows XP years ago with the XP cd.  Command was something like fixmbr.


Don't know how much space you have on your HD, but that Ubuntu would be handy to have available when Windows breaks, even if you don't use Ubuntu.  A reinstall would also allow you to boot Windows.  8 gig for / and 1-2 gig for swap partition.


yes i have tried using a windows vista disk to get access to a command prompt and doing fixmbr and fixboot but still not having any luck. if i cant get windows to load soon - i might just reinstall ubuntu and have it on the background... but id really like to dedicate this to windows only if possible

---

### Post by ksaul on 2011-06-23
is there a way to remove grub completely??

---

### Post by FrankenCub on 2011-06-24
I did the same thing on my old computer after building a dedicated Ubuntu box. I tried everything I could find to fix the MBR so my granddaughters could use XP for their games. I ended up sending the old computer to our local computer store to be repaired cause they have an excellent rep. They couldn't fix the MBR either. Ended up doing a fresh install of XP.

---

### Post by Rubi1200 on 2011-06-24
This link has information on how to run a startup repair for Windows 7:
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

I believe in most cases it needs to be run 3 times.

---

### Post by yetiman64 on 2011-06-24
> **ksaul said:**
> is there a way to remove grub completely??

In this circumstance you have removed grubs files on the Ubuntu install (whose partition you removed with the Windows 7 disk management tool), the only part of grub left is in the MBR of the drive. 

As has already been mentioned you need a Windows disk to do that **OR** follow this post from an Ubuntu live cd :- [[COLOR=Blue]http://ubuntuforums.org/showpost.php?p=7128133&postcount=4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7128133&postcount=4")  (this is using just the mbr code from the lilo boot loader to give access to Windows). Good luck.

---

### Post by cbowman57 on 2011-06-24
Dedicate a 10Gb partition to Ubuntu and re-install it, at least you can get back into Windows while you get it sorted out.

---


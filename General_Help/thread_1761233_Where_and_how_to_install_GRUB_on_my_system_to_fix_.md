---
title: "Where and how to install GRUB on my system to fix my DualBoot?"
date: 2011-05-17
forum: General Help
---

### Post by _1MoreDay_ on 2011-05-17
Hello,
   
  I was running Ubuntu 11.04 next to Windows 7 but lost my DualBoot after re-installing my Windows 7 using a backup image. The Ubuntu Partition (/dev/sdb5) is unchanged.
  Windows 7 comes with a default Bootmanager Partition (dev/sdb1) in size of 105MB.
   
   
  Here my system (2 Harddisks)
   
  **ubuntu@ubuntu:~$ sudo fdisk -l**
   
  Disk /dev/sda: 203.9 GB (Storage only)
  Disk /dev/sdb: 500.1 GB (Systems)
   
  **ubuntu@ubuntu:~$ sudo blkid**
  /dev/loop0: TYPE="squashfs"
  /dev/sda1: LABEL="Maxtor Storage"
  /dev/sdb1: UUID="1CLDD70434AAA" TYPE="ntfs" // this is the Bootmanager of Windows 7
  /dev/sdb2: LABEL="Seagate Windows 7 64 Bit            // Windows 7 System Partition
  /dev/sdb3: LABEL="Seagate Applications
  /dev/sdb5: LABEL="Seagate Ubuntu                             // Ubuntu 11.04 System

---

### Post by williejones on 2011-05-17
> Where and how to install GRUB on my system to fix my DualBoot?Where--Reinstall grub to /dev/sdb

How-- [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by _1MoreDay_ on 2011-05-18
> **williejones said:**
> Where--Reinstall grub to /dev/sdb

The fact that I have my boot system stored on a 2nd HD makes it tricky. 

Reinatll GRUB on /dev/sdb ?
OR, what about reinstall GRUB inside the /dev/sdb1 ?

I need to know where the Master Boot Record need to be stored !
Non of the methods could help me getting it back.

I now try out [B] [Rescatux]("http://rescatux.berlios.de/")


[/B]

---

### Post by Rubi1200 on 2011-05-18
> OR, what about reinstall GRUB inside the /dev/sdb1 ?
You definitely do NOT want to do that; or you will end up having to restore the Windows boot partition.

Based on what you have told us, the best advice is to reinstall GRUB to the MBR of sdb.
You can follow the instructions here:
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

If you want us to take a closer look before you do anything, then please post the results of the boot info script. There is a link at the bottom of my post with instructions.

Thanks.

---


---
title: "USB detected but not accessible"
date: 2012-09-03
forum: General Help
---

### Post by SeaHawk22 on 2012-09-03
I gparted/formatted a USB drive to fat32, and it is detected by USB in Ubuntu, and in Windows 7. I can access the drive on my Windows system (add files), but I cannot access the drive from my home folder in Ubuntu. I am not sure if this helps, but here is the output from lsusb command in terminal.

```
 cubuntu@laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 002 Device 011: ID 0781:5530 SanDisk Corp. Cruzer 
```

---

### Post by gordintoronto on 2012-09-04
The flash drive should appear on your desktop. or, if you start the Nautilus File Manager, it should appear as "nn GB Filesystem" near the top-left. Just click on it, and you should be able to copy files to or from the flash drive.

---

### Post by NikTh on 2012-09-04
Hello , 

If you formated recently (no sensitive data inside) then try to reformat the USB with **Disk Utility** (and not Gparted)

Do not forget to [COLOR=Red]**Delete** [/COLOR]the filesystem first (**unallocated space**) and then recreate it . 

Thanks

---

### Post by shreepads on 2012-09-04
Since you're using SanDisk and have a Win 7 install available, best way would be to get the SanDisk USB repair tool from their website (for Win 7) and run it on the drive while connected to a Win 7 instance...

Sometimes the OS tools are not enough and manufacturer specific tools are required, most of which are not available in Linux unfortunately...

---


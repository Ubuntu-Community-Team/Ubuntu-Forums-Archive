---
title: "About Grub problem and Removal of Kubuntu"
date: 2012-08-25
forum: General Help
---

### Post by amir786_z on 2012-08-25
Hi there guys.. is there any simple method to recover Grub? I am not so good at programming and not with linux please give some simple solution.. The Grub is main reason due to which i am stuck with wubi installation method.

And i want to know how to remove kubuntu without messing up my whole system. I want to keep both Windows 7 and Kubuntu..

Thanks :)

---

### Post by Erik1984 on 2012-08-25
1. Wubi does not install GRUB (but adds an entry to the NT loader for Ubuntu). How did you get GRUB, did you install Kubuntu next to Windows or from within Windows?

2. I don't understand this part:
> **remove kubuntu** without messing up my whole system. I want to **keep both Windows 7 and Kubuntu..**

---

### Post by amir786_z on 2012-08-25
> **Euroman said:**
> 1. Wubi does not install GRUB (but adds an entry to the NT loader for Ubuntu). How did you get GRUB, did you install Kubuntu next to Windows or from within Windows?

2. I don't understand this part:
**remove kubuntu** without messing up my whole system. I want to **keep both Windows 7 and Kubuntu** 

1. I didnt get grub. i said i want to install kubuntu normally not by wubi but iam afraid of grub issue.. so iam stuck with wubi intalled kubuntu.. so anyone have simplest way of recovering grub incase of any failure?

2. If i installed kubuntu normally without wubi.. so what is the method to remove kubuntu? without messing up my windows??

Hope its clear now :)

---

### Post by oldfred on 2012-08-25
Reinstalling grub is not a big issue is you have a liveCD. You should always have a liveCD or repairCD for every system you have installed.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you prefer a gui, you can download this into your Ubuntu liveCd when you need it or download as a full liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

You should also have good backups & a Windows repairCD.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by amir786_z on 2012-08-25
> **oldfred said:**
> Reinstalling grub is not a big issue is you have a liveCD. You should always have a liveCD or repairCD for every system you have installed.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you prefer a gui, you can download this into your Ubuntu liveCd when you need it or download as a full liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

You should also have good backups & a Windows repairCD.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


Thanks man :)

---

### Post by amir786_z on 2012-08-27
Whats the the method of removing ubuntu/kubuntu? just format the drive?

---

### Post by oldfred on 2012-08-27
You can use gparted from the liveCD to delete partitions. You may have to click on swap and right click swap off. Only use Windows to resize the Windows partitions, not gparted.

If reinstalling you can use  manual install and choose the same partitions.

---

### Post by amir786_z on 2012-08-27
> **oldfred said:**
> You can use gparted from the liveCD to delete partitions. You may have to click on swap and right click swap off. Only use Windows to resize the Windows partitions, not gparted.

If reinstalling you can use  manual install and choose the same partitions.

thanks :)

---


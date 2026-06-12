---
title: "uninstall ubuntu 11.04"
date: 2011-09-25
forum: General Help
---

### Post by spider05906 on 2011-09-25
Hi all;
first of all im so noobie in ubuntu and this is my first time using it.

i have windows 7 already installed and i installed ubnutnu 11.04 [dualbooted] and now i want to uninstall ubuntu. i read once in internet that i can do it by deleteing the disk partition of ubuntu so i did therefore i lost the windows bootloader and a black screen appeared with something like (grub) in it so installed ubuntu back again (using the option (alongside with windows) AGAIN) and now its back again.

so my question is how i can uninstall ubuntu and keep the windows bootloader????

P.S: i didnt use wubi in the first place, all was from an ubuntu disk

---

### Post by garvinrick4 on 2011-09-25
Partition install use Windows disk and reinstall windows boot loader:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

If do not have a Windows disk:
Use Ubuntu install disk and Try Ubuntu and open a terminal (ctrl/alt/t)
and copy and paste these two commands.
 
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR
Now reboot into windows.

##Anyone with WUBI install can uninstall by using ADD and Remove programs in Windows or go to Ubuntu folder in C: drive open and use uninstall.

---

### Post by oldfred on 2011-09-25
+1 on garvinrick4's suggestion.

But you should always have a repair CD for every system you have installed. Ubuntu or other Linux can do many repairs even to Windows systems, but you really need a Windows repairCd or USB for some Windows issues.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---


---
title: "Grub rescue help please mates!"
date: 2012-09-08
forum: General Help
---

### Post by scorpiorian83 on 2012-09-08
hey hi everyone!

i have had windows 7 installed and decided to install ubuntu as well.
so i managed to use wubi to install it.
however, after that i decided to completely format my laptop and so i did an uninstall just from the windows control panel.

right now whenever i turn on my laptop, it says:

error: unkonwn filesystem.
grub rescue>

is there anyway around here just so that i can boot back to my windows 7?
please help me coz i'm kinda stuck and helpless.

thanks in advance!

---

### Post by oldfred on 2012-09-08
Welcome to the forums.

If you had wubi, you should not even have the grub boot loader in the MBR? wubi boots via the Windows boot loader.

Do you have a Windows repairCD or an Ubuntu liveCD to make repairs with?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

If you have access to or a friend with the same 32bit or 64bit, you can create a Windows repair disk.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

From Ubuntu you can use this to repair with a gui or download a full repairCD.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by scorpiorian83 on 2012-09-08
oh hey hi,

i'm so impressed about the response over here.

luckily i managed to find a ubuntu live cd i had when i installed the previous times.
phew.....you don't know how glad i am.
but anyway thanks for the help and have a great weekend! :D

---


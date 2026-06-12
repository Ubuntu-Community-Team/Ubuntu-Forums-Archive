---
title: "Fixing GRUB version?"
date: 2011-11-25
forum: General Help
---

### Post by Xtensity on 2011-11-25
I recently installed windows 7 to an additional hardrive, which overwrote my grub bootloader.

I booted ubuntu with the live CD and fixed the grub boot loader with

sudo mount /dev/sda3 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda

restarted and did

sudo update-grub


.

Now when my computer boots, it boots to this quick black screen where I have 3 seconds to press escape to get to the boot menu(with all my operating systems). This menus only shows 3 ubuntu installations(for some reason?), and an option that says chain load into grub 2. This last option gives me an error.

It doesn't even show my Windows 7 Installation..

How do I get back the grub screen that is pink and white and will list all operating systems on all partitions and all discs?

---

### Post by oldfred on 2011-11-25
If you have a chainload into grub2, it sounds like you still have grub legacy installed??

Download this and post the link it provides for the boot info script. May be able to auto repair it also.

Yanni has created a easy way to download boot repair & run boot info script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Xtensity on 2011-11-26
I ran boot-repair and got grub 2 reinstalled(haven't verified it through restarting yet)

It said this in the console though..


Found linux image: /boot/vmlinuz-2.6.35-31-generic
Found initrd image: /boot/initrd.img-2.6.35-31-generic
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1 *******(Broken Win 7)
Found Windows NT/2000/XP (loader) on /dev/sdg1


For some reason it doesn't see 'Windows 7 64' on /dev/sdb1. It appears to be completely absent. Why would this be?



BTW:[http://paste.ubuntu.com/750027/](http://paste.ubuntu.com/750027/) Boot info output

---

### Post by oldfred on 2011-11-26
Windows 7 uses three files to boot and the first two are with  7 often in a seperate boot recovery partition. If you have multiple installs it combines the first two boot files into the first install, so they are missing from any additional installs.

Windows boot files, first two may not be in same partition as the third which will be the c: "drive":
[COLOR=DarkRed]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

    Boot files:        /menu.lst /grldr [COLOR=DarkRed]/Windows/System32/winload.exe[/COLOR] /grldr 
                       /grldr.mbr /wubildr /ubuntu/winboot/wubildr 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

Ubuntu says your sda1 is broken, not sure why. You have wubi files in both sda1 & sdb1.
You also have menu.lst in sdb1 which is from grub legacy, wubi files & grldr.
Do you want to keep the wubi install since you now have a full install in sda3?

Do you have a Windows repairCD for a full install DVD, so you can run Windows repairs. 
Or know someone with a working version of Windows 7 that is the same 32 or 64Bit verison?

Windows only boots from or repairs the active partition (boot flag), so I would puta boot flag on sdb1 and move the boot flag from sda3 to sda1.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

After moving boot flag, I might copy bootmgr & the BCD to the same locations and run Windows repairs. But you  need to houseclean menu.lst, and probably some of the other files first also. You can back them up if concerned about something you want to save.

---


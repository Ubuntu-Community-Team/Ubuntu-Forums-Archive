---
title: "Huge problem! Need Help! Grub Rescue?"
date: 2010-04-10
forum: General Help
---

### Post by schwabdale on 2010-04-10
I have a Laptop with Windows 7 and Ubuntu 10.04 on it. I booted off a Ubuntu 9.10 CD and Installed 9.10 to a flash drive.  During the Install to the flash drive, it asked me if I wanted to update Grub. I could keep the currently installed version or the package maintainers. I choose to update to the package maintainers. 

Now... The only way it will boot is if the Flash drive is plugged in. If its not plugged in I get the following 
message..... 

Grub loading.
error. no such disk
Grub rescue>


Please help

---

### Post by nitstorm on 2010-04-10
[http://www.ubuntu-inside.me/2009/06/...r-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

Maybe this could help...??

---

### Post by MooPi on 2010-04-10
Your grub was corrupted by the new install and need to be updated to function..    [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by schwabdale on 2010-04-10
I will try and post the results. Thanks for the help!

---

### Post by themusicalduck on 2010-04-10
It sounds like grub was installed onto the flashdrive, and now it expects to have the flashdrive in for it to be able to boot.

I would first try booting up with the flashdrive in. Once you have booted into the Ubuntu which is installed onto your computer (not the flashdrive version), take the flashdrive out and run this in a terminal ```
sudo update-grub
``` and see if grub will work again after that.

If that doesn't help anything, then I'd follow these instructions to reinstall grub to the drive in your computer:

[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2)

---

### Post by motsteve on 2010-04-10
Sounds to me like it wants to use the grub that is on the USB stick.  Try the easy stuff, but if push comes to shove try:

[http://ubuntuforums.org/showthread.php?t=1295297](http://ubuntuforums.org/showthread.php?t=1295297)

It involves a  lot of keying in the terminal window.  Good luck.

Steve

---

### Post by oldfred on 2010-04-10
If you can boot to the install on your hard drive with the USB installed:

reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

---

### Post by schwabdale on 2010-04-10
Thanks for all the help! I updated Grub after I booted into another Ubuntu installation. 

For future reference.. What if I dual booted with Ubuntu and Windows 7... Then had some problems with Ubuntu and had to uninstall it. How do I remove Grub and just go back to normal windows?

---

### Post by misterbk on 2010-04-10
> **schwabdale said:**
> Thanks for all the help! I updated Grub after I booted into another Ubuntu installation. 

For future reference.. What if I dual booted with Ubuntu and Windows 7... Then had some problems with Ubuntu and had to uninstall it. How do I remove Grub and just go back to normal windows?

I can't spout the solution to that off the top of my head, but I've found that by far the best way to dual-boot Win7 and Ubuntu is using the bios boot select built in to your motherboard.  Neither OS and neither bootloader need be aware of the other OS or the other bootloader, so all the annoying incompatibilities that have recently surfaced become moot.

For a machine with e-sata, it's even easier...  I tell my machine the first boot device is e-sata, and if I want to boot Linux I just plug in the cable.

---

### Post by oldfred on 2010-04-11
This has info on reinstalling boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From Ubuntu you can reinstall:
Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by Doctor Mike on 2010-04-11
> **oldfred said:**
> This has info on reinstalling boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From Ubuntu you can reinstall:
Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbrWow I could have used something like this when I first tried the Lucid beta instead of doing it all the hard way, or almost... restore image...

---

### Post by schwabdale on 2010-04-12
Thanks

---


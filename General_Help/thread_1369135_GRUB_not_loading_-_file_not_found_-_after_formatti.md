---
title: "GRUB not loading - file not found - after formatting partitions"
date: 2009-12-31
forum: General Help
---

### Post by nandopinheiro on 2009-12-31
I have installed LINUX after WINXP. But for me, the version 9.10 of Ubuntu was not working well, because my Video Board is VIA and the existent drivers are not working well for this kernel version. So, i´ve decided to install UBUNTU 8.04LTS. I have formatted all the partitions related with LINUX, in the Windows using "Partitiong Magic".
 So i messed up with GRUB2, and when i start my laptop this message appears


 GRUB LOADING..
Error: File not Found.

Then it goes to the  "grub-rescue>" prompt.


 My BIOS is set to BOOT with CD-ROM, i used a cd with UBUNTU 8.04 and UBUNTU 9.10 but they don´t initialize.:confused:

Is there any command to use in "grub-rescue>" prompt, to shut down the grub loading, and allow the PC BOOT directly in the Windows XP?

I am desperate and i have no idea what to do... PLEASE HELP ME!!


PS: Is SuperGrubDisk working for GRUB2? In their Forum they say no... 

[I]**Where will I find help?**
If you want help for GRUB2 (1.9X) please go elsewhere.[/I]

---

### Post by Sensiva on 2009-12-31
Use your Windows XP installation cd and boot to recovery mode, it will give you a command prompt, invoke fixmbr command, it will reinstall the NTLDR (WinXP boot loader).

---

### Post by Leppie on 2009-12-31
> **nandopinheiro said:**
> PS: Is SuperGrubDisk working for GRUB2? In their Forum they say no... 

[I]**Where will I find help?**
If you want help for GRUB2 (1.9X) please go elsewhere.[/I]

AFAIK karmic was the first ubuntu release to ship with grub2, so 8.04 lts should be using grub legacy (0.9x).

---

### Post by wereguy2 on 2010-01-12
I am having a similar problem. I installed 9.10 Kubuntu on my netbook, but found that it was not very compatible, so I - through the 9.04 Ubuntu LiveCD environment - formatted it's drive and tried to install Ubuntu on it. It said something about files not being able to copy and when I tried to restart and switch to Windows 7, the whole File not found thing popped up.
It does not appear to want to boot anything, either. I have tried both of the mentioned distributions (Ubuntu 9.04 and Kubuntu 9.10), as well as SuperGrubDisk (though a unetbootin-imaged USB)...

---

### Post by amsterdamharu on 2010-01-12
Grub is still in the mbr but the files in /boot/grub are missing. Don't think you can boot anything off the harddisk anymore but you should be able to boot off a usb stick or cd. As mentioned before either fix grub booting off CD or usb or fix mbr with windows cd.

You can try the following commands to boot windows:
root        (hd0,0)
savedefault
makeactive
chainloader    +1

hd(0,0) means that windows is on the first harddisk and the first partition.

---

### Post by Leppie on 2010-01-12
you can use windows recovery or an ubuntu livecd to restore the mbr.
booting with the ubuntu livecd, open a terminal and issue these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
this should restore the mbr to factory defaults.

---

### Post by wereguy2 on 2010-01-12
Well that's the problem, I - and since he seems to have the same problem, nado - cannot boot from the liveCD, since it seems to not do any BIOSey stuff at all (the computer, not the liveCD).
Shouldn't there be some sort of command that can be input into the grub rescue> prompt that can help?

EDIT. Okay, I am NOT very linux-learned, but it seems to me that the only way out of this is to use the prompt to switch to the windows BIOS.
I have tried booting in a number of different ways, including using a windows ghost image, but nothing has worked.
However, a few GRUB commands did work; "ls" listed the various partitions, "ls /boot" showed up with a weird string etc.

EDIT2. Okay, nevermind, got the liveCD to work.

---

### Post by geomic788 on 2011-01-07
man how did u make the Live Cd work? cd nor usb wil initialize
Please Help

---


---
title: "Installed Windows 7 - grub Boot Menu Gone"
date: 2009-11-23
forum: General Help
---

### Post by vergeh on 2009-11-23
Hi there,

To explain a little about my setup - I have three drives, in the order they appear in BIOS. 

The first drive was a dedicated Windows XP installation (now holds Windows 7)
The second drive is a NTFS drive with no installed applications (used only for storage)
My third drive is divided into 3 partitions:
- ext4 partition for Ubuntu 9 (upgraded from Ubuntu 8)
- swap partition for the Ubuntu installation
- NTFS partition (now housing backup for Windows XP)

My grub menu was fine and dandy until I installed Windows 7 Professional 64-bit on the first drive. Now when I power on my PC, the menu does not appear. I have three major questions:

1. How do I get back into my Ubuntu installation?
2. How do I restore the grub menu on boot?
3. Do I need to alter my grub menu to boot into Windows 7?

Thanks in advance. I'm at my wit's end here.

---

### Post by Giblet5 on 2009-11-23
Boot from the LiveCD in "Try It" mode.

Open a terminal window (Applications -> Accessories -> Terminal)

Run the following command: ```
sudo fdisk -l
```

Which partition is the ext4 / partition? (Don't ask me - I have no idea how you set up your system)

Let's assume that it's [COLOR="DarkRed"]/dev/sdb1[/COLOR] but USE WHAT YOU REALLY HAVE.

```
sudo mount [COLOR="DarkRed"]/dev/sdb1[/COLOR] /mnt
```

Now look at /mnt with a file browser window. Make sure it's a / filesystem. (/mnt/etc, /mnt/usr, /mnt/home, etc exist)

You might want to use copy/paste for these commands... The correct syntax is not "optional".

```
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt/bash
update-grub
grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
exit
```

Now, you should have a grub menu that let's you boot Ubuntu or Win7.

---

### Post by audiomick on 2009-11-23
Hallo.
The windows upgrade will have overwritten Grub.
You write that you are using Ubuntu 9.
Does this mean 9.10? If so, you had GRUB2, and should read this;
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If it is 9.04, it is still GRUB. You have to do the appropriate equivalent re-install. of GRUB. As I understand it, it is a little simpler with GRUB than with GRUB 2. I am sorry I can't offer a link for GRUB. I got the one for GRUB 2 out of a thread I read 5 minutes ago. A search for re install GRUB should produce results.

---

### Post by vigalance on 2009-11-23
Windows 7 has to be installed first

---

### Post by namok on 2009-11-23
J don't know which version of grub you have. If it is Grub Legacy (with menu.lst) you can simply restore grub with [Super Grub Disk.]("http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso") Start the computer with the cd and select:```
GRUB => MBR & !LINUX! (1)   AUTO
```If you have Grub2 (with grub.cfg) start the computer with the cd and select:```
1. Choose Language & NO HELP
2. English Super Grub Disk
3. Gnu/Linux
4. Boot Gnu/Linux
5. Boot Gnu/Linux Directly
```Ubuntu should start. Then i terminal:
```
sudo grub-install /dev/sd[COLOR=Red]X[/COLOR]
```where [COLOR=Red]X[/COLOR] is the disk number (a-1, b-2, c-3).

---

### Post by danielt998 on 2009-11-26
download supergrubdisk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) and put it on a floppy or something. It should let you boot from you GRUB installation and then set it as the default.

---

### Post by e-nygma on 2009-11-26
1.Re-install GRUB

Windows 7 has completely eaten your boot loader so you need to re-install grub. 
Boot from the ubuntu live cd and go to terminal.
Type the following in the terminal:

"sudo grub"
"grub> find /boot/grub/stage1"

That should return your Ubuntu partition in the form of (hdX,Y), use that:

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

(you don’t need to type the grub> bit)

The preceding steps will re-install grub, but you can no longer see windows 7

2.Edit grub

Reboot your system without the Live CD.  Go to the terminal and type :

“sudo gedit /boot/grub/menu.lst”

A large text file will open and at the bottom leave a line and add this:

title windows 7 (Loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

	save, exit and reboot.

(Do not type this line but if that does not work on re-boot try “hdo,0 or hd0,2” and so on until it works.)

I had the same problem when I re-installed windows, but I found the solution when I googled it.  Good luck and I hope it helps.  Cheers, dude!

---


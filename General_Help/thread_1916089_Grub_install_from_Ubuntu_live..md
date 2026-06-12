---
title: "Grub install from Ubuntu live."
date: 2012-01-27
forum: General Help
---

### Post by Zenock on 2012-01-27
Question...

I want to dual boot between Windows 7 and Dos.

I want to use Grub to do this instead of the Windows bootloader.

Is this possible?  Or do I have to have linux installed. 

Right now when I try to do grub-install I get the message...

error: cannot find a device for /boot/grub (is /dev mounted?).

I get this when ever I tried to do this from Ubuntu Live, even if I'm trying to install grub on a linux partition.  What am I doing wrong?

---

### Post by dragonfly41 on 2012-01-27
If you want a bootable DOS device .. perhaps in USB stick
here is one suggested approach ...

Boot up Ubuntu Live CD and install unetbootin
[COLOR=Navy][B]
sudo apt-get install unetbootin[/B][/COLOR]

then launch unetbootin from Applications > System Tools

 "select distribution"  e.g. FreeDOS to burn into USB stick (formatted FAT32)

You can select the USB DOS by F12 on starting up your PC and choosing USB (if your bios allows this).

---


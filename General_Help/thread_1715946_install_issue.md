---
title: "install issue"
date: 2011-03-27
forum: General Help
---

### Post by stktek on 2011-03-27
I am trying to install ubuntu 10.04 on my HP G60-445DX which has windows 7. i want to do a complete win7 wipe and just run Ubuntu but when i run the install disc i get an error not able to mount.
I believe it has something to do with the bios which will not let me get into the hard drive config
Any help would be great

---

### Post by gordintoronto on 2011-03-28
When, exactly, does this error come up? Are you trying to boot from a CD or a flash drive? Do you get to the "install or try" menu?

I use Ubuntu for everything, but I would still suggest you make a set of Windows 7 recovery DVDs before you blow away Windows 7. Perhaps two years from now you will decide to sell the computer, and the buyer might want Windows 7.

---

### Post by stktek on 2011-03-28
Boot from CD the Ubuntu screen comes up and then i get the following.
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'Help' for list of built-in-commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashf

---

### Post by gordintoronto on 2011-03-28
There are two articles in the Ubuntu Community Documentation which might help you. The first describes common problems with the CD, and is called BootFromCD. The second describes using boot options to handle quirks with your hardware, and is called BootOptions. From what I have seen, one or the other of them solves at least 90% of the problems.

---

### Post by stktek on 2011-03-30
Solved the problem by using a usb stick.
I tried different cd's and even bought a Ubuntu mag with a cd and that did not work either. I found this issue on a number of sight after a search on google and believe it an issue with the cd drive.

---


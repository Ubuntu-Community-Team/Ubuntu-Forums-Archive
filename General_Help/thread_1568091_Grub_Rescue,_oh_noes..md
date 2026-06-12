---
title: "Grub Rescue, oh noes."
date: 2010-09-04
forum: General Help
---

### Post by Sarteck on 2010-09-04
Right...  So for the past few months, every time I boot my computer, I've been presented with the lovely Grub Rescue prompt, because it couldn't pind the partition it was looking for.

At the prompt, I've had to type the following to get myself started:```
set root=(hd0,7)/
set prefix=(hd0,7)/boot/grub/
insmod (hd0,7)/boot/grub/linux.mod
linux (hd0,7)/vmlinuz root=/dev/sda7 ro
initrd (hd0,7)/initrd.img
boot
```

It seems that it's looking for hd0,8 instead of hd0,7 (at least that's what "set" reports when I run it without any arguments before doing the above).

I've tried **sudo update-grub** a few times, and although it seems to be doing whatever it's supposed to do (it doesn't throw any errors at me, anyhow), I'm still presented with that damned Grub Rescue prompt.



This started after I'd used GPartEd to squish back together a bunch of my separate partitions, so probably has something to do with it. XP



I'm in no hurry--I only reboot this thing once in a great while--but I would like to know how to fix it.  Any ideas, anyone?  Probably some utility on the GPartEd disk or somethin', yah?

---

### Post by oldfred on 2010-09-04
The sudo update-grub only updates the menu but does not reinstall grub to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

If you are booting into your install you do not have to use liveCD. The main difference is you do not have to tell it (mount partition with Ubuntu) which partition has Ubuntu, as you are already inside it.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---


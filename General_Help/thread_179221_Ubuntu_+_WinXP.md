---
title: "Ubuntu + WinXP"
date: 2006-05-19
forum: General Help
---

### Post by SreckoMicic on 2006-05-19
I got a question. 
I have Ubuntu and WinXP on two drives (XP is master). Grub is also installed on Master. So problem is that I need to format Xp hard drive and it will erase Grub too. Is there any posibility to install later Grub and to have functional old Ubuntu and newly installed XP.
Thanks for any answer and explaination.

---

### Post by savas on 2006-05-19
Hi. There are a lot of solutions to this problem. Firstly, create a grub floppy:

sudo grub-install fd0

If it works skip below, After install winxp boot from floppy. Then boot ubuntu. After ubuntu boot install grub to master hard drive.

sudo grub-install /dev/hda (use your master disk instead of /dev/hda)

And thats all.

If it gives a error interested with bios fallow below instructions.

sudo grub-floppy

Then save informations that grub uses to boot system.

In my system;

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

Install winxp. Boot from grub floppy, Enter to command mode and give below commands

root (hd0,1)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet
initrd          /boot/initrd.img-2.6.12-10-386
boot

After boot ubuntu, install grub to master disk

sudo grub-install /dev/hda (use your master disk instead of /dev/hda)

A second solution and easer solution is using Super grub disk.

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by redistributer on 2006-05-19
it's easier if you go into the grub configuration write down the target of linux and when you reinstall windows add that to the windows boot loader, that would be your best bet.

If you right click my computer in xp go to advanced, go to startup options (don't remember what button it is) once in the window you can edit the file manualy and make it look like the grub configuration. reboot and test

Do what was stated above just in case you do happen to mess up.

Now you got a couple solutions

-Red

---


---
title: "Boots straight to initramfs"
date: 2011-10-28
forum: General Help
---

### Post by Rob T on 2011-10-28
When I start up my laptop it flashes a cursor for a while the says:

No init found. Try passing init= bootarg 

Busybox v 1.13.3 (ubuntu 1:1.13.3-ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


It wont boot into the grub menu either so I cant enter the recovery mode, any ideas how to get it to boot normally? Thanks for any help in advance

---

### Post by Rubi1200 on 2011-10-28
Hi and welcome to the forums :)

Please post the results of the boot info script so we can diagnose the problem.

There is a link at the bottom of my post with instructions.

---

### Post by ionplay on 2012-02-06
my HH 8.0.4 was booting straight to initramfs after a fresh install

I had to use the F6 boot option to get the install done
added 
all_generic_ide floppy=off irqpoll

problem is the new SSD drive

once installed it would still boot to initramfs - thought after the install everything would be wonderful

had to edit the /boot/grub/menu.1st and manually add the boot option there

now everything is peachy

---


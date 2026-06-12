---
title: "editing mbr"
date: 2011-02-10
forum: General Help
---

### Post by jonnny_j22 on 2011-02-10
Hi all, 
Here's my set up - 
sda1 windows7 using easy bcd
sda2 net bsd - net bsd bootloader
sda4 puppy linux - Grub4dos
sda5-7 Ubuntu - booted via puppy's grub4dos

When you turn on the machine you go to the mbr prompt set up by net bsd. from here you choose to go to easy bcd, grub4dos, or the netbsd bootloader.

I recently had to reinstall ubuntu and forgot to not install grub (I boot it using puppy's grub. I have got it all sorted, the only problem is i don't know how to remove the ubuntu 'linux' entry from the mbr select? now I've got rid of Grub2, my mbr screen looks like this

1 windows
2 bsd
3 linux
4 linux

I want to get rid of number 3.. any ideas?

---

### Post by jonnny_j22 on 2011-02-11
I have now fixed the problem using a netbsd installer. Does anyone know of a way to do it without using the installer? not a massive issue I know, but still, if there's an easier way?

---


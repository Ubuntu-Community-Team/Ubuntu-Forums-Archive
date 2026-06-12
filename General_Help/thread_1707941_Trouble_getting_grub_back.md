---
title: "Trouble getting grub back"
date: 2011-03-16
forum: General Help
---

### Post by destructaball on 2011-03-16
Hi there,

I'm trying to get grub back after a windows install something I've done about 5 times before. My system is half 11.04 half windows 7, I'm using a 10.04 live USB, I mount my ubuntu partition then type into the terminal:

mount | tail -1

it outputs

/dev/sda1 on /media/c1ae6896-daae-4453-9c81-002a6af9569c type ext4 (rw,nosuid,nodev,uhelper=udisks)

I then type in

ls /media/c1ae6896-daae-4453-9c81-002a6af9569c/boot

it then outputs

abi-2.6.38-5-generic         memtest86+_multiboot.bin
abi-2.6.38-6-generic         System.map-2.6.38-5-generic
config-2.6.38-5-generic      System.map-2.6.38-6-generic
config-2.6.38-6-generic      vmcoreinfo-2.6.38-5-generic
grub                         vmcoreinfo-2.6.38-6-generic
initrd.img-2.6.38-5-generic  vmlinuz-2.6.38-5-generic
initrd.img-2.6.38-6-generic  vmlinuz-2.6.38-6-generic
memtest86+.bin

I then type in

ls /media/c1ae6896-daae-4453-9c81-002a6af9569c

and it outputs

bin    dev   home            lib    lost+found  opt   sbin     sys  var
boot   etc   initrd.img      lib32  media       proc  selinux  tmp  vmlinuz
cdrom  grub  initrd.img.old  lib64  mnt         root  srv      usr  vmlinuz.old

I then type in

sudo grub-install --root-directory=/media/c1ae6896-daae-4453-9c81-002a6af9569c/ /dev/sda

it outputs

Installation finished. No error reported.

When I restart there is just a blinking cursor, I know I'm doing something stupid, I just don't know what...

Thanks in advanced :)

PS I'm following these instructions as close to the letter as I can
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindowe](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindowe)

---

### Post by zvacet on 2011-03-16
Read [this]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") and see if it helps.

---


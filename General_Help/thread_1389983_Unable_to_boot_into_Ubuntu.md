---
title: "Unable to boot into Ubuntu"
date: 2010-01-25
forum: General Help
---

### Post by blairm on 2010-01-25
Hi,

Installed Fedora as a dual boot the other night out of curiosity - wanted to play with an rpm distro for a bit - and I am now unable to boot into Ubuntu.
Have done some searching on the web and I gather I need to edit grub, but I'm unsure how to proceed; grub is an area I've had little to do with and instructions I've found have been pretty complex.
Is anyone able to offer some easy to understand advice?

Thanks,

Blair

EDIT: Using Karmic and Fedora 11

---

### Post by byStanderone on 2010-01-25
...reinstall grub:

-boot from your karmic live cd

-findout your karmic partition (sdxy or whatever it is): sudo fdisk -l

-mount your karmic partition: sudo mount /dev/sdxy /mnt

-reinstall grub: sudo grub-install --root-directory=/mnt /dev/sdx (do not include 'y' )

-unmount the partition: sudo umount /mnt

-reboot

---


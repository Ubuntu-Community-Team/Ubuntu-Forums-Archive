---
title: "Windows 7 and Ubuntu 11.10"
date: 2011-11-19
forum: General Help
---

### Post by ramus313 on 2011-11-19
i am running ubuntu 11.10, and i have a windows 7 32 bit iso file saved on my computer, is there a way to install it and dual boot with ubuntu without getting a blank disk, i mean like how can i mount the iso file and what exactly would i do? sorry im new to linux... p.s. i have power ISO

---

### Post by hansdown on 2011-11-19
Hi, ramus313.

You need to burn the ISO, to a disk, or usb.

It needs , to be bootable.

CAUTION:

Installing windows, after ubuntu, will erase the ubuntu boot loader.

---

### Post by justinram22 on 2011-11-19
To elaborate on what the poster above me said, burn it to a disk, boot it, and install it on its own partitions (do not install over the ubuntu partition).  This is going to erase your grub bootloader and you will not be able to boot into Windows.  You are going to have to boot off of a liveCD again, and reinstall Grub.

I'm sure there are plenty of videos on Youtube.

---


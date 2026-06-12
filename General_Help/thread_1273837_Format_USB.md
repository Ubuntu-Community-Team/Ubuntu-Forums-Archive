---
title: "Format USB"
date: 2009-09-23
forum: General Help
---

### Post by BarefootSoul83 on 2009-09-23
what the terminal command for Formatting a USB to Fat32

---

### Post by peculiar penguin on 2009-09-23
[FONT=Courier New]sudo mkfs.vfat -F 32 <device>[/FONT]

---

### Post by BarefootSoul83 on 2009-09-23
donald@Tux:~$ sudo mkfs.vfat -F 32 /media/disk
mkfs.vfat 3.0.1 (23 Nov 2008)
mkfs.vfat: unable to open /media/disk

---

### Post by community nerd on 2009-09-23
The partition editor works great for that. If it isnt installed in Sytem>Administration> then install it. It is called GParted. I used it today.

---

### Post by tkoco on 2009-09-23
When you format a HD or USB, it cannot be mounted! Use "dmesg" command to find the device name (like /dev/sdb). Then disconnect the USB stick with the "umount" command (or right-click on the desktop icon and select "unmount") Then try the "mkfs.vfat" command again.
Or, as suggested, use gparted.
> **BarefootSoul83 said:**
> donald@Tux:~$ sudo mkfs.vfat -F 32 /media/disk
mkfs.vfat 3.0.1 (23 Nov 2008)
mkfs.vfat: unable to open /media/disk

---

### Post by ninjapirate89 on 2009-09-23
Is there a graphical way to do this other than with GParted? Maybe a nautilus script?
Edit -> Like in Windows you can right click on a drive and click Format.

---


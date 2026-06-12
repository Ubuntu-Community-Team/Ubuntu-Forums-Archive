---
title: "External USB HDD trouble"
date: 2006-05-29
forum: General Help
---

### Post by Fred Doolie on 2006-05-29
I gparted-ed my external 160Gig into two ext3 partitions.
Reformatted the second partition under Winblows2K and set it up as "Z:Windows Stuff"
Works fine under Windoze.
They both auto-mount fine and are readable under Ubuntu.
sda5 (ext3) mounts under /media/usbdisk
sda6 (NTFS) mounts under /media/usbdisk-1

No problems With sda6 (Windows). It shows up on the Ubuntu desktop as "Windows Stuff". Everything is fine.

Problems With sda5 (Ext3):
Can't write to it at all.
It shows up as "74.5 GB Volume" on the desktop. I can't rename it.

Problems With Both:
When I right-click either one and choose "Unmount Volume" they BOTH go away!
I can't remount either one without unplugging/replugging the USB cable.

Please help. Thank you.

---


---
title: "Error booting"
date: 2010-01-16
forum: General Help
---

### Post by professorchaos on 2010-01-16
When I try to start up ubuntu, I get the following message(s):
Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(dev/disk/by-uuid/fb9b16d5-806f-46b2-9a71-93b8c631a5d0) = dev(8,3)
kinit: trying to resume from /dev/disk/by-uuid/fb9b16d5-806f-46b2-9a71-93b8c631a5d0
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/d6c68bcf-5f92-4f26-ac5c-2cb2f44ad4dc on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

Suffice to say, I don't know what any of this means

---

### Post by drs305 on 2010-01-16
Do you get a Grub menu before it attempts to boot? Which version of Grub are you using?  (If you see the grub menu, the version is at the top. 0.97 or 1.97).

If you can't see the menu, press ESC if it's Grub or hold down the SHIFT key if it's Grub 2 to display the menu.

---

### Post by professorchaos on 2010-01-16
I get a grub menu, but there's no version listed

---

### Post by drs305 on 2010-01-16
Here's a possibly quick way to boot:

If it's Grub legacy, and you see a menu, highlight the first entry, press "e" to edit it. Highlight the "kernel" line, press "e" again. Use the cursor/arrow keys to edit: where it has "root=UUID=xxxx..." change that to "root=/dev/sdXY" with XY being your Ubuntu drive/partition. First drive, first partition would be sda1. Second drive, sdb, etc.

Once you have made the change, ESC once, then "b" to boot.

If you get into your system, run:
> 
sudo blkid -c /dev/null
sudo update-grub

and then check your /boot/grub/menu.lst to see if the UUIDs are now correct.

---

### Post by professorchaos on 2010-01-16
Sorry, no luck

---

### Post by professorchaos on 2010-01-18
No other ideas, I suppose?

---


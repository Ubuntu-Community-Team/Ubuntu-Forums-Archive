---
title: "Unable to Boot to Ubuntu 10.10"
date: 2010-10-25
forum: General Help
---

### Post by syrius013 on 2010-10-25
Two days ago, my computer was working fine. Yesterday, I booted to a screen that displayed this:

Gave up waiting for root device. Common Problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)
ALERT! /dev/disk/by-uuid/<long number> does not exist.
Dropping to a shell!

Then it dropped to a busy box.

I hard restarted and it opened to a linux kernel menu. When I selected the older one, it opened perfectly. Today, however, I did the same thing and now the old one opens to the error message.

Any help would be amazing.

---

### Post by syrius013 on 2010-10-25
Ah, I think I found the problem. Apparently its not looking for it long enough. I followed the information here:

This may cause the system to drop to a busybox initramfs shell on boot with a "Gave up waiting for root device." error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't, wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. (290153)

Of course there is no menu.lst anymore. So I typed sudo update-grub and it updated grub.cfg. Fixed.

---


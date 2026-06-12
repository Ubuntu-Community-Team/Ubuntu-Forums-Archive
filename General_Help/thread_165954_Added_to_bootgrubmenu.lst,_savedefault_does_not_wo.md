---
title: "Added to /boot/grub/menu.lst, savedefault does not work."
date: 2006-04-25
forum: General Help
---

### Post by RoboJ1M on 2006-04-25
Hi,

nvram-wakeup requires a reboot and shutdown to set the auto-timed-boot in my motherboards BIOS (Abit BD7). I use this with mythtv to let my pc boot when I want something recorded and I am not there.
I have added the following script to my system for nvram-wakeup and mythtv:

```
james@HAL:~$ cat /usr/sbin/mythshutdown
 ### /usr/sbin/mythshutdown ###
echo "savedefault --default=5 --once quit" | grub
reboot
```

This changes the default grub entry to No.5 and reboots.
This is the (new) entry, No.5
```

title           Power Off
savedefault     --default=0
halt

```
Now this is *meant* to set the default boot option back to 0 (normal) and shutdown.

But the default stays as Power Off. So as soon as the PC boots again, it powers off. Again and again and again, unless I Esc into grub and change it myself.

Can somebody tell me why this doesn't work?

Thanks,

J1M.

---


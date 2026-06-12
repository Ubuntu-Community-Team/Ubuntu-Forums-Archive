---
title: "Edit BootLoader"
date: 2010-01-14
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-01-14
I installed Ubuntu 9.10 on my desktop PC, dual booting with Windows Vista, installation went well, but when the computer boots up, Ubuntu will boot up after a period of 10 seconds unless I intervene, how do I edit the bootloader to change the default OS to Vista? I've included an image of the GRUB menu:

[[IMG]http://img31.imageshack.us/img31/4711/img0057uo.th.jpg[/IMG]](http://img31.imageshack.us/i/img0057uo.jpg/)

The top entry is the Ubuntu entry.

---

### Post by Leppie on 2010-01-14
you can change the default os to vista by editing the grub defaults file. open the file with your editor:
```
gksudo gedit /etc/default/grub
```
change the GRUB_DEFAULT line to the following:
```
GRUB_DEFAULT="Windows Vista (loader) (on /dev/sda1)"
```
do not omit the quotes, as that will result in not booting Vista as default.
save the file and close it, then run updat-grub:
```
sudo update-grub
```

and reboot your system, the default should now be set to Vista

---

### Post by ..::| Dave89 |::.. on 2010-01-14
Thanks, that worked.

---


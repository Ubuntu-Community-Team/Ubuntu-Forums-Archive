---
title: "grub.cfg update is stuck (I know why but need fix)"
date: 2010-12-04
forum: General Help
---

### Post by cereal killer on 2010-12-04
The problem is anytime there is a GRUB update in Ubuntu (I use 10.04), once it gets to the new Kernel install and installs grub, it gets stuck at the grub.cfg part and never finishes.

I've seen people come across this problem, but I don't know why it happened to them, but I know why it happens to me. I have 2 hard disk on my PC, one for OSs, the other purely for storage. This problem never existed until I installed a second hard disk. I have confirmed this by physically unplugging the storage disk and running the update, and everything goes smoothly. But surely there is something that can be done to fix this so I do not have to do this every time GRUB needs an update.

---

### Post by drs305 on 2010-12-04
Try running this and make sure the correct hard drive is selected:
```
sudo dpkg-reconfigure grub-pc
```

It's possible dpkg is trying to find the Grub files on the wrong drive. Do not select a specific partition unless you have a specific need to do so.

---

### Post by cereal killer on 2010-12-04
Doh. My Ubuntu is dead after I restarted when the update was going nowhere (no choice). Looks like I'll need a clean install before I try the above.

Thanks

---

### Post by Habitual on 2010-12-04
Unplug 2nd drive...
If you have a LiveCD, boot to it and go to the desktop.
Open a terminal once in the LiveCD desktop...

sudo fdisk -l (that's an EL)
sudo grub-install **/dev/sd**_*a*_ (yours may be different than sda)
sudo update-grub
reboot to hd.

---

### Post by cereal killer on 2011-01-03
> **Habitual said:**
> Unplug 2nd drive...
If you have a LiveCD, boot to it and go to the desktop.
Open a terminal once in the LiveCD desktop...

sudo fdisk -l (that's an EL)
sudo grub-install **/dev/sd**_*a*_ (yours may be different than sda)
sudo update-grub
reboot to hd.

Finally got around to reinstalling Ubuntu. I have to give a big thank you for the above advice, worked perfectly.

---


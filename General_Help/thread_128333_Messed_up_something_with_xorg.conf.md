---
title: "Messed up something with xorg.conf"
date: 2006-02-11
forum: General Help
---

### Post by matts0344 on 2006-02-11
I was wondering how to change the login screen resolution, its way too high for my monitor, I would like it to be the 1024x768. Is there anyway to change it?

---

### Post by aysiu on 2006-02-11
Sure. Go to Applications > Accessories > Terminal.
Then type these commands: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` Find the appropriate "kernel" line and add the phrase *vga=791* to it.

For example, if your entry looks like this: ```
title          Ubuntu, kernel 2.6.12-10-386
root           (hd0,6)
kernel         /boot/vmlinuz-2.6.12-10-386 root=/dev/hda7 ro quiet splash
initrd         /boot/initrd.img-2.6.12-10-386
savedefault
boot
``` change it to look like this instead: ```
title          Ubuntu, kernel 2.6.12-10-386
root           (hd0,6)
kernel         /boot/vmlinuz-2.6.12-10-386 root=/dev/hda7 ro quiet splash **vga=791**
initrd         /boot/initrd.img-2.6.12-10-386
savedefault
boot
```

---


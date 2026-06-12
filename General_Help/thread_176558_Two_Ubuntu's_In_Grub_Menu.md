---
title: "Two Ubuntu's In Grub Menu??"
date: 2006-05-14
forum: General Help
---

### Post by morbid_bean on 2006-05-14
I booted up my pc and i have a dual boot ubuntu/winxp system and now it shows like it has 2 copies of ubuntu on there...im not talkin about the regular startup and recovery mode, i mean there is 2 diffrent ones on there.....how do i fix this?

---

### Post by Dr. Nick on 2006-05-14
[quote=morbid_bean]I booted up my pc and i have a dual boot ubuntu/winxp system and now it shows like it has 2 copies of ubuntu on there...im not talkin about the regular startup and recovery mode, i mean there is 2 diffrent ones on there.....how do i fix this?[/quote]

If you look close their will probably be 2 different kernel versions. Edit the file /boot/grub/menu.lst and you can remove the lines for one of them. I would comment them out though using #'s at first if you havent done it before.

Also if you are sure you know what you are doing you can remove the older of the 2 kernels, jsut dont remove the runnig one.

---

### Post by morbid_bean on 2006-05-15
[QUOTE=Dr. Nick]If you look close their will probably be 2 different kernel versions. Edit the file /boot/grub/menu.lst and you can remove the lines for one of them. I would comment them out though using #'s at first if you havent done it before.

Also if you are sure you know what you are doing you can remove the older of the 2 kernels, jsut dont remove the runnig one.[/QUOTE]


Which lines are they???

---

### Post by aysiu on 2006-05-15
If you want to uninstall them, use Synaptic Package Manager and search for the word *linux-image* and remove the ones you don't want.

---

### Post by morbid_bean on 2006-05-15
Thanks.. :) :D

---

### Post by Dr. Nick on 2006-05-15
[quote=morbid_bean]Which lines are they???[/quote] Your numbers will vary but I have highlighted the ones in red I would remove on mine. Though if you use synaptic this is unnecessary as it will be done for you. This file must be edited as sudo```


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

......
## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-22-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-22-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-22-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-22-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-22-386
boot
[COLOR=Red]
title           Ubuntu, kernel 2.6.15-21-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-21-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-21-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-21-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-21-386
boot
[/COLOR]
title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault

```

---


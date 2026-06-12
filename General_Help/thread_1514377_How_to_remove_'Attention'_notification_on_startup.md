---
title: "How to remove 'Attention' notification on startup"
date: 2010-06-20
forum: General Help
---

### Post by malel on 2010-06-20
I get this Attention note when starting up to tell me that the system cannot handle video 1080 X 1024 which I am not using. I am using 1024 X 768. How can I get rid of this annoying little notice which slows down the start up considerable as it travel across the screen

---

### Post by malel on 2010-06-20
I am running Ubuntu 9,04 on a Pentium 4 computer and this annoying little message says:

Cannot display this video mode. Change computer display input to 1280 X 1024 @ 60Hz


Any help/suggestions appreciated

---

### Post by Chocrates on 2010-06-20
try adding a small log level to your grub.cfg like so
```
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f3c040e-8515-44ca-b1b8-48ab519d007c
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=0f3c040e-8515-44ca-b1b8-48ab519d007c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
    loglevel=1
}
```

play around with some numbers 0 is the highest priority, and 7 is the lowest.
Keep in mind that even if this makes it not display, the error will still be there, so you might want to figure out why its doing it

---


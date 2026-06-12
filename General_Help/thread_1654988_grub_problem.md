---
title: "grub problem"
date: 2010-12-29
forum: General Help
---

### Post by rockager on 2010-12-29
can someone please convert this program statement from grub.cfg:

menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6c863863-5d0b-4966-bee8-ea988c7556da ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic

to the menu.lst format? (i want to add an OS entry to a  menu.lst file)
thanks in advance

---


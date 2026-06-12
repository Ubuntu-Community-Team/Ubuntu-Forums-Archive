---
title: "Ubuntu 10.10 Grub /boot/grub/grub.cfg msdos listed"
date: 2011-01-19
forum: General Help
---

### Post by richy2010 on 2011-01-19
Anyone else running Ubuntu 10.10 and notice /boot/grub/grub.cfg has msdos in ever menuentry?

Any one know why this could be?

Cheers, rich


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {

class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set fa459e39-b39b-49b8-b856-a4cc468ca39e
        linux   /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=fa459e39-b39b-49b8-b856-a4cc468ca39e ro   acpi_osi=Linux
        initrd  /boot/initrd.img-2.6.35-24-generic-pae
}

---


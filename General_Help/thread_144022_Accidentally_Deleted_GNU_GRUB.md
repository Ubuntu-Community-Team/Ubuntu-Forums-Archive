---
title: "Accidentally Deleted GNU GRUB"
date: 2006-03-13
forum: General Help
---

### Post by bobgb4 on 2006-03-13
I have windows XP installed on my master hard-drive and Ubuntu installed on my second slave hard-drive.

I thought that during the computer start up, Windows would boot default, and I could just choose to boot my 2nd slave drive in order to launch Ubuntu.

So I booted with a floppy and ran "fdisk /mbr," thinking I didn't need the GNU GRUB.

Unfortunately, now when I choose to boot the 2nd slave hard-drive, I get a prompt screen with 'GRUB >.'

Any1 know of a way I can repair or reinstall the GNU GRUB?
Via a live Ubuntu cd maybe?

Thanks!

---

### Post by scristian on 2006-03-13
boot from live cd
open a console 
```

sudo mkdir /a
sudo mount /dev/hdXY /a
chroot /a
grub-install /dev/hdZW

```
now reboot
/dev/hdXY should be your curent ubuntu instalation
/dev/hdZW where you want to install grub

---

### Post by scristian on 2006-03-13
or in grub console
```

find /boot/grub/stage1
root (hd0,0)
setup (hd0)

```

Assuming that you want grub in mbr in first drive.

---

### Post by bobgb4 on 2006-03-13
k thanks il giv it a try

---


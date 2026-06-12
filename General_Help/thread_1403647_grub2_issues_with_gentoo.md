---
title: "grub2 issues with gentoo"
date: 2010-02-10
forum: General Help
---

### Post by poo_22 on 2010-02-10
Trying to get gentoo to play nice with grub2. failing so far.
here's what i got in my 40custom file (doens't work):
menuentry "Gentoo-Linux" {
set root (hd0,7)
kernel /boot/kernel-2.6.31-gentoo-r6 
initrd=/bin/bb
}

when i run grub-update btw it finds gentoo by itself but doesn't add it to the menu.

---

### Post by darolu on 2010-02-10
Try changing "set root (hd0,7)" to "set root=(hd0,7)"
BTW I'm pretty sure it was a typo but the command is "update-grub"

---

### Post by poo_22 on 2010-02-12
no that didn't solve my isssue. it does nothing when i select gentoo from the grub menu. and yes that was a typo.

i looked all around for answers guys but im pretty lost at this point.

---

### Post by Satoru-san on 2010-02-12
I use gentoo as well, which distro did you install first, as in which one is grub on?

---

### Post by poo_22 on 2010-02-14
i installed ubuntu first and that is the one that grub is on. mabe someone can point me to a guide to downgrade my grub to legacy?

---

### Post by bodhi.zazen on 2010-02-14
You need to :

1. Learn the correct terminology of grub 2 ;)

2. Specify the root partition on your kernel line, just as with grub legacy

```
linux /boot/kernel-2.6.31-gentoo-r6 root=UUID=xxx.yyy.zzz ro
``` [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

---


---
title: "how to re-order the grub boot menu"
date: 2010-05-08
forum: General Help
---

### Post by mjsilverstri on 2010-05-08
I have installed ubuntu 10.04 and kubuntu 10.04 on different partition (same hard drive). and window 7 on a different hard drive.

The boot menu order now is 1. kubuntu 2. memtest 3. window 7 4. ubuntu 10.04 kernel 2.6.32.22

I want to change to```
 1. ubuntu 10.04 kernel 2.6.32.22 2. window 7 3. kubuntu 4. memtest

```
These are the files in my ubuntu /etc/grub.d:

```
/etc/grub.d$        ls
00_header*        10_linux*       30_os-prober*  README
05_debian_theme*  20_memtest86+*  40_custom*
```

---

### Post by CryptoPaul on 2010-05-09
Grub 2 is quite different to Grub, I've not yet looked at it in detail myself.

There is quite good documentation though:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


Paul

---

### Post by dino99 on 2010-05-09
look at 40_custom into the Grub 2 Guide below

---


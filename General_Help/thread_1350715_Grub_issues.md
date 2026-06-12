---
title: "Grub issues"
date: 2009-12-09
forum: General Help
---

### Post by untappedpilot2 on 2009-12-09
I get this error message from grub every time I try to boot into Ubuntu.

GNU GRUB version 1.97 beta4
[minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]
sh:grub> 

the fix is : 

1) sh:grub>insmod ntfs
2) sh:grub>set root=(hd0,1)
3) sh:grub>loopback loop0 /ubuntu/disks/root.disk
4) sh:grub>set root(loop0)
5) sh:grub>linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk
6) sh:grub>initrd /boot/initrd.img-2.6.31-15-generic
7) sh:grub>boot

However it is tedious to do this every time I want to boot Ubuntu. How can I make these changes permanent? I have Ubuntu installed through WUBI and this error began when I updated from 2.6.31-14 to 2.6.31-15

---

### Post by Leppie on 2009-12-09
try the following:
```
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by Leppie on 2009-12-12
so did you solve this issue?

---


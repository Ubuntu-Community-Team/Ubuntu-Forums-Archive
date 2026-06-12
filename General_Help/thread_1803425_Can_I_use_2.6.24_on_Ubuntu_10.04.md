---
title: "Can I use 2.6.24 on Ubuntu 10.04"
date: 2011-07-13
forum: General Help
---

### Post by knightraj on 2011-07-13
hi,
I am trying to boot from kernel 2.6.24.6 in Ubuntu 10.04, I get the error

"Gave up waiting for root device. Common problems:
- Boot args
- check rootdelay= ...
- check root= ...
- missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/<my-drive-uuid> does not exist. Dropping to a shell!

BusyBox Built In Shell ...
(initramfs)

What could be done?? Please help.. 
Thank You

---

### Post by dino99 on 2011-07-13
why such a request for an oldish kernel ? Might need to compile it as the actual distro packages have been updraded (gcc & libs).

---

### Post by knightraj on 2011-07-13
I have compiled and installed in the normal way, but when I try to boot from my grub, i get the error mentioned above..

---

### Post by knightraj on 2011-07-13
Can there a problem due to initrd and initramfs ???

---

### Post by Gyokuro on 2011-07-13
Mount root with the explicit device name (/dev/sda1). If I remember correct UUID support was a patched in thing.

---


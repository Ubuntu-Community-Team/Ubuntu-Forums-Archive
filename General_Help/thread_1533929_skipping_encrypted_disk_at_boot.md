---
title: "skipping encrypted disk at boot?"
date: 2010-07-18
forum: General Help
---

### Post by metalfan_ on 2010-07-18
Hi,

ive managed to screw up an encrypted disk experiment, basically at boot i get ask to enter my password which i lost.
only a data partition is encrypted, the linux system is unecrypted.

however, the skip option thats presented that should work via S does not work. every key in input adds one * behind the password prompt.
the password prompt changes from white to red though. as if in the white phase you should be able to skip.

im to lazy at the moment to swap the drive and comment the drive in fstab
i already booted in single, but still the mount occours. is there another way to get the system booting?


ubuntu server 10.04

---

### Post by Zorgoth on 2010-07-18
Boot from a live CD and edit /etc/fstab.

---


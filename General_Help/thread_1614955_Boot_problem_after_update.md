---
title: "Boot problem after update"
date: 2010-11-06
forum: General Help
---

### Post by Stuie on 2010-11-06
Hi guys got a problem after running updates on my 10.10 install

PC doesnt boot at all gets to loading OS then just powercycles.

UBUNTU is installed on a 2 disk raid0 array which seems to have changed. It used to run /dev/dm-1 for the root and /dev/dm-2 for the swap

Ive booted to a live cd and it now shows /dev/dm-2 for the root disk and -3 for the swap so im guessing grub is failing. Unfortunately I cant seem to get the device to mount and I fear im going to have to reinstall to fix this.

Any ideas guys?

---

### Post by linux-hack on 2010-11-06
You can simply reinstall grub on the root partition with :

Take a look at this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

An please use the search option of the forum.. There are a lot of posts like this one.

---

### Post by dino99 on 2010-11-06
which kind of raid is used ?

[http://ubuntuforums.org/showthread.php?t=1521566](http://ubuntuforums.org/showthread.php?t=1521566)

---

### Post by Stuie on 2010-11-06
it was raid0

and you cant simply reinstall grub on the root partition if its not mountable from a live cd

---

### Post by Rubi1200 on 2010-11-06
Also that link is from 2006 and is only relevant for legacy-GRUB. Ubuntu uses GRUB2 from version 9.10 onwards.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---


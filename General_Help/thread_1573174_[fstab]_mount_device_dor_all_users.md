---
title: "[fstab] mount device dor all users"
date: 2010-09-12
forum: General Help
---

### Post by Roman-K on 2010-09-12
OS: Ubuntu 10.04 (in VirtualBox virtual machine)

I have no idea how to mount a device for all users. I tried everything and can mount it only for root.
I'm trying to mount shared device in VirtualBox virtual machine.

I added record in `fstab` file:
shared   /mnt/shared   vboxsf   rw   0   0

I got /mnt/shared permissons: drwx------

I've tried to add options 'rw,user' in fstab, but the option 'user' is not supported by mount program in my system.

---

### Post by sisco311 on 2010-09-13
Hi and welcome to the forums!

You can set the owner, group, file and directory permissions with the *uid, gid, fmask, dmask* options. i.e.:
```
shared  /mnt/shared  vboxsf  rw,gid=**plugdev**,dmask=007,fmask=117  0  0
```
sets read/write permissions for the **plugdev** group.

---


---
title: "vmbuilder execscripts"
date: 2011-08-25
forum: General Help
---

### Post by ldg on 2011-08-25
Hello,

I'm trying to write an execscript for vmbuilder which copies /boot/vmlinuz* and /boot/initrd* from the vmbuilder image and places in my home directory. 

Can someone please help me?

I've tried a few things but none have worked so far.

I was thinking it would just be something like

cp $1/boot/vmlinuz(chroot $1 uname -r) ~

or

cp -r $1/boot ~

Any help would be greatly appreciated. Thanks in advance!

---

### Post by ldg on 2011-09-07
bump

---

### Post by ldg on 2011-09-19
Anyone please?

---


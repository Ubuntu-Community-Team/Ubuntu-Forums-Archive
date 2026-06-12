---
title: "How to add pcbsd to the grub bootloader?"
date: 2009-11-24
forum: General Help
---

### Post by JigglyWiggly_ on 2009-11-24
Ok so, pcbsd* is on /dev/sda5, and I have done sudo update-grub2, and it doesn't detect...

How can I add pcbsd to grub2? I mean with grub1 I could, but I have no idea how to do it with the stupid new grub system. Thanks in advance.

---

### Post by JigglyWiggly_ on 2009-11-25
help please...

---

### Post by JigglyWiggly_ on 2009-11-25
Also how do I make grub show no matter what? Right now it just passes it.
EDIT: I just installed win7 on a differnet partion and did grub-update now it pops up as expected. But I want pcbsd to show up!

---

### Post by Libertino on 2010-02-02
Hello all,

I would like to use PC-BSD, too, on my multi-boot system together with Ubuntu 9.10 Ubuntu 8.04, Sidux and Windows. Everything ist in the start-up menu but pc-bsd. I think, the problem is in the special way BSD-systems use "slices" and partitions. Is there still any way to run PC-bsd 8.0 from grub2?

Please help


CHeers 

Libertino

---

### Post by rnerwein on 2010-02-02
hi
you are running grub2 you can try to modify your /etc/grub.d/40_custom
see: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) for further information.
i got a similar problem with solaris 10 on a second hard drive. but i am using the good old boot loader with menu.lst  (just edit it via vi)
i  insert:
### don't touch this line - insert by richi solaris on hdb ###
title solaris 10
    rootnoverify (hd1,1)
    chainloader +1

this causes grub to call the solaris grub boot loader - and it works for me
ciao

---


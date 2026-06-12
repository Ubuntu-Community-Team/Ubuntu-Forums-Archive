---
title: "old kernels in 9.10"
date: 2009-12-07
forum: General Help
---

### Post by jjpm1 on 2009-12-07
Guys,

I've been taking a look at some of the advice given in these forums (here for instance > [http://ubuntuforums.org/showthread.php?t=1333120&highlight=uninstalling+kernels](http://ubuntuforums.org/showthread.php?t=1333120&highlight=uninstalling+kernels)) but none seem to deal with my problem.

I've an old kernel (or at least Grub and the terminal tell me so), a 9.04 2.6.28.something. Running **uname -r **shows I'm running 2.6.31.16, which is fine, but Synaptic doesn't recognise I've an old 9.04 kernel. A sudo update-grub2 gives me:

> Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found Ubuntu 9.10 (9.10) on /dev/sdb5Is the fact the 9.04 is on /dev/sdb5 mean anything? I'm not sure what's going on; any ideas? Plus, the reason I say 9.04 and, not 9.10 as the terminal does, is that Grub tells me it's a 9.04.

Many thanks,

Joe

---


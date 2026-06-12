---
title: "patched Kernel + USplash + modules?"
date: 2006-03-18
forum: General Help
---

### Post by Bazon on 2006-03-18
Hello!

I patched my Kernel according to [this HowTo in the Wiki.](https://wiki.ubuntu.com/ViaEpiaDriHowto)

[SIZE="1"](
Abstract so you don't have to read it:
```
$ patch -p1 < ../patch-2.6.12.3-epia
$ make gconfig
$ make
$ sudo make modules_install
$ sudo cp arch/i386/boot/bzImage /vmlinuz
$ gedit nano /boot/grub/menu.lst
```
...
but without initrd for the new kernel
+backup old stuff
)[/SIZE]

Mainly it worked (it boots and direct rendering + special CPU support enabled...), but however, I got some questions left:

_**1. USplash:**_
USplash isn't working anymore with my patched Kernel.
**How can I use Usplash with a patched kernel?**
Was something wrong in [my .config](http://home.arcor.de/bazonbloch/files/logs/Epia2.6.12.config)?
I really would be happy if  could get back my USplash in the patched (=better) Kernel, too.
_**2. Modules / influence on the other kernel:**_
After using that patched kernel, loading the regular normal kernel had some problems, too:
[list=a][*]USplash didn't work for the regular kernel, too.
[*]So I could read while booting: The Kernel tried to load the wrong moduls:
It tried to load in /lib/modules/2.6.12.3-epia (the directory for the patched kernel) instead of /lib/modules/2.6.12-10-386 (the regular directory for the standard kernel.) 
Did I made something wrong during *make modules_install *? [/list]
However, this problems disappeared for the regular kernel as I made the automatic update yesterday (from update notifier...).
*[The patched kernel worked after I replaced the symlink vmlinuz by the patched kernel again...]*
But I would like to be able to use patched kernels witout having these influences on the normal kernel.
**So how can I avoid these problems when patching kernel?**

Thanks,
Bazon

---


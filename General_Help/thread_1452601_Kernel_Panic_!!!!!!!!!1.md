---
title: "Kernel Panic !!!!!!!!!1"
date: 2010-04-12
forum: General Help
---

### Post by pczafer on 2010-04-12
I was trying to compile Kernel 2.6.33.2 

I used fallowing commands without any error!

make menuconfig
make-kpkg clean
fakeroot make-kpkg --revision=custom.1.0 kernel_image

dpkg -i kernel-image-2.6.33.2_custom.1.0_i386.deb

mkinitrd -o /boot/initrd.img-2.6.33.2 2.6.33.2
changed the menu.lst configuration for the new Kernel

then after restart with new kernel a got this error.

[IMG]http://i44.tinypic.com/zv4gfr.jpg[/IMG]

Can anybody tell me what i have done wrong??

---

### Post by pczafer on 2010-04-12
NOBODY have any idea?????????

---

### Post by prodigy_ on 2010-04-12
Less exclamation marks, please. 

Now let's start from the beginning: what exactly do you want to achieve by switching to a Mainline kernel? Are you sure that there's no simpler solution? If yes, there's a [Mainline kernel PPA](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds). You can just grab a .deb package from there.

---

### Post by pczafer on 2010-04-12
> **prodigy_ said:**
> Less exclamation marks, please. 

Now let's start from the beginning: what exactly do you want to achieve by switching to a Mainline kernel? Are you sure that there's no simpler solution?

I am trying to do this only for learning purposes. 

I can still boot up from my old kernel but when i try to boot from new one, im getting that error in my first post?

---

### Post by prodigy_ on 2010-04-12
I'm not very familiar with kernel compiling but I'm pretty sure that devfs support was completely dropped from 2.6 quite some time ago. You need to use udev instead.

Try [this HOWTO](http://www.disaggregate.com/blog/technicalweblog/archives/000012.html).

---


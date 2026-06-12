---
title: "safely removing self-compiled kernels"
date: 2009-12-13
forum: General Help
---

### Post by FreezWay on 2009-12-13
I installed a kernel from kernel.org tweaked it a little and broke my video driver. I can boot the generic kernel fine so its not urgent, but how do I remove the old kernels? they aren't in apt. I followed the directions here: [http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html](http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html)

i just dont want my hd to fill up with broken kernels.

---

### Post by juancarlospaco on 2009-12-13
sudo apt-get autoremove && sudo apt-get autoclean

---

### Post by FreezWay on 2009-12-13
they aren't in apt

---

### Post by Some Penguin on 2009-12-13
1) find the grub configuration file, and remove references to that kernel
2) reinstall grub
3) remove /lib/modules/that-kernel-version
    remove the kernel image from wherever you put it (probably /boot)
    remove the kernel source and build tree (probably somewhere in /usr/src)

Nothing complicated about it.  It won't leave random files all over the place.

---

### Post by FreezWay on 2009-12-13
thanks

---


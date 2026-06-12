---
title: "Compiled a new kernel - but it has a Kernel Panic / Not Syncing error"
date: 2010-04-18
forum: General Help
---

### Post by tom66 on 2010-04-18
I've compiled a new kernel for my system in an attempt to fix a bug with radeon power saving. I compiled v2.6.34, which is "mainline". However, it will not boot; it has a kernel panic trying to mount root fs. How can I fix this? I had added root=UUID=8cd7b... to the boot string but it still fails.

Thanks! :)

---

### Post by Felix-the-Cat on 2010-04-20
There is no way of anyone knowing how to fix it without knowing how you complied the kernel. The thing with compiling you own kernel is that its yours alone - and its the only one in the world like it. So I would try recompiling. I should probably ask are you really compiling your own kernel or is it a package coming from somewhere. Let us know a little more about what exactly you are doing and where it is coming from.

---

### Post by klemes on 2010-04-20
Better show us your /etc/fstab,but it is most likely a non-running kernel so you most probably will have to recompile it with the correct options in it's configuration file.
It's rather common when you edit a lot of thing in the configuration file.
You say you edited the grub.cfg file yourself.Did not you use make-kpkg command to create a new linux-image package which when installed with dpkg -i it will update correctly your grub.cfg file?I think this is the best practice.And did you remeber to make a initrd image files for the kernel modules?
I suggest you recompile your kernel using make-kpkg this time .A good guide is the following:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---


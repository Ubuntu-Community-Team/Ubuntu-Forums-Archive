---
title: "Xubuntu 8.04: Error installing 2570 wireless drivers."
date: 2011-04-16
forum: General Help
---

### Post by SilentlyLoud on 2011-04-16
Other posts have been super helpful, i know my way around linux enough to basically most of the time figure out my own problems. but im lost this time 

I referred to this post about installing the driver
[http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)

Once i go to /module and use the command "sudo make" i get this output

[B]lynne@lynne-desktop:/usr/src/rt2570-1.1.0-b1/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-29-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-29-generic'
rt2570.ko failed to build!
make: *** [module] Error 1[/B]


Ive tried resintalling needed packages. so far they are all there. im completely lost on what to do if you need anymore information ask. im quite new to this ill do the best i can.

---


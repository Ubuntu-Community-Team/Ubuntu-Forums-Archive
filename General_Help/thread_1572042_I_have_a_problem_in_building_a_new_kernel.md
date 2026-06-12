---
title: "I have a problem in building a new kernel"
date: 2010-09-10
forum: General Help
---

### Post by thot135 on 2010-09-10
Hi. I just started to use the Ubuntu 10.4
I wanted to build a new kernel but the problem occurred 
when I tried using the command named "make bzImage"

The following is error information.
-----------------------------------
root@thoth-laptop:/usr/src/linux-headers-2.6.32-24# make xconfig
  CHECK   qt
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/x86/Kconfig
#
# using defaults found in /boot/config-2.6.32-24-generic
#
#
# configuration written to .config
#
root@thoth-laptop:/usr/src/linux-headers-2.6.32-24# make dep
scripts/kconfig/conf -s arch/x86/Kconfig
*** Warning: make dep is unnecessary now.
[B]root@thoth-laptop:/usr/src/linux-headers-2.6.32-24# make bzImage
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[1]:  *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make: *** [prepare0] Error 2[/B]
--------------------------------
I tried some ways again and again but I couldn't find the answer.
I hope someone could help me to solve this problem.
I will wait for your answer. Thank you!

---

### Post by Gunman1982 on 2010-09-10
> **thot135 said:**
> 
root@thoth-laptop:/usr/src/linux-headers-2.6.32-24# 

You are trying to build the kernel by compiling the headers? 
Download the kernel source (either package or the vanilla kernel from kernel.org), the dev/header package is only usefull for other programms who need the kernel headers to compile.

---

### Post by thot135 on 2010-09-10
Oh, I'm ashamed what I have done....
I'll try again. Thank you for your answer! 
:)

---


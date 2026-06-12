---
title: "Is there any already-compiled 32-bit, Intel Core2 supporting kernel for karmic?"
date: 2010-02-09
forum: General Help
---

### Post by dxxvi on 2010-02-09
I don't dare to recompile the kernel :(

Thank you.

---

### Post by lisati on 2010-02-09
The "standard" 32-bit kernel should work. I'm using a 32-bit verion of Ubuntu on a cpu that identifies itself as Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz"  Have a look here: [http://ubuntu.com/getubuntu](http://ubuntu.com/getubuntu)

---

### Post by efflandt on 2010-02-09
Look through **dmesg | less** in a terminal after you boot (from install CD or a system) and it should automatically show it using both cpu's.  Or System > Administration > System Monitor should show 2 curves for CPU History.

---

### Post by dxxvi on 2010-02-09
Yeah, I know that with a standard kernel both cores of the cpu are utilized. If you ever try to re-compile the kernel, you'll see that the i386 cpu family option is checked but not the core2/new Xeon cpu family. The kernel I need is the one compiled with that core2/new Xeon checked (not sure if I can see any performance improvement :p) Does anybody see anything different when switching from i386 to core2/new Xeon?

Thank you.

---

### Post by mushwars on 2010-02-09
> **dxxvi said:**
> I don't dare to recompile the kernel :(
Why is everyone so scared of compiling their kernel?

```
cd /usr/src/linux
make menuconfig
make && make modules_install
cp arch/i386/boot/bzImage /boot/<KERNEL NAME>
```then edit grub.

Its good experience, I do it from time to time when I add hardware or what ever.

EDIT: hit the '/' key in menuconfig to search for something like your processor.

EDIT2: it is in "processor type and features" off the main menu.
```
Symbol: MCORE2 [=n]                                                     &#9474;  
  &#9474; Prompt: Core 2/newer Xeon                                               &#9474;  
  &#9474;   Defined at arch/x86/Kconfig.cpu:256                                   &#9474;  
  &#9474;   Depends on: <choice>                                                  &#9474;  
  &#9474;   Location:                                                             &#9474;  
  &#9474;     -> Processor type and features                                      &#9474;  
  &#9474;       -> Processor family (<choice> [=y])        
```

---

### Post by dxxvi on 2010-02-09
> **mushwars said:**
> Why is everyone so scared of compiling their kernel?

```
cd /usr/src/linux
make menuconfig
make && make modules_install
cp arch/i386/boot/bzImage /boot/<KERNEL NAME>
```then edit grub.

Its good experience, I do it from time to time when I add hardware or what ever.

EDIT: hit the '/' key in menuconfig to search for something like your processor.

EDIT2: it is in "processor type and features" off the main menu.
```
Symbol: MCORE2 [=n]                                                     &#9474;  
  &#9474; Prompt: Core 2/newer Xeon                                               &#9474;  
  &#9474;   Defined at arch/x86/Kconfig.cpu:256                                   &#9474;  
  &#9474;   Depends on: <choice>                                                  &#9474;  
  &#9474;   Location:                                                             &#9474;  
  &#9474;     -> Processor type and features                                      &#9474;  
  &#9474;       -> Processor family (<choice> [=y])        
```

:) I can see that you're from gentoo, so compiling stuff is what you like, right? Actually, I can compile a kernel, but there are new kernels all the time and I get tired of compiling kernels (but I still want to have the latest code on my machine :) ). I intended to switch to Arch, but after a few days playing with Arch, I realized that it would take me weeks to make Arch as beautiful/useful as Ubuntu.

---


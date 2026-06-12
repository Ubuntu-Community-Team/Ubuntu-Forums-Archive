---
title: "modules.dep fatal loading error"
date: 2009-11-08
forum: General Help
---

### Post by FoxMcCloud on 2009-11-08
I'm trying to download and compile a newer kernel version for use with ubuntu 9.04. I'm doing it as an exercise, so while I know I can use deb packages, I want to do it the manual way. I got it from kernel.org, configured it, make bzImage, modules, modules_install and used make install and KGrub Editor to add it to grub. However, when I try to boot it, I get 5 instances of the following error:

FATAL: Could not load /lib/modules/<kernel version>/modules.dep: No such file or directory

Then it waits for root fs for a while, fails and jumps to BusyBox with a (initramfs) prompt.. Any ideas?

---

### Post by hal8000 on 2009-11-08
> **FoxMcCloud said:**
> I'm trying to download and compile a newer kernel version for use with ubuntu 9.04. I'm doing it as an exercise, so while I know I can use deb packages, I want to do it the manual way. I got it from kernel.org, configured it, make bzImage, modules, modules_install and used make install and KGrub Editor to add it to grub. However, when I try to boot it, I get 5 instances of the following error:

FATAL: Could not load /lib/modules/<kernel version>/modules.dep: No such file or directory

Then it waits for root fs for a while, fails and jumps to BusyBox with a (initramfs) prompt.. Any ideas?



Youre using an old howto.
After configuring the kernel the steps are:
make
make install

make install automatically creates modules in /lib/modules/2.6.xxx where xx is kernel version.

However you also have to create a new initramfs unless you have explicitly compiled all modules required to boot your system into your new kernel.
I would start again but this time clean your kernel config with
make mrproper

and then copy the current ubuntu config as .config into your new /usr/src/linux directory and configure the kernel again.

You must keep your old kernel and manually link to your new kernel and initramfs (if using initramfs) by manually editing grub to be sure you can still boot.

---

### Post by FoxMcCloud on 2009-11-09
I seem to be using an outdated how to indeed. Can you point me to a guide that's suitable for ubuntu 9.04?

---


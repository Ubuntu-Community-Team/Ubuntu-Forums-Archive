---
title: "Kernel panic - not syncing : VFS : Unable to mount root fs (on a custom kernel)"
date: 2010-05-02
forum: General Help
---

### Post by kostaskoukos on 2010-05-02
Ubuntu 10.04 / Kubuntu 10.04
Kernel panic - not syncing : VFS : Unable to mount root fs on unknown - block (0,0).

I am trying to built a custom kernel using either the ubuntu source or a kernel.org
distribution of the latest 2.6.32 kernel. In both cases when i try to boot the new kernel
i get the above message. The .config file used is the default config of the generic kernel
ships with Ubuntu 10.04 with some modifications. I have patched the kernel with
perfctr module and for the kernel with ubuntu patches i have unchecked all third
party modules except from the aufs modules and the compcache modules. 
The reason is that the kernel could not compile all of these modules 
(so i disabled some not needed).

I' ve tried to edit the /boot/gub/grub.cfg manually for the new kernel entries but
without any luck. The same with the grub scripts hacking.

I 've made this procedure hundreds of times in the previous releases in many different
system configurations without any problems. I also noticed that the kernels produced 
by kpkg for this distribution are very small in size (~33 M).
What i need to built a working custom kernel in this distribution?
(I really need perfctr installed!!!).
kernel config file is attached as well as grub.cfg

Thanks in advance.

---

### Post by kostaskoukos on 2010-05-09
It seems to be a known bug :

Refer to 

[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/546277](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/546277)

---


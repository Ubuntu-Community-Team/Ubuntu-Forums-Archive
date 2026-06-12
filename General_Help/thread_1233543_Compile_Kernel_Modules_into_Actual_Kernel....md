---
title: "Compile Kernel Modules into Actual Kernel..."
date: 2009-08-06
forum: General Help
---

### Post by icanfly0307 on 2009-08-06
Hi all, I was just wondering... is it possible to build kernel modules directly into the kernel itself? I have a kernel module (i810fb) that i want to build into the kernel statically. My graphics card (intel i815) doesn't support vesafb, so I'm forced to use the i810fb that is compiled into the kernel as a module. However, the i810fb module doesn't get loaded at boot time because of a bug... . Does anyone know how or if I can compile modules into the actual kernel itself without recompiling the whole entire kernel? Thanks.

---

### Post by frikker on 2009-09-23
If you use the 'old' way of configuring a kernel, you can do this.  Try going into the top directory and typing 'make menuconfig'... YMMV

---


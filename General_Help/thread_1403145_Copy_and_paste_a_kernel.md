---
title: "Copy and paste a kernel"
date: 2010-02-09
forum: General Help
---

### Post by ant2ne on 2010-02-09
Supposing I succeed at rolling a kernel (work in progress), How can I transplant that kernel from one box to another? The boxes are of similar design and model, and may only be different in CPU freq and possible vga devices.

---

### Post by cariboo on 2010-02-10
I haven't compiled a custom kernel for years, but when I did, part of the process was to create a .deb. Once you're done, it should be located in /usr/src.

---

### Post by Satoru-san on 2010-02-10
> **ant2ne said:**
> Supposing I succeed at rolling a kernel (work in progress), How can I transplant that kernel from one box to another? The boxes are of similar design and model, and may only be different in CPU freq and possible vga devices.

The whole purpose of compiling your own kernel is to make it work on your box without having stuff you dont need.

Basically you can use the default kernel that comes with ubuntu just do this.

```
cd /usr/src/linux
make menuconfig
---change settings---
make && make modules_install
cp arch/i386/boot/bzImage /boot/<IMAGE NAME>
```

dont forget to add new [m] to the /etc/modules.autoload.d/kernel-2.6

It is easy enough to do it separately on each machine, dont share kernels its unsanitary.

---


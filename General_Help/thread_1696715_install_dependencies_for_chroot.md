---
title: "install dependencies for chroot?"
date: 2011-02-27
forum: General Help
---

### Post by kty1104 on 2011-02-27
hello
there is ubuntu img which is made by rootstock
(to run in ARM architecture)
but I can't chroot the img
many people say this is dependencies problem
if I do not have the loader and/or shared libraries available to make,

I have ubuntu img and I can't chroot the img
so I have no idea how to add or install
such a libraries and loader

I dont know how to install them(below)
$ ldd /usr/bin/make
    linux-vdso.so.1 =>  (0x00007fff95fff000)
    librt.so.1 => /lib/librt.so.1 (0x00007fc97d557000)
    libc.so.6 => /lib/libc.so.6 (0x00007fc97d1f6000)
    libpthread.so.0 => /lib/libpthread.so.0 (0x00007fc97cfd9000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fc97d761000)

could somebody tellme what I have to do?
thanks in advanced
Regards.
Taeyun

---


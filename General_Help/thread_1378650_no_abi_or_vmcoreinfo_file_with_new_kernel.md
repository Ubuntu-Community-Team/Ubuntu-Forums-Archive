---
title: "no abi or vmcoreinfo file with new kernel"
date: 2010-01-11
forum: General Help
---

### Post by hart02 on 2010-01-11
After compiling my kernel and installing the created debs. Some how i dont have the vmcoreinfo or abi files for the new kernel.
/boot looks like this

```
System.map-2.6.31-14-generic  initrd.img-2.6.31-17-generic
System.map-2.6.31-17-generic  initrd.img-2.6.31-17-generic.bak
System.map-2.6.32-candela     initrd.img-2.6.32-candela
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-17-generic         vmcoreinfo-2.6.31-14-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.31-17-generic
config-2.6.31-17-generic      vmlinuz-2.6.31-14-generic
config-2.6.32-candela         vmlinuz-2.6.31-17-generic
grub                          vmlinuz-2.6.32-candela
initrd.img-2.6.31-14-generic

```

Really i just want to know if create these files and if so, how?

---

### Post by hart02 on 2010-01-11
Ok then. Guess there is no way to create these files.So now what I just give up on compiling custom kernels?

---

### Post by ppww on 2010-03-12
I was wondering the same thing, after using the process described at [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

Finally arrived at
```
makedumpfile -g /boot/vmcoreinfo-2.6.31.9-custom -x /usr/src/linux/vmlinux
```
(Fix the kernel version/abi/flavor to that of your own, and the path to the unstripped, uncompressed vmlinux in your kernel build directory, if not /usr/src/linux.)

I haven't seen any way of generating the abi file though.  Even what is supposedly a new/improved process for building custom ubuntu kernels, found at [http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/]("http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/"), simply copies the abi from the previous version, so I just did a
```
cp /usr/src/linux/debian.master/abi/2.6.31-19.56/amd64/generic /boot/abi-2.6.31.9-custom
```

---


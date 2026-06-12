---
title: "Compiling my own kernel: undefined reference to `populate_rootfs_wait'"
date: 2012-06-11
forum: General Help
---

### Post by Cheesehead on 2012-06-11
I'm compiling my own 12.04 kernel (based on 3.2.0-23.36). It's meant for a VIA Epia 5000-L motherboard with a Via C3 processor. Both are 10 years old, so cannot handle the current stock kernels with pae and cmov.

Since it's for a specific machine, I thought I'd take the easy route and compile in only the hardware I need, skip the modules and eliminate the initrd. I did successfully compile a kernel for Debian 6.0.3 just that way on the same machine. The compile is running on the same hardware the finished kernel will run on.

The current 12.04 custom compile errors out looking for a reference to populate_rootfs_wait. Here's what it looks like

```
...blah...blah...
  AS      arch/x86/lib/putuser.o
  AS      arch/x86/lib/rwlock.o
  AS      arch/x86/lib/rwsem.o
  CC      arch/x86/lib/string_32.o
  CC      arch/x86/lib/strstr_32.o
  AS      arch/x86/lib/thunk_32.o
  CC      arch/x86/lib/usercopy.o
  CC      arch/x86/lib/usercopy_32.o
  AR      arch/x86/lib/lib.a
  LD      vmlinux.o
  MODPOST vmlinux.o
  GEN     .version
  CHK     include/generated/compile.h
  UPD     include/generated/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `kernel_init':
main.c:(.init.text+0x268): undefined reference to `populate_rootfs_wait'
fs/built-in.o: In function `do_coredump':
(.text+0x56b8): undefined reference to `populate_rootfs_wait'
lib/lib.a(kobject_uevent.o): In function `kobject_uevent_env':
kobject_uevent.c:(.text+0x501): undefined reference to `populate_rootfs_wait'
drivers/built-in.o: In function `uvesafb_exec':
uvesafb.c:(.text+0x7b6bc): undefined reference to `populate_rootfs_wait'
net/built-in.o: In function `br_stp_set_enabled':
(.text+0xfd326): undefined reference to `populate_rootfs_wait'
net/built-in.o:(.text+0xfd3d4): more undefined references to `populate_rootfs_wait' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-3.2.0'
make: *** [debian/stamp/build/kernel] Error 2
root@mini-deb6:/usr/src/linux# 

```

The only reference I can find to that variable is some Ubuntu kernel dev discussion about introducing a patch with this variable to let the rootfs stabilize before mounting the system and transferring control fron initrd to init.

Does this mean that Ubuntu *requires* an initrd?

Has anyone ever run across this kind of error?

Can I fix this with a kernel setting?
Or should I use a vanilla kernel source instead of an Ubuntu kernel source?

Enlightenment and advice welcome...

---

### Post by Cheesemill on 2012-06-11
Does the non-PAE Ubuntu kernel from the repositories work with your machine?
If so it would be a much easier option than compiling your own.

---

### Post by Cheesehead on 2012-06-11
> **Cheesemill said:**
> Does the non-PAE Ubuntu kernel from the repositories work with your machine?
If so it would be a much easier option than compiling your own.

Great question! Sadly, it does not.

The stock Ubuntu kernel includes three elements, pae, cmov, and cx8. The non-pae kernel solves only one of those. Using a [FONT="Courier New"]--arch i486[/FONT] version solves the other two. Debian does have a 3.2.0-486 kernel in sid, and I could try it...but is Ubuntu 12.04 likely to work using it?

I'm doing this to learn - it's an experimental system.

Right now it looks like I have three options:
1) Go with the Debian kernel.
2) Try to solve this error.
3) Back up and compile a kernel from Ubuntu source that only removes those three services (instead of almost everything).

---

### Post by SKxF3ZdW on 2012-06-17
I had this problem when disabling the CONFIG_BLK_DEV_INITRD kernel config setting, apparently there are a lot dependencies on populate_rootfs_wait() in init/initramfs.c

---


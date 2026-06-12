---
title: "mkinitrd"
date: 2010-02-24
forum: General Help
---

### Post by osmorphyus on 2010-02-24
is the MKINITRD command available in the current linux kernel?

i have a DSL installed on a loopback FS.  when i attempt to upgrade the kernel to 2.6.18 kernel, my system halts at kernel panic stating, "cannot find the loopback file system"

my initrd and syslinux bootloader is properly configured and pointing to where the LB FS is at, and the 2.4.x kernel boots just fine.

i have been wondering for a long time now if loopback support is whats keeping me unable to boot this newer kernel, but i dont have enough knowledge about it all, yet.

i have just read that kernels < 2.6 only support loopback capability. 

if this is the case, is there any known method for booting a kernel 2.6.x based or higher from a LB FS?

---


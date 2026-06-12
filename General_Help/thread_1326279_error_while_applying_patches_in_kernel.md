---
title: "error while applying patches in kernel"
date: 2009-11-14
forum: General Help
---

### Post by tapas_mishra on 2009-11-14
I 

[LIST]
[*] Downloaded Kernel from [www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.29.2.tar.bz2]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.29.2.tar.bz2")
[*] Download Patches from [gentoo-xen-kernel.googlecode.com/files/xen-patches-2.6.29-6.tar.bz2]("http://gentoo-xen-kernel.googlecode.com/files/xen-patches-2.6.29-6.tar.bz2")
[*] Unpack into /usr/src/ and /usr/src/xen-patch
[*] Applied patches with  cd /usr/src/linux-2.6.29.2
[*] cat ../xen-patch/* | patch -p1
[/LIST]
then i have been getting  lot of error messages like this


The next patch would create the file include/xen/interface/hvm/save.h,
which already exists!  Assume -R? [n]

---

### Post by falconindy on 2009-11-14
That's not an error. What you have is a diff file which affects multiple files. The question you're being asked is "assume recursive?" However, because that can be a destructive and sometimes unwanted effect, the default response is no. If you're sure this is what you want to do, enter 'y' and it'll continue patching. Also, save yourself some keystrokes, use:
```
patch -Np1 -i ../xen-patch/*
```

---

### Post by tapas_mishra on 2009-11-14
Ok thanks a lot I answered yes to a lot of them is there a way to revert it back

---

### Post by tapas_mishra on 2009-11-14
All worked fine except one last error message 

patch: ../xen-patches/60002_linux-2.6.19-rc1-kexec-move_segment_code-x86_64.patch1: extra operand
patch: Try `patch --help' for more information.

---


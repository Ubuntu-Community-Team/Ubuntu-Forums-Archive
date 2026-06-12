---
title: "Recompile Kernel"
date: 2006-02-09
forum: General Help
---

### Post by littlespy on 2006-02-09
I was hoping someone could enlighten me.  I have an AMD64 processor, but I am running the i386 kernel.  I do not want to run 64-bit ubuntu, but I was wondering if I would gain any real performance gain by using the K7 kernel.  And if I would, would it be a large effort? Would it "break" lots of other software.

---

### Post by jcl on 2006-02-09
I have a Celeron and downloaded the 686 kernel from the repository, rebooted and everything went great... easy peasy... no recompile necessary...

Also check out: [http://www.ubuntuforums.org/showthread.php?t=85917&highlight=686+kernel](http://www.ubuntuforums.org/showthread.php?t=85917&highlight=686+kernel)

---

### Post by az on 2006-02-09
It will break nothing.

Install linux-k7 (use synaptic or any other package manager you like) and reboot.

Your done.

apt-cache show linux-k7

Package: linux-k7
Priority: optional
Section: restricted/base
Installed-Size: 48
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.12.16.1
Depends: linux-image-k7, linux-restricted-modules-k7
Filename: pool/restricted/l/linux-meta/linux-k7_2.6.12.16.1_i386.deb
Size: 22500
MD5sum: 688a76790be7658220c8b52e9c801f01
Description: Complete Linux kernel on AMD K7.
 This package will always depend on the latest complete Linux kernel available
 for AMD Duron/Athlon.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---


---
title: "tutorials on initramfs, building initrd.img"
date: 2012-01-08
forum: General Help
---

### Post by rafe_b on 2012-01-08
I'm feeling proud of myself having built and installed a kernel for the first time, today.  The main stumbling block, it turned out, was **initramfs**, or more precisely, the newly-created initrd.img-xxx file.

While I have a working kernel (i386, for Asus desktop) I'm still hazy on how to create the new initrd.img file.  The default version of this file, from the Ubuntu distribution (11.10) is around **12 MB** in size.  The first initrd.img that I created was** 2.6 MB** and failed to boot (I got dumped into Busybox.)  The next initrd.img that I created is **113 MB**.  This one allows a boot, though there's some garbage on the screen during the boot process.  I have a hunch the new initrd.img file contains every single module that got built by 'make modules_install'.  The command line I used was

update-initramfs -c -k 3.0.9

So -- I'm looking for any hints and tips on creating an initrd.img file on a current Ubuntu distribution, hopefully from user experience and not just something I've already found via google.  Thanks!

---


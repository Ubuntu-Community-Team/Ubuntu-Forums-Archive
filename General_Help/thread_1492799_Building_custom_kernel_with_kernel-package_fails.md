---
title: "Building custom kernel with kernel-package fails"
date: 2010-05-25
forum: General Help
---

### Post by robkey on 2010-05-25
Hi have been building custom kernels for successfully for a few years using make-kpkg from the kernel-package. Now it has started failing, even going back to older versions still fail. The source compiles fine but check the errors below.

It was invoked like this
sudo -i
make menuconfig  (did configuration)
make-kpkg clean
make-kpkg --initrd --revision=custom1.0 --append-to-version=-custom1.0 kernel_image kernel-headers

the error message I get at the end of the build is this

exec make -f /usr/share/kernel-package/ruleset/minimal.mk debian DEBIAN_REVISION=custom1.0  APPEND_TO_VERSION=custom1.0  V=1  INITRD=YES 
====== making target debian/stamp/conf/minimal_debian [new prereqs: ]======
This is kernel package version .
test -d debian             || mkdir debian
test ! -e stamp-building || rm -f stamp-building
WARNING: Couldn't open directory /usr/src/linux-source-2.6.26/debian/linux-image-/lib/modules/2.6.32-live1.0: No such file or directory
FATAL: Could not open /usr/src/linux-source-2.6.26/debian/linux-image-/lib/modules/2.6.32-live1.0/modules.dep.temp for writing: No such file or directory
make[2]: *** [_modinst_post] Error 1
make[2]: Leaving directory `/mnt/linux/src/linux-source-2.6.26'
make[1]: *** [debian/stamp/install/linux-image-] Error 2
make[1]: Leaving directory `/mnt/linux/src/linux-source-2.6.26'
make: *** [kernel_image] Error 2

the kernel source was 2.6.26, where does the 2.6.32-live1.0 string come from? 
Any help would be appreciated as I'm going nuts with kernel-package
Thanks,
  Rob Key

---

### Post by robkey on 2010-05-25
I have just tried it like this
make-kpkg --initrd --append-to-version=-custom1.0 kernel_image kernel-headers

and it bombs out after a successful compile with this error

  INSTALL debian/linux-image-/lib/firmware//yamaha/ds1e_ctrl.fw
  DEPMOD  
WARNING: Couldn't open directory /usr/src/linux-source-2.6.32/debian/linux-image-/lib/modules/2.6.32-custom1.0: No such file or directory
FATAL: Could not open /usr/src/linux-source-2.6.32/debian/linux-image-/lib/modules/2.6.32-custom1.0/modules.dep.temp for writing: No such file or directory
make[2]: *** [_modinst_post] Error 1

What is going on here?
Thanks Rob Key

---


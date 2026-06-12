---
title: "make-kpkg"
date: 2006-03-23
forum: General Help
---

### Post by p47 on 2006-03-23
Hello eveybody !

I hope you can help me because I've a problems with kpkg
Now I want to install the new kernel and I reading a tutorial in this site about recmpile the kernel but when I type in the console tith sudo or in root mode I got this message:

root@ubuntu:/usr/src/linux# make-kpkg clean
bash: make-kpkg: command not found
root@ubuntu:/usr/src/linux#
Why ?
Somebody can help me !
What can I do ?
Thank's a lot

---

### Post by Ramses de Norre on 2006-03-23
sudo apt-get install kernel-package

---

### Post by p47 on 2006-03-23
Thank's a lot 
Ramses de Norre
Now the command is ok but I have a question because when I type sudo make-kpkg clean ubuntu show me this:



```
root@ubuntu:/usr/src/linux# make-kpkg clean
/usr/bin/make -f /usr/share/kernel-package/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-2.6.16ck1'
test ! -f .config || cp -pf .config config.precious
test -f Makefile && \
            /usr/bin/make    ARCH=i386 distclean
make[2]: Entering directory `/usr/src/linux-2.6.16ck1'
  CLEAN   scripts/basic
  CLEAN   scripts/kconfig
  CLEAN   .config .config.old include/linux/autoconf.h .kernelrelease
make[2]: Leaving directory `/usr/src/linux-2.6.16ck1'
test ! -f config.precious || mv -f config.precious .config
test ! -f stamp-patch || /usr/bin/make -f /usr/share/kernel-package/rules unpatch_now
test -f stamp-building || test -f debian/official || rm -rf debian
# work around idiocy in recent kernel versions
test ! -e scripts/package/builddeb.dist || \
            mv -f scripts/package/builddeb.dist scripts/package/builddeb
test ! -e scripts/package/Makefile.dist || \
            mv -f scripts/package/Makefile.dist scripts/package/Makefile
rm -f modules/modversions.h modules/ksyms.ver debian/files conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches debian/buildinfo stamp-build stamp-configure stamp-source stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-buildpackage stamp-libc-kheaders stamp-debian stamp-patch stamp-kernel-configure
rm -rf debian/tmp-source debian/tmp-headers debian/tmp-image debian/tmp-doc
make[1]: Leaving directory `/usr/src/linux-2.6.16ck1'
root@ubuntu:/usr/src/linux#


```

Why ?
make[1]: Leaving directory `/usr/src/linux-2.6.16ck1
Help me !!!!!!!!!

---

### Post by Barrakketh on 2006-03-23
You could consider reading the manpage for make-kpkg or at least learn how build targets work.
> [indent]**TARGETS**
[indent]**clean**     Cleans the kernel source directory of all  files
              created  by  target build, and runs a make dist&#8208;
              clean. (Please look at a Linux  kernel  Makefile
              for details).  Please note that although we take
              care of the list of current kernel configuration
              contained   in   the   file  .config,  the  file
              include/linux/autoconf.h is not preserved.  This
              target  should  not  be combined with other tar&#8208;
              gets, since make-kpkg reads in all  data  before
              running  any  target,  so the subsequent targets
              shall be run with the old data, which may not be
              what you want.[/indent][/indent]


If you've ever ran "make clean" or "make dist-clean" while building nearly any other program that makes use of automake it would all look very familiar.  What you witnessed is normal.

---


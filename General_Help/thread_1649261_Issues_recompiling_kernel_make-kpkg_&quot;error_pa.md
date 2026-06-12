---
title: "Issues recompiling kernel: make-kpkg &quot;error: package not in control info&quot;"
date: 2010-12-20
forum: General Help
---

### Post by Ibidem on 2010-12-20
Well, 
I've got a Thinkpad X100e, with a Realtek 8172 wireless n chipset (reported as 8191SE/8192SE)--a chip that has very limited functionality in Linux right now.  From what I've read, some improvements for Realtek wireless n support are scheduled for kernel 2.6.38--which is currently still future.
So I thought I'd try recompiling with a copy of the wireless-testing tree, which should have the code if it exists yet.
After running make localmodconfig and make gconfig (to tune it and get the Realtek drivers), I tried running make-kpkg:
```
 CONCURRENCY_LEVEL=4 make-kpkg --initrd --us --uc --append-to-version=rtl-dec19 kernel-image kernel-headers
```

The compile went perfectly, and completed in about 40-50 minutes.
However, make-kpkg died  when attempting to package the compiled kernel ($SRC means the source directory):
```
        ./debian/templates.l10n   > ./debian/templates.master
install -p    -o root -g root  -m  644 ./debian/templates.master $SRC/wireless-testing/debian/linux-image-2.6.37-rc6rtl-dec19-wl/DEBIAN/templates
dpkg-gencontrol -DArchitecture=i386 -isp             \
                        -plinux-image-2.6.37-rc6rtl-dec19-wl -P$SRC/wireless-testing/debian/linux-image-2.6.37-rc6rtl-dec19-wl/
dpkg-gencontrol: error: package linux-image-2.6.37-rc6rtl-dec19-wl not in control info
make[2]: *** [debian/stamp/binary/linux-image-2.6.37-rc6rtl-dec19-wl] Error 255
make[2]: Leaving directory `$SRC/wireless-testing'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.37-rc6rtl-dec19-wl] Error 2
make[1]: Leaving directory `$SRC/wireless-testing'
```

I find this in wireless-testing/debian/control:
```
Package: linux-image-2.6.37-rc6rtl-dec19
Architecture: i386
Section: kernel
Priority: optional
Provides: linux-image,  linux-image-2.6
Pre-Depends: debconf (>= 0.2.17) | debconf-2.0
Depends:  coreutils (>= 5.96)
Suggests: fdutils, linux-doc-2.6.37-rc6rtl-dec19 | linux-source-2.6.37-rc6rtl-dec19, ksymoops, linux-image-2.6.37-rc6rtl-dec19-dbg
Description: Linux kernel binary image for version 2.6.37-rc6rtl-dec19
 This package contains the Linux kernel image for version 
 2.6.37-rc6rtl-dec19.
 .
```

Any idea what's going on here, or suggestions?
(Just don't say 'ndiswrapper'; swapping wireless cards is also not an option, thanks to Lenovo's BIOS whitelist).
I've already tried looking at compat-wireless, but that's a no-go; I'll try hacking debian/control to work.

---

### Post by Ibidem on 2010-12-20
OK, 
SOLVED (possible bug in make-kpkg).
make-kpkg is being stupid--it appends '-wl' to the package name (per branch name?), but doesn't write that name to debian/control.
The control file must be updated manually, but make-kpkg regenerates debian/control on every run; setting chattr +i will make it die.
So the only solution is to overwrite debian/control AFTER make-kpkg does:
run make-kpkg; edit debian/control; copy debian/control to ../control; open a second terminal; rerun make-kpkg; while make-kpkg is working on the kernel, copy ../control to debian/control.

---

### Post by Ibidem on 2010-12-20
Well, after figuring out how to fool make-kpkg,
I discovered that I have an 8191SE--and that the 
driver is not even in wireless-testing.
It has to be otained from Realtek.

---


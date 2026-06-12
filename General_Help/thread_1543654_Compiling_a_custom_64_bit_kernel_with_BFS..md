---
title: "Compiling a custom 64 bit kernel with BFS."
date: 2010-08-01
forum: General Help
---

### Post by emshains on 2010-08-01
Hello forum. 

Since I have too much time on my hands, I would like to try and optimize my kernel a bit. Since I am doing this on a fresh install, I don't really care if the os gets bricked in the process, and I am sure I can bring it back if I can boot into a recovery console from the old kernel. So, I followed this[post]("http://ubuntuforums.org/showpost.php?p=7958358&postcount=4"). I patched it and copied and edited a config file from /boot/, saved it as .config, I tried it several times with both removing and not removing /debian and /debian.master directories from the source, yet I always get the same error when I run "make oldconfig". 
```
$ make oldconfig
scripts/kconfig/conf -o arch/x86/Kconfig

*** Error during writing of the kernel configuration.

make[1]: *** [oldconfig] Error 1
make: *** [oldconfig] Error 2

```
Will I be able to compile a kernel AND install nvidia's closed source driver ? 
My cpu is AMD Athlon 64 X2 5000+ non-b.e. (I guess it's a windsor, though I am not sure), I've got 1280 mb of ddr2 ram, asus m2n-sli n560 motherboard and an 8600gt.

---

### Post by anglican on 2010-08-02
> **emshains said:**
> Hello forum. 

Since I have too much time on my hands, I would like to try and optimize my kernel a bit. Since I am doing this on a fresh install, I don't really care if the os gets bricked in the process, and I am sure I can bring it back if I can boot into a recovery console from the old kernel. So, I followed this[post]("http://ubuntuforums.org/showpost.php?p=7958358&postcount=4"). I patched it and copied and edited a config file from /boot/, saved it as .config, I tried it several times with both removing and not removing /debian and /debian.master directories from the source, yet I always get the same error when I run "make oldconfig". 
```
$ make oldconfig
scripts/kconfig/conf -o arch/x86/Kconfig

*** Error during writing of the kernel configuration.

make[1]: *** [oldconfig] Error 1
make: *** [oldconfig] Error 2

```Will I be able to compile a kernel AND install nvidia's closed source driver ? 
My cpu is AMD Athlon 64 X2 5000+ non-b.e. (I guess it's a windsor, though I am not sure), I've got 1280 mb of ddr2 ram, asus m2n-sli n560 motherboard and an 8600gt.
1) Have you got all the necessary packages installed:
```
sudo apt-get install linux-source-2.6.32 linux-headers-`uname -r` kernel-package libncurses5-dev fakeroot
```2) It's more convenient (especially later) to be root:
```
sudo /bin/bash
```3) Change to your source directory and run "make oldconfig" etc...

H

---


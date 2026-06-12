---
title: "Natty gtk+1.2 installation problem"
date: 2011-07-31
forum: General Help
---

### Post by upartizan on 2011-07-31
Hello! I`m using Ubuntu 11.04.
I need to install some old printer-driver, it requires gtk+-1.2.
This package is not present in repositories, so I tried to compile it from source code.
I can not install gtk+-1.2.10 because I get an error:
```
./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking for ranlib... (cached) ranlib
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
loading cache ./config.cache within ltconfig
ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
configure: error: libtool configure failed

```
libtool 2.2.6b present.


ps adding reppository from this thread didn`t help: [http://ubuntuforums.org/showthread.php?t=1784254](http://ubuntuforums.org/showthread.php?t=1784254)

---


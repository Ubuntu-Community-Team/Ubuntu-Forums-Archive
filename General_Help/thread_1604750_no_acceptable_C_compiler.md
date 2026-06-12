---
title: "no acceptable C compiler"
date: 2010-10-24
forum: General Help
---

### Post by machko on 2010-10-24
Hi, can somebody help with this: ( using ubuntu 10.10)

root@server:/etc/ssh/mc-4.6.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux
checking host system type... x86_64-unknown-linux
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

but...

root@server:/etc/ssh/mc-4.6.1# apt-get install gcc-4.5-base
Csomaglisták olvasása... Kész / Done
Függ&#337;ségi fa építése 
Állapot adatok olvasása... Kész / Done
gcc-4.5-base már a legújabb verzió. / you already have the newest version

and...

root@server:/etc/ssh/mc-4.6.1# gcc --version
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: apt-get install <selected package>

root@server:/etc/ssh/mc-4.6.1# g++ --version
The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: apt-get install <selected package>

I don't get it, honestly - maybe thats because the 10.10 ubuntu ?

---

### Post by HermanAB on 2010-10-24
Howdy,

Compile the kernel.

The easiest and best way to ensure that your development environment is configured correctly, is to follow a howto guide on compiling the kernel.  After that, any other software will compile too.

---

### Post by bukwirm on 2010-10-24
Did you install the build-essential package? I believe it's still required for compiling stuff.

---

### Post by WorMzy on 2010-10-24
gcc-4.5-base is a fairly useless package. The package that contains the gcc executable is, as suggested, "gcc". However, it's probably best if you install build essential.

```
sudo apt-get install build-essential
```

---

### Post by sgosnell on 2010-10-24
+1  Build-essential is one of the first packages you need to install.

---


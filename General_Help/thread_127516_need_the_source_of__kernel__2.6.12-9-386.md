---
title: "need the source of  kernel  2.6.12-9-386"
date: 2006-02-09
forum: General Help
---

### Post by shams2 on 2006-02-09
hi,
i am runing ubutntu, and need the source of kernel 2.6.12-9-386 which is the runing kernel for this distro, plz help me from where i can get it?

---

### Post by az on 2006-02-09
Install the relevant linux headers package to compile a kernel module.  If that is what you need to do, you do not need the full source.  Install build-essential to get the toolchain.  The kernel was compiled with a different version of the compiler, though, so you will have to install gcc-3.4, as well.

the linux-headers for the 386 kerneland build-essential are all on the install cd, so you don't need network access.  However, gcc-3.4 is not on the cd.  You need to fetch the gcc-3.4, gcc-common and cpp-3.4 packages by hand - use the packages.ubuntu.com website.

If you really do need to recompile the whole kernel, install the linux-source package.

---

### Post by shams2 on 2006-02-09
thanks for reply, you are right i need the kernel headers to install the driver for my conexant hsf modem, i installed the gcc-3.4 with ap-get, browse the cd and there is package.gz, don't know the exact name of kernel headers to use apt-get to install the package, or is there any other way to install from cd?

---

### Post by az on 2006-02-09
[QUOTE=shams2]thanks for reply, you are right i need the kernel headers to install the driver for my conexant hsf modem, i installed the gcc-3.4 with ap-get, browse the cd and there is package.gz, don't know the exact name of kernel headers to use apt-get to install the package, or is there any other way to install from cd?[/QUOTE]
Either use synaptic (search, click and install)

or
sudo apt-cache search linux-headers
sudo apt-get install linux-headers-386

---


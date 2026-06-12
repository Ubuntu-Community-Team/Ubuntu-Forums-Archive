---
title: "Noob needs basic help"
date: 2009-09-12
forum: General Help
---

### Post by VincentCruise on 2009-09-12
I am a noob and I can't follow some basic directions for installing a driver. Can you help? I don't know much about terminal commands and so forth.

Step 1: Package Extraction:

tar zxfg ZD1211LnxDrv_xxxx.tar.gz
#where xxxx is the version number, such as 2_0_0_0

The first thing one should do is to uncompress this package by tar. After untaring this package, you can see the source files. One should change directory into this directory for proceeding the next step.

Step 2 Build and install the driver

The package contains drivers for ZD1211 and ZD1211B. If you doesn't have specified request, both of them will be installed. Under the extracted directory, there is a Makefile in it. Because our driver can support for kernel 2.4 and kernel 2.6 there are two sets of rule in the Makefile. One has to modify the Makefile according to the path of "kernel source tree" and the version of the kernel in your system. In the Makefile, you may see the following statements:

#if the kernel is 2.6.x turn on this
#KERN_26=Y
#kERNEL_SOURCE=/usr/src/linux-2.6.7
#if the kernel is 2.4.x turn on this
KERN_24=Y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8

If you want to build the kernel under the kernel of 2.4.x, one has to set the variable KERN_24=y and comment the KERN_26=y like that as the example above and modify the variable KERNEL_SOURCE to the path which you install the kernel source. After doing these things, one just need to type the "make" and the driver module will be generated and installed.

---

### Post by Bucky Ball on 2009-09-12
You need to move to the directory you have 'untarred' to. Where is it extracting?

```
dir /etc

```... will show you everything in the directory '/etc'.
```

cd /etc
```... will put you at the /etc directory.

If, for instance you have extracted to /media/programs/ZD1211 you would input:

```
cd /media/programs/ZD1211
```... which would put you there, or:

```
dir /media/programs/
```... would show you what was in there.

What bit are you having problems with exactly?

---

### Post by VincentCruise on 2009-09-12
I extracted it using the command:

tar zxfg Desktop/Linux/ZD1211LnxDrv_xxxx.tar.gz

I'm a noob and don't know where it went

---

### Post by Bucky Ball on 2009-09-12
Well, it went to the directory /Desktop/Linux/

---


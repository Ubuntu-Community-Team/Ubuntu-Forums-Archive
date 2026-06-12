---
title: "Where??! Directory of C header files..."
date: 2006-04-17
forum: General Help
---

### Post by mengqing on 2006-04-17
I am trying to run Vmware Workstation 5.51..and when I configuring it.. i've been asked to specify the "Directory of C header files"..

I entered /usr/src/linux/include, however the program said 
"The kernel defined by this directory of header files does not have the same address space size as your running kernel."

What is wrong??? I thought /usr/src/linux/includer is the header directory...

I am running the 2.6.16ck4 kernel...

would anybody enlight me???

thx

---

### Post by az on 2006-04-17
Install build-essential to bring in the headers and the compiler toolchain.  You will also need your linux-headers-(version) package which is the version of the kernel you are running.  Just install the linux-headers-386 (or 686, k7, whatever) metapackage and that will take care of the rest

---

### Post by mengqing on 2006-04-17
[QUOTE=azz]Install build-essential to bring in the headers and the compiler toolchain.  You will also need your linux-headers-(version) package which is the version of the kernel you are running.  Just install the linux-headers-386 (or 686, k7, whatever) metapackage and that will take care of the rest[/QUOTE]


I've built the 2.6.16 kernel... so build-essential shouldnt be the problem...

Also, I have the source in /usr/src so shouldnt the header be there already??? I tried to download the 2.6.16 header however didnt find one that match the kernel version I m using..

---

### Post by az on 2006-04-17
[QUOTE=mengqing]I've built the 2.6.16 kernel... so build-essential shouldnt be the problem...

Also, I have the source in /usr/src so shouldnt the header be there already??? I tried to download the 2.6.16 header however didnt find one that match the kernel version I m using..[/QUOTE]

It should use the source tree instead of the headers.  How did you compile and install the kernel?

---


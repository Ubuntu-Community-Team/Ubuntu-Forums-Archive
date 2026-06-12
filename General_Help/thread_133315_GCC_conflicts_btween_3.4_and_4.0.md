---
title: "GCC conflicts btween 3.4 and 4.0"
date: 2006-02-19
forum: General Help
---

### Post by madubuntuer on 2006-02-19
Well this is just flippin annoying. When I try using anything that need a kernel module the damn thing needs to be compiled using gcc 3.4 however anjuta and g++ need gcc4.0 and so does gnome 2.12. OSS is complaining about it and the damn CC enviroment bvarible is set but it still complains. Saying it I shud be using gcc3.4

so how do I resolve this conflict?

can I run it in 32bit chroot but use it in the 64bit system

---

### Post by jrib on 2006-02-20
Most configure scripts respect the environment variable you set with 'export CC=gcc-3.4'.  I've had one occasion where I had to pass it as an option to ./configure, './configure --cc=gcc-3.4'.  You can always use a dirty hack and change where the /usr/bin/gcc symlink points to...

---


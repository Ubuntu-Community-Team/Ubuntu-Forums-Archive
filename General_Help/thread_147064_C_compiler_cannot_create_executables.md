---
title: "C compiler cannot create executables"
date: 2006-03-19
forum: General Help
---

### Post by majik279 on 2006-03-19
I downloaded wine and am trying to install it. I couldn't get it installed using the repositories because when I add them to sources.list, they just get ignored for some reason. So, when I type in ./configure I get:

```

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

and in the config.log it says:

```

configure:1888: checking for C compiler default output file name
configure:1891: gcc -m32    conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/**libc.so** when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/**libc.a** when searching for -lc/usr/bin/ld: skipping incompatible /usr/lib/**libc.so** when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/**libc.a** when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
configure:1894: $? = 1
configure: failed program was:
| /* confdefs.h.  */

```

I have reinstalled 'build-essential' i have gcc-4 and gcc-3.4 and gcc installed. I also have libc6 installed. I see where people are saying to install glib-dev, but that's not on my list of available software in synaptic. Looking at this:

[http://packages.ubuntulinux.org/breezy/virtual/glibc-2.3.5-0ubuntu1](http://packages.ubuntulinux.org/breezy/virtual/glibc-2.3.5-0ubuntu1)

makes it seem like glib is part of libc6. SO, what am I missing? If I need to install glibc-dev, then where do I download it from? I'm running an AMD64 machine with Ubuntu 64 Breezy installed. Any help would be greatly appreciated.

---

### Post by JAwuku on 2006-03-19
Hi, just been searching the Ubuntu packages site, and there is one package which may fulfil your needs : **libc6-dev-amd64**

Try typing in ```
sudo apt-get install libc6-dev-amd64
```
and see if this helps.

Try and install other packages such as **make**, **gnome-devel** etc. if the above does not work.

---

### Post by majik279 on 2006-03-19
I must not have the correct repository in my sources.list because I don't have that. Care to upload a copy of your sources.list? Thanks for your help.

---

### Post by majik279 on 2006-03-19
OK! It appears that installing the 'build-essential' package DOES WORK on 32 BITS.

IF you're running 64, then it's not the solution. I don't know what it is yet, though. I, instead, created a 32 bit chroot and it worked from there.

---

### Post by adza on 2007-04-27
sweet.. i had the same problem (running on AMD-64) the package to get it all working is as follows..

1) sudo apt-get build-dep wine   -- installs dependencies
2) sudo apt-get install wine  -- wine
3) sudo apt-get install libc6-dev-i386 -- the missing link!!


install happy :)

---


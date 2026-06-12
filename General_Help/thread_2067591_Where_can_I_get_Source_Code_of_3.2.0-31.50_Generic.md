---
title: "Where can I get Source Code of 3.2.0-31.50 Generic"
date: 2012-10-07
forum: General Help
---

### Post by lihai425 on 2012-10-07
Hi, I am a beginner of linux driver development, now I am using Ubuntu 12.04 LTS, the core of linux is 3.2.0-31 Generic, when I compile my first linux driver, I met a conflict issue that my kernel source code is conflict with my current ubuntu version.

so, can anyone help me? where can I download the source code of 3.2.0-31 Generic?

---

### Post by GeForce 9500GT on 2012-10-07
[Take a look here]("http://www.kernel.org/"). This is the Linux kernel website.

---

### Post by zombifier25 on 2012-10-07
> **GeForce 9500GT said:**
> [Take a look here]("http://www.kernel.org/"). This is the Linux kernel website.
Good advice, but Ubuntu's Linux kernel has major differences from the vanilla Linux kernel. I'm sure the OP wants to grab the Ubuntu one.
The instructions for getting and compiling Ubuntu's kernel is here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Lars Noodén on 2012-10-07
In addition to kernel.org mentioned above, it's in the 12.04 repository you can get it with apt-get.

```

apt-get source linux-image-3.2.0-31-generic

```

---

### Post by MG&amp;TL on 2012-10-07
> **Lars Noodén said:**
> In addition to kernel.org mentioned above, it's in the 12.04 repository you can get it with apt-get.

```

sudo apt-get source linux-image-3.2.0-31-generic

```

Ditch 'sudo' - that might cause problems with files owned as root. :)

---

### Post by Lars Noodén on 2012-10-07
> **MG&TL said:**
> Ditch 'sudo' - that might cause problems with files owned as root. :)

Thanks.  I've fixed it.  It's a reflex to use sudo with apt-get but it is not needed when loading source.

---

### Post by MG&amp;TL on 2012-10-07
> **Lars Noodén said:**
> Thanks.  I've fixed it.  It's a reflex to use sudo with apt-get but it is not needed when loading source.

Tell me about it, I do it all the time then wonder why I can't build. :)

---

### Post by lihai425 on 2012-10-07
> **Lars Noodén said:**
> In addition to kernel.org mentioned above, it's in the 12.04 repository you can get it with apt-get.

```

apt-get source linux-image-3.2.0-31-generic

```

Thanks, I ever tried to get the source code by "apt-get install linux-source-3.2.0-31-generic", but it was not worked.

But now I see that your command is get image, I mean that are you sure it is get the source code of it?

---

### Post by Lars Noodén on 2012-10-07
> **lihai425 said:**
> Thanks, I ever tried to get the source code by "apt-get install linux-source-3.2.0-31-generic", but it was not worked.

But now I see that your command is get image, I mean that are you sure it is get the source code of it?

Right and it's also 'apt-get source' not 'apt-get install'.  It will download the Linux source to your current directory.  So be where you want the source to go when you do it.

---

### Post by lihai425 on 2012-10-07
> **Lars Noodén said:**
> Right and it's also 'apt-get source' not 'apt-get install'.  It will download the Linux source to your current directory.  So be where you want the source to go when you do it.

Thank you very much, Now I am downloading it.

---

### Post by lihai425 on 2012-10-07
> **Lars Noodén said:**
> Right and it's also 'apt-get source' not 'apt-get install'.  It will download the Linux source to your current directory.  So be where you want the source to go when you do it.

I met another issue, the source code was downloaded complete, and I move the source code (decompressed) to /usr/src/linux-3.2.31/

then I cd to /usr/src/linux-3.2.31/, and then 
make oldconfig
make prepare
make scripts

then I update my makefile for "hello" linux driver, and compile it.

then I still got "insmod: error inserting 'hello.ko': -1 Invalid module format", do you know why?
=========================================================
root@ubuntu:~/Documents# [COLOR="red"]make[/COLOR]
make -C /usr/src/linux-3.2.31/ M=/root/Documents
make[1]: Entering directory `/usr/src/linux-3.2.31'

  WARNING: Symbol version dump /usr/src/linux-3.2.31/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Documents/hello.o
/root/Documents/hello.c: In function ‘hello_exit’:
/root/Documents/hello.c:13:2: warning: ‘return’ with a value, in function returning void [enabled by default]
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Documents/hello.mod.o
  LD [M]  /root/Documents/hello.ko
make[1]:[COLOR="red"] Leaving directory `/usr/src/linux-3.2.31'[/COLOR]
root@ubuntu:~/Documents# [COLOR="red"]modinfo hello.ko[/COLOR]
filename:       hello.ko
author:         lpj
license:        GPL
srcversion:     EDF2990443E0047B5832364
depends:        
vermagic:       [COLOR="red"]3.2.28 SMP mod_unload modversions 686 [/COLOR]
root@ubuntu:~/Documents# [COLOR="red"]insmod hello.ko[/COLOR]
insmod: error inserting 'hello.ko': -1 Invalid module format
root@ubuntu:~/Documents#[COLOR="red"] uname -r[/COLOR]
[COLOR="red"]3.2.0-31-generic[/COLOR]
root@ubuntu:~/Documents#

---

### Post by lihai425 on 2012-10-07
I still need your help

---

### Post by Lars Noodén on 2012-10-07
Looking at the official notes, if you are working with drivers, you do not need to rebuild the kernel.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

But drivers and kernel building are out of my league.  The build process is not like with a regular package.  I do have some old notes from a *long* time ago where I did have to build a custom kernel.  But they get stuck on the 'make menuconfig' step:

make mrproper
make menuconfig

make dep
make-kpkg clean
make-kpkg --revision=3.2.0.lars.1.0 kernel_image

---


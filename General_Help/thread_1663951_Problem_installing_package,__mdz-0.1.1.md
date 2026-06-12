---
title: "Problem installing package,  mdz-0.1.1"
date: 2011-01-10
forum: General Help
---

### Post by gotanothergrot on 2011-01-10
:-s

=================
mdz Installation
=================

You need development versions of the following libraries:

 * GTK2
 * libpng 
 * pkg-config
 * mpfr
 * pthreads

Unless you know what you're doing it is strongly recommended to use
the development packages provided by your Linux distribution's package
manager.

Once the library dependacies are satisified:

  cd src
  make
  sudo make install

_my Teminal output_


graham@graham-desktop:~$ pwd
/home/graham
graham@graham-desktop:~$ cd /mdz-0.1.1
bash: cd: /mdz-0.1.1: No such file or directory
graham@graham-desktop:~$ cd 
graham@graham-desktop:~$ cd /home/graham/mdz-0.1.1
graham@graham-desktop:~/mdz-0.1.1$ cd src
graham@graham-desktop:~/mdz-0.1.1/src$ make
gcc `pkg-config --cflags gtk+-2.0` -Wall -Wextra -pedantic -std=gnu99 -DVERSION=\"0.1.1\" -O3 -fomit-frame-pointer -Winline -c cmdline.c
In file included from palette.h:7,
                 from main.h:4,
                 from cmdline.c:8:
image_info.h:8: fatal error: mpfr.h: No such file or directory
compilation terminated.
make: *** [cmdline.o] Error 1
graham@graham-desktop:~/mdz-0.1.1/src$ sudo make install
gcc `pkg-config --cflags gtk+-2.0` -Wall -Wextra -pedantic -std=gnu99 -DVERSION=\"0.1.1\" -O3 -fomit-frame-pointer -Winline -c cmdline.c
In file included from palette.h:7,
                 from main.h:4,
                 from cmdline.c:8:
image_info.h:8: fatal error: mpfr.h: No such file or directory
compilation terminated.
make: *** [cmdline.o] Error 1
graham@graham-desktop:~/mdz-0.1.1/src$

---

### Post by lrgmmc on 2011-01-10
not to sound mean, but did you install those packages? also have you tried redownloading the app?

---

### Post by gotanothergrot on 2011-01-10
no. the package was from a disc that came with linux magazine.

---

### Post by oldos2er on 2011-01-10
apt-cache search mpfr:
lib32gmp3-dev - Multiprecision arithmetic library developers tools (32bit)
libgmp3-dev - Multiprecision arithmetic library developers tools
libmpc-dev - multiple precision complex floating-point library development package
libmpc2 - multiple precision complex floating-point library
libmpfr-dev - multiple precision floating-point computation developers tools
libmpfr-doc - multiple precision floating-point computation documentation
libmpfr4 - multiple precision floating-point computation
libgmpada1 - Ada binding to the GNU MultiPrecision library: shared library
libgmpada1-dbg - Ada binding to the GNU MultiPrecision library: debug symbols
libgmpada1-dev - Ada binding to the GNU MultiPrecision library: development
libmpfi-dev - multiple precision floating-point interval computation library
libmpfi0 - multiple precision floating-point interval computation library
libmpfr1ldbl - multiple precision floating-point computation

Install the -dev files it's asking for. You'll need to repeat this process for all the dependencies listed in your first post.

---

### Post by gotanothergrot on 2011-01-10
> **oldos2er said:**
> 

Install the -dev files it's asking for. You'll need to repeat this process for all the dependencies listed in your first post.

I'm trying,


:(
apt-cache search mpf
libmpfr1ldbl: command not found
graham@graham-desktop:~$ apt-cache search mpfr
libgmp3-dev - Multiprecision arithmetic library developers tools
libmpc-dev - multiple precision complex floating-point library development package
libmpc2 - multiple precision complex floating-point library
libmpfr-dev - multiple precision floating-point computation developers tools
libmpfr-doc - multiple precision floating-point computation documentation
libmpfr4 - multiple precision floating-point computation
libgmpada1 - Ada binding to the GNU MultiPrecision library: shared library
libgmpada1-dbg - Ada binding to the GNU MultiPrecision library: debug symbols
libgmpada1-dev - Ada binding to the GNU MultiPrecision library: development
libmpfi-dev - multiple precision floating-point interval computation library
libmpfi0 - multiple precision floating-point interval computation library
libmpfr1ldbl - multiple precision floating-point computation
graham@graham-desktop:~$ sudo apt-get install GTK2
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package GTK2
graham@graham-desktop:~$ sudo apt-get install lib32gmp3-dev
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lib32gmp3-dev
graham@graham-desktop:~$ sudo apt-get lib32gmp3-dev
E: Invalid operation lib32gmp3-dev
graham@graham-desktop:~$

---

### Post by oldos2er on 2011-01-10
Typo? The package name is libgmp3-dev (it helps if you use copy & paste).

You will need to run **apt-cache search gtk2 dev** to find the correct packages to install. You can also do all this with Synaptic Package Manager, if a GUI is easier for you.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware)

---

### Post by gotanothergrot on 2011-01-10
Thanks, oldos2er 

I'll try that.

---


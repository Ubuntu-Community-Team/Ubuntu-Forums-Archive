---
title: "Build Kernel"
date: 2006-05-28
forum: General Help
---

### Post by helpme123 on 2006-05-28
Hello,
I am trying to use the make command in a shell.  I get this message:
"make
make -C driver
make[1]: Entering directory `/home/cheech/ndiswrapper-1.16/driver'
Can't find kernel build files in /lib/modules/2.6.12-10-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/cheech/ndiswrapper-1.16/driver'
make: *** [all] Error 2"

In /lib/modules/2.6.12-10-386 , there is no build folder.  What do I do to create one? THANKS!!!

---

### Post by simo on 2006-05-28
You dont create it. You must install some additional packages. I do not know what packages exactly but try looking for in synaptic something like modules, linux etc.

---

### Post by dschaller on 2006-05-28
You need the kernel headers installed in order to compile kernel modules. If you're using the 386 kernel, use Synaptic to get linux-headers-386.

---

### Post by Sutekh on 2006-05-28
[quote=helpme123]
In /lib/modules/2.6.12-10-386 , there is no build folder.  What do I do to create one? THANKS!!![/quote]
You need the relevant kernel headers package.  Does your Ubuntu install have *any* kind of internet connection?

If so, this command will get the headers.
```
sudo apt-get install linux-headers-2.6.12-10-386
```

---

### Post by helpme123 on 2006-05-28
Thank you Sutekh

I followed that command, now I get this error:

"make -C driver
make[1]: Entering directory `/home/cheech/ndiswrapper-1.16/driver'
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/cheech/ndiswrapper-1.16/driver \
        DRIVER_VERSION=1.16
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  LD      /home/cheech/ndiswrapper-1.16/driver/built-in.o
/bin/sh: ar: command not found
make[3]: *** [/home/cheech/ndiswrapper-1.16/driver/built-in.o] Error 127
make[2]: *** [_module_/home/cheech/ndiswrapper-1.16/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/cheech/ndiswrapper-1.16/driver'
make: *** [all] Error 2
"

Any ideas of what to do?thanks!

---

### Post by Sutekh on 2006-05-28
So you have a net connection?  Great!  It makes things alot easier.  

Next you need to install a C compiler.  For this particular kernel you need the GNU C Compiler v3.4 (gcc-3.4) and other important compiling packages (build-essential)
```
sudo apt-get install build-essential gcc-3.4
```

---


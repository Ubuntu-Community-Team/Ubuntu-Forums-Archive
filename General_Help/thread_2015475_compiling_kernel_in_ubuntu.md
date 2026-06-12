---
title: "compiling kernel in ubuntu"
date: 2012-07-03
forum: General Help
---

### Post by scarja on 2012-07-03
Hi,
I'm trying to compile a kernel, but wethere it a 2.6.x or a 3.x kernel i always get the same errore message:

```

make[1]: *** [kernel/bounds.s] Error 1
make: *** [prepare0] Error 2

```Does anyone have any ideas??
I'm running latest ubuntu (12 something) and already googled and some people suggested checking the "config_cross_compilation" variable to see if it was empty and it is... I'm running "make vmlinux.srec" i've already run "make menuconfig".

James

---

### Post by cipherboy_loc on 2012-07-03
Question, why are you wanting to run a custom kernel? Ubuntu has a repository of pre-built [kernels]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), and generally the community doesn't support driver errors on custom kernels. 

Disclaimer aside, can you post more of the error message? Is there stuff above those two lines that you posted? Also, why make vmlinux.srec?


Cipherboy

---

### Post by scarja on 2012-07-04
hi,
 the custom kernel is then meant for a PB1100 board so i'm creating the linux.srec to then load it through TFTP.

I admit i kind of wrote in general help and chanced it.
Here is what i get:
```

root@james-VirtualBox:~/Desktop/linux-3.4.3/linux-3.4.3# make vmlinux.srec
gcc: error: 0: No such file or directory
gcc: error: unrecognized option ‘-G’
gcc: error: unrecognized option ‘-EL’
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      kernel/bounds.s
gcc: error: 0: No such file or directory
gcc: error: unrecognized option ‘-G’
gcc: error: unrecognized option ‘-EL’
make[1]: *** [kernel/bounds.s] Error 1
make: *** [prepare0] Error 2
root@james-VirtualBox:~/Desktop/linux-3.4.3/linux-3.4.3#

```

thanks if anyone can help, or if anyone can give suggestions on where to ask for help?


James

---

### Post by Redblade20XX on 2012-07-04
> **scarja said:**
> hi,
 the custom kernel is then meant for a PB1100 board so i'm creating the linux.srec to then load it through TFTP.

I admit i kind of wrote in general help and chanced it.
Here is what i get:
```

root@james-VirtualBox:~/Desktop/linux-3.4.3/linux-3.4.3# make vmlinux.srec
gcc: error: 0: No such file or directory
gcc: error: unrecognized option ‘-G’
gcc: error: unrecognized option ‘-EL’
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      kernel/bounds.s
gcc: error: 0: No such file or directory
gcc: error: unrecognized option ‘-G’
gcc: error: unrecognized option ‘-EL’
make[1]: *** [kernel/bounds.s] Error 1
make: *** [prepare0] Error 2
root@james-VirtualBox:~/Desktop/linux-3.4.3/linux-3.4.3#

```thanks if anyone can help, or if anyone can give suggestions on where to ask for help?


James

Maybe you should use a stable version of the kernel for a build? 3.4.2. or 3.4.4

Also can you give use some information on your build environment since gcc is throwing unrecognized errors.

- Red

---

### Post by scarja on 2012-07-05
hi,
here is a test with a different version:
```

root@james-VirtualBox:~/Desktop/linux-2.6.38# make vmlinux.srec
gcc: error: 0: No such file or directory
gcc: error: unrecognized option ‘-G’
gcc: error: unrecognized option ‘-EL’
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      kernel/bounds.s
gcc: error: 0: No such file or directory
gcc: error: unrecognized option ‘-G’
gcc: error: unrecognized option ‘-EL’
make[1]: *** [kernel/bounds.s] Error 1
make: *** [prepare0] Error 2
root@james-VirtualBox:~/Desktop/linux-2.6.38# 

```

i just installed ubuntu 12 on a new VM, ran all the updates and then ran make menuconfig and then make vmlinux.srec... what do you need to know?

---

### Post by scarja on 2012-07-05
is this what you needed?
```

root@james-VirtualBox:~/Desktop/linux-2.6.38# gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
root@james-VirtualBox:~/Desktop/linux-2.6.38# 

```

---

### Post by scarja on 2012-07-05
i ran make with "-d" i don't know if that helps:
```

................. all other "ok" stuff..............................

 No need to remake target `scripts/Makefile.build'.
Updating goal targets....
Considering target file `__build'.
 File `__build' does not exist.
  Considering target file `include/generated/bounds.h'.
   File `include/generated/bounds.h' does not exist.
    Considering target file `kernel/bounds.s'.
     File `kernel/bounds.s' does not exist.
      Considering target file `kernel/bounds.c'.
       Looking for an implicit rule for `kernel/bounds.c'.
       Trying pattern rule with stem `bounds.c'.
       Trying implicit prerequisite `kernel/bounds.c_shipped'.
       No implicit rule found for `kernel/bounds.c'.
       Finished prerequisites of target file `kernel/bounds.c'.
      No need to remake target `kernel/bounds.c'.
      Considering target file `FORCE'.
       File `FORCE' does not exist.
       Finished prerequisites of target file `FORCE'.
      Must remake target `FORCE'.
      Successfully remade target file `FORCE'.
     Finished prerequisites of target file `kernel/bounds.s'.
    Must remake target `kernel/bounds.s'.
Putting child 0x08c7c758 (kernel/bounds.s) PID 26936 on the chain.
Live child 0x08c7c758 (kernel/bounds.s) PID 26936 
Reaping winning child 0x08c7c758 PID 26936 
Live child 0x08c7c758 (kernel/bounds.s) PID 26937 
  CC      kernel/bounds.s
gcc: error: 0: No such file or directory
gcc: error: unrecognized option ‘-G’
gcc: error: unrecognized option ‘-EL’
Reaping losing child 0x08c7c758 PID 26937 
make[1]: *** [kernel/bounds.s] Error 1
Removing child 0x08c7c758 PID 26937 from chain.
Reaping losing child 0x0887b7b8 PID 26935 
make: *** [prepare0] Error 2
Removing child 0x0887b7b8 PID 26935 from chain.
root@james-VirtualBox:~/Desktop/linux-2.6.38# 

```

---

### Post by dino99 on 2012-07-05
follow this guide

[https://help.ubuntu.com/community/Kernel/Compile/](https://help.ubuntu.com/community/Kernel/Compile/)

---

### Post by scarja on 2012-07-05
I tried, still no luck :(

Do i need to be in a certain DIR to compile a kernel? I'm doing it from a folder on the desktop..

---

### Post by Redblade20XX on 2012-07-05
> **scarja said:**
> I tried, still no luck :(

Do i need to be in a certain DIR to compile a kernel? I'm doing it from a folder on the desktop..

From the other posts you've posted on other sites, your trying to compile for a MIPS system?  

Maybe this will help, [http://www.linux-mips.org/wiki/Kernel_Build](http://www.linux-mips.org/wiki/Kernel_Build)

-Red

---

### Post by scarja on 2012-07-10
Hi,
yes that is indeed what i'm doing looking through different suggestions i found out that i need to build a cross compilation enviroment first, i've been able to compile binutils ok but i'm having problems with gcc. I first tried with 4 version but i think it's too new, now trying with a 3.3.4 and a 3.3.6 i've gotten further on but i get stuck here:

I'm following this guide:
[http://imara.inria.fr/users/oliviermehani/2007ie/mipsellinuxtoolchain](http://imara.inria.fr/users/oliviermehani/2007ie/mipsellinuxtoolchain)


```

In function &#8216;open&#8217;,
inlined from &#8216;collect_execute&#8217; at ../../gcc-3.3.6/gcc/collect2.c:1575:20:
/usr/include/i386-linux-gnu/bits/fcntl2.h:51:24: error: call to &#8216;__open_missing_mode&#8217; declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [collect2.o] Error 1
make[1]: Leaving directory `/media/4b4fda61-803d-46ed-a574-c1ab1f7cda6f/gcc-build/gcc'
make: *** [all-gcc] Error 2
root@james-VirtualBox:/media/4b4fda61-803d-46ed-a574-c1ab1f7cda6f/gcc-build#

```

---


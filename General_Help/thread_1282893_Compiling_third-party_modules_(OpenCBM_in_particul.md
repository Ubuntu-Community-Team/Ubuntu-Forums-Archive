---
title: "Compiling third-party modules (OpenCBM in particular)"
date: 2009-10-04
forum: General Help
---

### Post by Eric Christopherson on 2009-10-04
Hi, all. I am using 9.04 (Xubuntu). A few months ago I correctly compiled and installed [OpenCBM]("http://www.trikaliotis.net/opencbm"), including the kernel module, using the directions found at [http://ubuntuforums.org/showthread.php?t=500905]("http://ubuntuforums.org/showthread.php?t=500905"). Since then, it appears that I have upgraded my kernel from 2.6.28-13-generic to 2.6.28-15-generic. The old kernel module still loads, but I decided to recompile it just to make sure things are OK.

Here is where the problem started. The compilation process now seems to now produce a file called cbm.o; it used to be cbm.ko. It installs the .o file in the modules directory, but insmod and modprobe are unable to deal with it. I'm not sure what's changed since the last time I compiled it; the OpenCBM sources haven't. So my main question is: why isn't this producing a .ko file? And how do I make it produce one?

Second, I wanted to look at the build process to see if I could figure it out. The output produced is:
```
eric@eric-desktop:~/Sources/opencbm-0.4.2a/sys/linux$ make -f LINUX/Makefile
ln -s LINUX/Makefile Makefile
make -C /lib/modules/2.6.28-15-generic/build here=`pwd` CBM4LINUX_KERNEL_FLAGS= SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/eric/Sources/opencbm-0.4.2a/sys/linux/cbm_module.o
/home/eric/Sources/opencbm-0.4.2a/sys/linux/cbm_module.c: In function ‘init_module’:
/home/eric/Sources/opencbm-0.4.2a/sys/linux/cbm_module.c:907: warning: passing argument 5 of ‘parport_register_device’ from incompatible pointer type
  LD [M]  /home/eric/Sources/opencbm-0.4.2a/sys/linux/cbm.o
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
rm -f Makefile

```

So question #2: how do I see the actual command lines being executed, instead of "CC [M]..."? I have googled all over and asked on IRC, with no result. This seems to be something specific to kernel and module builds, since compiling other things produces the actual command lines.

Finally, question #3: Is there any system for automatically copying third-party modules to the new module directories when upgrading kernels?

---

### Post by Eric Christopherson on 2009-10-11
OK. I've found out a few things since posting that -- and I also realized I forgot to say I'm running the AMD64 kernel and userland.

#1: The .ko module is not generated because the program modpost fails for some reason. I still don't know why. See below for more detailed info.

#2: Apparently passing V=1 on the command line (after the word make, not before) will turn on verbose output from the kernel build process. I finally found this by looking through the kernel build makefiles; I would have thought it would be well-documented on the Web! Furthermore, V= appears to be part of something called kbuild, but I went to the Sourceforge page for kbuild and it said the project was dormant. :confused:

(Also, V=1 hides the very useful message "MODPOST x modules" :()

More detail on #1: I found, through trial and error, that running make with sudo successfully builds the .ko module, while running it as a normal user does not. This, I found out, is true whether running (and building against) kernel 2.6.28-13-generic or 2.6.28-15-generic (contrary to my prior assumption). Also, it is true even when building a very simple example module.

The example module I tried is taken from [http://tldp.org/LDP/lkmpg/2.6/html/x121.html](http://tldp.org/LDP/lkmpg/2.6/html/x121.html). Here is the code and the output from various invocations of make; perhaps someone can figure out from this what my problem is:

hello-1.c:
```
/*  
 *  hello-1.c - The simplest kernel module.
 */
#include <linux/module.h>    /* Needed by all modules */
#include <linux/kernel.h>    /* Needed for KERN_INFO */

int init_module(void)
{
    printk(KERN_INFO "Hello world 1.\n");

    /* 
     * A non 0 return means init_module failed; module can't be loaded. 
     */
    return 0;
}

void cleanup_module(void)
{
    printk(KERN_INFO "Goodbye world 1.\n");
}

```Makefile:
```
obj-m += hello-1.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$$PWD modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$$PWD clean

```When I run make without sudo and without V=1:
```

eric@eric-desktop:~/Sources/hello-module$ make
make -C /lib/modules/2.6.28-13-generic/build M=$PWD modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/eric/Sources/hello-module/hello-1.o
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'

```When I run make without sudo and with V=1:
```

eric@eric-desktop:~/Sources/hello-module$ make V=1
make -C /lib/modules/2.6.28-13-generic/build M=$PWD modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/eric/Sources/hello-module/.tmp_versions ; rm -f /home/eric/Sources/hello-module/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/eric/Sources/hello-module
  gcc -Wp,-MD,/home/eric/Sources/hello-module/.hello-1.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(hello_1)"  -D"KBUILD_MODNAME=KBUILD_STR(hello_1)"  -c -o /home/eric/Sources/hello-module/.tmp_hello-1.o /home/eric/Sources/hello-module/hello-1.c
(cat /dev/null;   echo kernel//home/eric/Sources/hello-module/hello-1.ko;) > /home/eric/Sources/hello-module/modules.order
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.28-13-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.28-13-generic/Module.symvers -I /home/eric/Sources/hello-module/Module.symvers  -o /home/eric/Sources/hello-module/Module.symvers -S -K /usr/src/linux-headers-2.6.28-13-generic/Module.markers -M /home/eric/Sources/hello-module/Module.markers -w  -s
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'

```When I run make with sudo and without V=1:
```

eric@eric-desktop:~/Sources/hello-module$ sudo make
make -C /lib/modules/2.6.28-13-generic/build M=$PWD modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/eric/Sources/hello-module/hello-1.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/eric/Sources/hello-module/hello-1.mod.o
  LD [M]  /home/eric/Sources/hello-module/hello-1.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'

```When I run make with sudo and with V=1:
```

eric@eric-desktop:~/Sources/hello-module$ sudo make V=1
make -C /lib/modules/2.6.28-13-generic/build M=$PWD modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/eric/Sources/hello-module/.tmp_versions ; rm -f /home/eric/Sources/hello-module/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/eric/Sources/hello-module
  gcc -Wp,-MD,/home/eric/Sources/hello-module/.hello-1.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(hello_1)"  -D"KBUILD_MODNAME=KBUILD_STR(hello_1)"  -c -o /home/eric/Sources/hello-module/.tmp_hello-1.o /home/eric/Sources/hello-module/hello-1.c
(cat /dev/null;   echo kernel//home/eric/Sources/hello-module/hello-1.ko;) > /home/eric/Sources/hello-module/modules.order
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.28-13-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.28-13-generic/Module.symvers -I /home/eric/Sources/hello-module/Module.symvers  -o /home/eric/Sources/hello-module/Module.symvers -S -K /usr/src/linux-headers-2.6.28-13-generic/Module.markers -M /home/eric/Sources/hello-module/Module.markers -w  -s
  gcc -Wp,-MD,/home/eric/Sources/hello-module/.hello-1.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(hello_1.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(hello_1)"  -DMODULE -c -o /home/eric/Sources/hello-module/hello-1.mod.o /home/eric/Sources/hello-module/hello-1.mod.c
  ld -r -m elf_x86_64  --build-id -o /home/eric/Sources/hello-module/hello-1.ko /home/eric/Sources/hello-module/hello-1.o /home/eric/Sources/hello-module/hello-1.mod.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'

```Could this be a problem in Ubuntu's build tools? As I mentioned, I first thought the problem came with the -15 kernel, but now I've found that it's the same on -13, so I don't think it's the kernel packages themselves that are at fault. On the other hand, modpost is provided by the linux-headers-* packages.

---

### Post by lacippp4 on 2011-11-21
I have the exact same problem with 2.6.32-34-generic :D

---


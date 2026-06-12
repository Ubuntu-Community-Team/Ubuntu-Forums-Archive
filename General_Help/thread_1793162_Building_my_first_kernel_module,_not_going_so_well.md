---
title: "Building my first kernel module, not going so well"
date: 2011-06-29
forum: General Help
---

### Post by CountSessine on 2011-06-29
I'm reading [this]("http://tldp.org/LDP/lkmpg/2.6/lkmpg.pdf") book on programming kernel modules, and I've managed to trip and fall on the very first example. The source is super-duper simple:

```

/*
 * hello-1.c - The simplest kernel module.
 */
#include <linux/module.h>
#include <linux/kernel.h>

int init_module( void )
{
  printk( KERN_INFO "Hello world 1.\n" );

  /*
   * A 0 return means init_module failed; module can't be loaded.
   */
  return 0;
}

void cleanup_module( void )
{
  printk( KERN_INFO, "Goodbye world 1.\n" );
}

```

as is the Makefile:

```

obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

And yet, when I try to compile this on Natty, with headers installed, this is what I get:

```

user@ubuntu:~/Documents/kernel-modules$ make
make -C /lib/modules/2.6.38-8-generic/build M=/home/user/Documents/kernel-modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
  CC [M]  /home/user/Documents/kernel-modules/hello-1.o
cc1: error: unrecognized command line option "-mregparm=3"
/home/user/Documents/kernel-modules/hello-1.c:1: error: bad value (i686) for -march= switch
Assembler messages:
Error: unknown architecture `i686'

Error: unrecognized option -march=i686
make[2]: *** [/home/user/Documents/kernel-modules/hello-1.o] Error 1
make[1]: *** [_module_/home/user/Documents/kernel-modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2

```

Anyways, before I dive into kbuild and try to figure out what's going on, is there anyone who can give me a hint about what I should be doing here to diagnose this? It seems odd that it complains that my gcc has no support for stack protectors - I'm using 4.5.2 which I would imagine is late enough for this. And the -march and the -mregparms errors have me stumped.

---

### Post by Bachstelze on 2011-06-29
Works For Me&#8482;, make sure you have build-essential installed, not just gcc.

---

### Post by CountSessine on 2011-06-29
Well, this is probably the fastest I've ever answered one of my own questions. :-)

I had been experimenting with some ARM builds for a beagleboard a little while ago, and even though 'which' finds the right version of gcc, somehow kbuild was finding my cross-compiler. I removed the cross compiler from my path and I was able to build the kernel module. Yay!

---


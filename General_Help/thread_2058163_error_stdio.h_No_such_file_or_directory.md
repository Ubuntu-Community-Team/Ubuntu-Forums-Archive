---
title: "error: stdio.h: No such file or directory"
date: 2012-09-15
forum: General Help
---

### Post by wxwx0104 on 2012-09-15
when i makefile a module. i meet this problem, no such file or directory. it works if i use gcc -c. the o file appears.(i think i means the code is right). I installed the build-essential. and the stdio.h is in the direction usr/inculde/stdio.h(so the build-essential is already installed). i do not know what is going on.
i tried 2 kind of Makefile both of them cannot work.
```
ifneq ($(KERNELRELEASE),)
    obj-m    := d.o

else
    KDIR    := /lib/modules/$(shell uname -r)/build
    PWD        := $(shell pwd)

    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
    endif
``````

obj-m := hello.o
KERNELDIR ?= /usr/src/linux-source-3.2.0
PWD := $(shell pwd)

all:
    $(MAKE) -C $(KERNELDIR) M=$(PWD) modules

```
```

#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <errno.h>
#include <termios.h>
#include <unistd.h>
#include <xdo.h>
#include <X11/Xlib.h>
#include <X11/keysym.h>

```
the h file i include.

---

### Post by steeldriver on 2012-09-15
AFAIK the standard include paths are not searched during kernel compiles - the things you are trying to include really have no place in a kernel module - kernels have their own I/O routines (e.g. printk) and certainly shouldn't be using X11 headers

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html)

Hope this helps

---

### Post by wxwx0104 on 2012-09-15
> **steeldriver said:**
> AFAIK the standard include paths are not searched during kernel compiles - the things you are trying to include really have no place in a kernel module - kernels have their own I/O routines (e.g. printk) and certainly shouldn't be using X11 headers

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html)

Hope this helps

you means i cannot include this files which not include in the linux source? I searched a lot. for example, <stdio.h> usually appears in the helloworld tutorial. and the x11/.h file is working for a keyboard driver. and the whole driver works well on other computers.

---

### Post by steeldriver on 2012-09-15
sorry this is beyond my level of expertise - I don't know what to suggest

---


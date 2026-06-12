---
title: "Makefiles"
date: 2010-06-18
forum: General Help
---

### Post by ibe2fly4chu on 2010-06-18
I am currently trying to install my xbox360 controller for use on my computer. I am currently on ubuntu 10.4 and i have the script:

KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS=-I$(shell pwd)

obj-m:=xpad.o

all:
        $(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install:
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick 

Thing is created a blank document, name it and ended it with a .make extansions. I am not sure if this is correct. I nee do make a make file to run it in terminal (duh). The error i get when i try to run this file is: make: *** No targets specified and no makefile found.  Stop.

any advice?

---

### Post by Simian Man on 2010-06-18
By default make looks for files named "Makefile" or "makefile" with no extensions.  You can use another file name, but then you have to tell make what it is with the -f switch.  For example:```
make -f file.make [targets]
```

I'm not sure if that will be all you need though, because I really don't understand what you're trying to do exactly.

---

### Post by ibe2fly4chu on 2010-06-18
changed the file name to just make. tried to run it from terminal but still got the same error

error: make: *** No targets specified and no makefile found.  Stop.

when i try to specify the file by name..this is the mesg is returns:

error: make:11: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

---

### Post by ibe2fly4chu on 2010-06-18
bump

---

### Post by Simian Man on 2010-06-18
Make is a very stupid program and insists that the makefiles be formatted exactly right.  You must indent them with exactly one tab after the lines that end in a semicolon:

```

KERNEL_PATH?=/usr/src/linux-headers-$(shell uname -r)

EXTRA_CFLAGS=-I$(shell pwd)

obj-m:=xpad.o

all:
        $(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)

install:
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```

Make sure those spaces after all and install are actually tab characters and not spaces or make will bitch again.

---

### Post by ibe2fly4chu on 2010-06-19
ah...lol that solved the issue. had to back space the lines after semi to start of margin then tab over one..thanks

---


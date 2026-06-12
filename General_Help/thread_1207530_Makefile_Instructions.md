---
title: "Makefile Instructions"
date: 2009-07-08
forum: General Help
---

### Post by VastOne on 2009-07-08
I am trying to get AMD K10 thermal sensors working in Jaunty using the following instructions:

```
$ mkdir k10temp && mv k10temp.c k10temp/k10temp.c
```

Create a makefile with the lines :

```
obj-m := k10temp.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:

$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
```


Example for my kernel is :

obj-m := k10temp.o
KDIR := /lib/modules/2.6.29.30-Candela/build
PWD := $(shell pwd)
default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

and now you can start compile these node with :

```
$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
$ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ depmod && modprobe k10temp

```

I know where it say (uname -r) I have to put in my own uname variables, but where there are other () such s (pwd) and (shell pwd) do I supply those variables as well?

First time compiling and using makefile, so please be gentle....

---

### Post by zigga15 on 2009-07-08
pwd, uname etc. are all commands from terminal that print results out to the screen when run. gmake or make read these in a particular way to get the information reported by these commands. A makefile is like a script with a special interpreter, sort of.

If you are making this thing portable then you should keep them in there. If the build is not working, I do not think that is the problem.

You can test it by running pwd, or uname or whatever from a terminal and simply hard coding it into the makefile. That is, just copy paste the results in where the ( ) commands are, replace the variables with results.

~ Dan



> **VastOne said:**
> I am trying to get AMD K10 thermal sensors working in Jaunty using the following instructions:

```
$ mkdir k10temp && mv k10temp.c k10temp/k10temp.c
```

Create a makefile with the lines :

```
obj-m := k10temp.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:

$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
```


Example for my kernel is :

obj-m := k10temp.o
KDIR := /lib/modules/2.6.29.30-Candela/build
PWD := $(shell pwd)
default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

and now you can start compile these node with :

```
$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
$ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ depmod && modprobe k10temp

```

I know where it say (uname -r) I have to put in my own uname variables, but where there are other () such s (pwd) and (shell pwd) do I supply those variables as well?

First time compiling and using makefile, so please be gentle....

---

### Post by VastOne on 2009-07-08
> **zigga15 said:**
> pwd, uname etc. are all commands from terminal that print results out to the screen when run. gmake or make read these in a particular way to get the information reported by these commands. A makefile is like a script with a special interpreter, sort of.

If you are making this thing portable then you should keep them in there. If the build is not working, I do not think that is the problem.

You can test it by running pwd, or uname or whatever from a terminal and simply hard coding it into the makefile. That is, just copy paste the results in where the ( ) commands are, replace the variables with results.

~ Dan

Thanks Dan.  I assumed these things but wanted clarification. I am having trouble compiling it and hopefully can respond back here and get help on a line by line basis. I am not at home now to start it but will later.

I appreciate your insight and help

Terry

---

### Post by VastOne on 2009-07-16
> **zigga15 said:**
> pwd, uname etc. are all commands from terminal that print results out to the screen when run. gmake or make read these in a particular way to get the information reported by these commands. A makefile is like a script with a special interpreter, sort of.

If you are making this thing portable then you should keep them in there. If the build is not working, I do not think that is the problem.

You can test it by running pwd, or uname or whatever from a terminal and simply hard coding it into the makefile. That is, just copy paste the results in where the ( ) commands are, replace the variables with results.

~ Dan

Hey Dan

When I run my script, I receive the following

make: Entering directory `/usr/src/linux-2.6.30'
scripts/Makefile.build:44: /home/vastone/k10temp/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/vastone/k10temp/Makefile'.  Stop.
make: *** [_module_/home/vastone/k10temp] Error 2
make: Leaving directory `/usr/src/linux-2.6.30'

This is my makefile

obj-m := k10temp.o
    KDIR := /lib/modules/(shell uname -r)/build
    PWD := $(shell pwd)

    default:

    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

I cannot see where the error lies, maybe your shrewd eyes can

Thanks

---


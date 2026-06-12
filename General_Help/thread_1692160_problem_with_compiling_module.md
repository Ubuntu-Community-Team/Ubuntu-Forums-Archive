---
title: "problem with compiling module"
date: 2011-02-21
forum: General Help
---

### Post by sunil.gandhi007 on 2011-02-21
I have a directory /usr/src/linux-2.6.36.1/mod where i store all my modules and compile them.I had compiled them before.but now it is giving me following error:

make: Entering directory `/usr/src/linux-2.6.36.1'
  Building modules, stage 2.
  MODPOST 1 modules
make: Leaving directory `/usr/src/linux-2.6.36.1'

The command i used was
make -C /lib/modules/2.6.36.1/build M=$(PWD) modules

Plz help me with this prob...
Thanx in advance...

---

### Post by sunil.gandhi007 on 2011-02-21
hey guys!!!I found out the solution..for those who are having same problem..
My makefile was wrong...I had not told compiler which file to compile...
silly...bt solved...
This is my currect new make file...


obj-m += abc2.o

all:
        make -C /lib/modules/2.6.36.1/build M=$(shell pwd) modules
clean:
        make -C /lib/modules/2.6.36.1/build M=$(shell pwd) clean

---


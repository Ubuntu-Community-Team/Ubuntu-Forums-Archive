---
title: "Error building kernel module"
date: 2011-08-13
forum: General Help
---

### Post by eldro on 2011-08-13
hello, 

I'm new but sadly I have to ask for a solution because there is nothing I can do about it ..

So I want to build the module which is described here: [http://www.sondaar.nl/Avr-html/usb_drv02.html](http://www.sondaar.nl/Avr-html/usb_drv02.html)

It is pretty old, but suits to most 2.6-requirements (I think...) so I changed only these things:

[LIST]
[*]avr309.c: renamed the include linux/config.h to linux/autoconf.h
[*]Makefile: changed the header-path from *KDIR:=/usr/src/linux-headers-$(shell uname -r)/build to* *KDIR:=/lib/modules/$(shell uname -r)/build*
[*]and installed packages build-essential, kbuild, linux-headers-2.6.32-28-generic (and some more in desperate trys to solve it)
[/LIST]
It looks like there is only a package or something like that missing, so I hope the understanding of the code is not that necessary.

But first 
$ uname -a:
> Linux elddes 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux 	

In order to compile it by "make" the following happened (first stage has been succesfully compiled):
$ sudo make:
> make -C /lib/modules/2.6.32-28-generic/build SUBDIRS=/home/eldro/usb/ modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-28-generic'
Building modules, stage 2.
MODPOST 1 modules
CC /home/eldro/usb/avr309.mod.o
/home/eldro/usb/avr309.mod.c:9: error: implicit declaration of function ‘KBUILD_STR’
/home/eldro/usb/avr309.mod.c:9: error: ‘avr309’ undeclared here (not in a function)
make[2]: *** [/home/eldro/usb/avr309.mod.o] Fehler 1
make[1]: *** [modules] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-28-generic'
make: *** [default] Fehler 2 	

It looks like there is a problem with Kbuild. Admittedly, i was already able build the module on a debian system (same kernel-version, same steps to get it working).

Thanks so much in advance

---


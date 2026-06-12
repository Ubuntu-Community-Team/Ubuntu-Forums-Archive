---
title: "Compilation help (DMX4Linux)"
date: 2009-08-23
forum: General Help
---

### Post by mr tim esquire on 2009-08-23
Ive fiddled for a while with this and havn't made any progress.  There error was exactly the same under fedora.  I'm hoping i might hit it lucky with someone here :). fingers crossed!
```
tim@topsytim:~/Programs/dmx4linux-2.6.1$ ./configure                                                                       
dmx4linux successfully configured
tim@topsytim:~/Programs/dmx4linux-2.6.1$ make
make -C libs all
make[1]: Entering directory `/home/tim/Programs/dmx4linux-2.6.1/libs'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tim/Programs/dmx4linux-2.6.1/libs'
make -C tools all
make[1]: Entering directory `/home/tim/Programs/dmx4linux-2.6.1/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tim/Programs/dmx4linux-2.6.1/tools'
make -C examples all
make[1]: Entering directory `/home/tim/Programs/dmx4linux-2.6.1/examples'
make -C htmlexamples all
make[2]: Entering directory `/home/tim/Programs/dmx4linux-2.6.1/examples/htmlexamples'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tim/Programs/dmx4linux-2.6.1/examples/htmlexamples'
make[1]: Leaving directory `/home/tim/Programs/dmx4linux-2.6.1/examples'
make -C drivers all
make[1]: Entering directory `/home/tim/Programs/dmx4linux-2.6.1/drivers'
make -C dmxdev all
make[2]: Entering directory `/home/tim/Programs/dmx4linux-2.6.1/drivers/dmxdev'
make -C /lib/modules/2.6.28-11-generic/build M=/home/tim/Programs/dmx4linux-2.6.1/drivers/dmxdev modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/tim/Programs/dmx4linux-2.6.1/drivers/dmxdev/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[3]: *** [_module_/home/tim/Programs/dmx4linux-2.6.1/drivers/dmxdev] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/home/tim/Programs/dmx4linux-2.6.1/drivers/dmxdev'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/tim/Programs/dmx4linux-2.6.1/drivers'
make: *** [all] Error 2
tim@topsytim:~/Programs/dmx4linux-2.6.1$

```

---


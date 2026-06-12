---
title: "vanilla kernel with realtime preemption (i did exactly what it said!!!)"
date: 2006-03-25
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-03-25
i was following the directions at [http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation]("http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation")...

...when i got to the "low-latency kernel" part, i picked ["vanilla kernel with realtime preemption"]("http://ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption").

before i started, i installed build-essential, because it seems to be a must for these kinds of things.

i copied and pasted the code straight from the web page and into a terminal window - everything went well until```
make-kpkg --revision 1 --initrd kernel_image kernel_headers modules_image
```

the last few lines in the terminal window were```
  CC [M]  drivers/net/pcnet32.o
  CC [M]  drivers/net/eepro100.o
  CC [M]  drivers/net/e100.o
  CC [M]  drivers/net/tlan.o
  CC [M]  drivers/net/epic100.o
  CC [M]  drivers/net/sis900.o
drivers/net/sis900.c: In function 'sis900_reset_phy':
drivers/net/sis900.c:962: warning: 'status' may be
used uninitialized in this function
drivers/net/sis900.c: In function
'sis900_auto_negotiate':
drivers/net/sis900.c:1416: warning: 'status' may be
used uninitialized in this function
drivers/net/sis900.c: In function 'sis900_read_mode':
drivers/net/sis900.c:1452: warning: 'status' may be
used uninitialized in this function
  CC [M]  drivers/net/yellowfin.o
  CC [M]  drivers/net/natsemi.o
  CC [M]  drivers/net/ns83820.o
  CC [M]  drivers/net/fealnx.o
  CC [M]  drivers/net/tg3.o
  CC [M]  drivers/net/bnx2.o
  CC [M]  drivers/net/skge.o
In file included from drivers/net/skge.c:43:
drivers/net/skge.h:2477: error: duplicate member
'hw_lock'
make[3]: *** [drivers/net/skge.o] Error 1
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory
`/usr/src/linux-2.6.15.6-rt21'
make: *** [stamp-build] Error 2
```

i might have gone on, but the web page said "once that is complete without errors..."

...can anyone help me?

---

### Post by kartebi on 2006-08-09
[-X  when you make menuconfig , uncheck all the unneeded hardware. Thats a good reason for not compiling. 

Or you have
  CC [M]  drivers/net/pcnet32.o
  CC [M]  drivers/net/eepro100.o
  CC [M]  drivers/net/e100.o
  CC [M]  drivers/net/tlan.o
  CC [M]  drivers/net/epic100.o
  CC [M]  drivers/net/sis900.o
  CC [M]  drivers/net/yellowfin.o
  CC [M]  drivers/net/natsemi.o
  CC [M]  drivers/net/ns83820.o
  CC [M]  drivers/net/fealnx.o
  CC [M]  drivers/net/tg3.o
  CC [M]  drivers/net/bnx2.o
  CC [M]  drivers/net/skge.o
that many network cards ? :o

---


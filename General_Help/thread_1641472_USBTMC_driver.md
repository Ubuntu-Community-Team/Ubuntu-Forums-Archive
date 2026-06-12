---
title: "USBTMC driver"
date: 2010-12-09
forum: General Help
---

### Post by Peque on 2010-12-09
Hey Guys. 
I'm trying to make a machine for a AGILENT INSTRUMENT - and needing this driver to make it work: 
[http://www.home.agilent.com/upload/cmc_upload/All/usbtmc.html](http://www.home.agilent.com/upload/cmc_upload/All/usbtmc.html)

But after downloading the driver and trying to run the make command - I'm getting this error:
```

$ sudo make
[sudo] password for pbj: 
make	-C /lib/modules/2.6.35-23-generic/build	SUBDIRS=/build modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /build/usbtmc.o
/build/usbtmc.c: In function ‘usbtmc_open’:
/build/usbtmc.c:187: error: implicit declaration of function ‘kmalloc’
/build/usbtmc.c:187: warning: assignment makes pointer from integer without a cast
/build/usbtmc.c: In function ‘usbtmc_release’:
/build/usbtmc.c:216: error: implicit declaration of function ‘kfree’
/build/usbtmc.c: In function ‘usbtmc_probe’:
/build/usbtmc.c:1517: warning: assignment makes pointer from integer without a cast
/build/usbtmc.c: In function ‘usbtmc_init’:
/build/usbtmc.c:1664: warning: assignment makes pointer from integer without a cast
make[2]: *** [/build/usbtmc.o] Fejl 1
make[1]: *** [_module_/build] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.35-23-generic'
make: *** [default] Fejl 2
pbj@Ubuntu-test:/build$ 

```

Since its failing - what caurses this problæem, Could it be that its a very OLD driver - so it'll only compile against old versions of Linux. 
I'm running Ubuntu 10.10 Desktop  - and know this have worked for 8.04 versions - but then it should be quite easy to make it work under newer releases! But hopefully you'll give me the answers for that problem! 

TIA 
P

---

### Post by nuess0r on 2010-12-23
Hi Peque

Stuff like this happens sometimes when things in the kernel change (or a compiler gets more restrictive).

As you, I was using this driver before and know that it works. When I get an error like that, I type the error into a search engine and look at other projects if they got a solution. 

In this case I searched for *error: implicit declaration of function ‘kfree’* and found a discussion about parallels and problems with recent kernels: [http://forum.parallels.com/pda/index.php/t-103146.html]("http://forum.parallels.com/pda/index.php/t-103146.html")

After reading this I would guess that you have to add the line:
*#include <linux/slab.h>*

to the Agilent driver source. Hopefully this is enough to get it working again.

---

### Post by robotarmy on 2011-03-08
Hey guys, i found this on google and it saved my ***.  Just confirming that adding:

```
#include <linux/slab.h>
```

to usbtmc.c solved the errors and the make completed fine.  Still haven't tested the drivers but we'll see how it goes!

(ubuntu 10.10 on a toshiba notebook)

---


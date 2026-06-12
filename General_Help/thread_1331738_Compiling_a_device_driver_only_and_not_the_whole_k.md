---
title: "Compiling a device driver only and not the whole kernel... Is this possible?"
date: 2009-11-19
forum: General Help
---

### Post by balteo on 2009-11-19
Hello,

I have recently installed the sources for 2.6.28 and being very new to device driver development I have the following question:

-can I compile the usb-storage (/home/julien/src/linux-source-2.6.28/drivers/usb/storage) module **without compiling the whole kernel**?
-If so, **how**?

Any clue welcome!

Julien.

---

### Post by ibuclaw on 2009-11-19
cd into the top directory of the kernel source [NOPARSE](/home/julien/src/linux-source-2.6.28),[/NOPARSE]
then run:
```
make M=./drivers/usb/storage
```

Regards
Iain

---

### Post by balteo on 2009-11-19
Thanks Ian: much better now. However I get this:
```

  WARNING: Symbol version dump /home/julien/Downloads/sources/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      drivers/usb/storage/usb-storage.o
ld: no input files
make[1]: *** [drivers/usb/storage/usb-storage.o] Erreur 1
make: *** [_module_./drivers/usb/storage] Erreur 2

```J.

---

### Post by ibuclaw on 2009-11-19
> **balteo said:**
> Thanks Ian: much better now. However I get this:
```

  WARNING: Symbol version dump /home/julien/Downloads/sources/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      drivers/usb/storage/usb-storage.o
ld: no input files
make[1]: *** [drivers/usb/storage/usb-storage.o] Erreur 1
make: *** [_module_./drivers/usb/storage] Erreur 2

```J.

Hmm, try running:
```

make prepare
make scripts

```
Then the same again.

---

### Post by balteo on 2009-11-19
Much better but...
```

  WARNING: Symbol version dump /home/julien/Downloads/sources/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      drivers/usb/storage/built-in.o
  CC [M]  drivers/usb/storage/scsiglue.o
  CC [M]  drivers/usb/storage/protocol.o
  CC [M]  drivers/usb/storage/transport.o
  CC [M]  drivers/usb/storage/usb.o
  CC [M]  drivers/usb/storage/initializers.o
  CC [M]  drivers/usb/storage/sierra_ms.o
  CC [M]  drivers/usb/storage/option_ms.o
  CC [M]  drivers/usb/storage/shuttle_usbat.o
  CC [M]  drivers/usb/storage/sddr09.o
  CC [M]  drivers/usb/storage/sddr55.o
  CC [M]  drivers/usb/storage/freecom.o
  CC [M]  drivers/usb/storage/dpcm.o
  CC [M]  drivers/usb/storage/isd200.o
  CC [M]  drivers/usb/storage/datafab.o
  CC [M]  drivers/usb/storage/jumpshot.o
  CC [M]  drivers/usb/storage/alauda.o
  CC [M]  drivers/usb/storage/karma.o
  LD [M]  drivers/usb/storage/usb-storage.o
ld: no input files
make[1]: *** [drivers/usb/storage/usb-storage.o] Erreur 1
make: *** [_module_./drivers/usb/storage] Erreur 2

```FYI I used make oldconfig before running the other commands...

---

### Post by balteo on 2009-11-20
from another forum, the solution was as simple as that:

```
sudo make drivers/usb/storage
```

thanks anyway!

Julien.

---

### Post by ibuclaw on 2009-11-20
> **balteo said:**
> from another forum, the solution was as simple as that:

```
sudo make drivers/usb/storage
```

thanks anyway!

Julien.

You shouldn't really be using sudo to compile modules in your home directory... but never mind.

---


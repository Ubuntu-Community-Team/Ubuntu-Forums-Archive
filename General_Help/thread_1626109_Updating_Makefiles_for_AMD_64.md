---
title: "Updating Makefiles for AMD 64?"
date: 2010-11-19
forum: General Help
---

### Post by mr_luksom on 2010-11-19
Hi,

I'm trying to get the driver for my wireless USB adapter working on my recently acquired AMD system.

I had no issues on my i386 systems, just compile the driver and insmod it into the kernel.

When I try compiling the same driver on the AMD machine I get the following errors:

```
 /tmp/rtl/driver/rtl/hal/rtl8192c/usb/usb_ops_linux.c:928: warning: assignment makes pointer from integer without a cast

/tmp/rtl/driver/rtl/include/wifi.h:362: warning: cast to pointer from integer of different size

```.

I get one of these errors for every file the driver attempts to touch when compiling the driver.

I have a feeling it has something to with this - I'm not sure if x86_64 is the correct 'ARCH':

```
 make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/2.6.35-22-generic/build M=/tmp/rtl/driver/rtl  modules

```

Any ideas to point me on my way?

---

### Post by dcstar on 2010-11-20
> **mr_luksom said:**
> Hi,

I'm trying to get the driver for my wireless USB adapter working on my recently acquired AMD system.

I had no issues on my i386 systems, just compile the driver and insmod it into the kernel.

When I try compiling the same driver on the AMD machine I get the following errors:

```
 /tmp/rtl/driver/rtl/hal/rtl8192c/usb/usb_ops_linux.c:928: warning: assignment makes pointer from integer without a cast

/tmp/rtl/driver/rtl/include/wifi.h:362: warning: cast to pointer from integer of different size

```.

I get one of these errors for every file the driver attempts to touch when compiling the driver.

I have a feeling it has something to with this - I'm not sure if x86_64 is the correct 'ARCH':

```
 make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/2.6.35-22-generic/build M=/tmp/rtl/driver/rtl  modules

```

Any ideas to point me on my way?

There are no guarantees that the code is 64-bit compatible, if things are not specifically designed to be compiled on 64-bit systems then there could be mismatches in data structures which may well be what is occurring.

Ask in the programming forum and some others with more knowledge may know.

---


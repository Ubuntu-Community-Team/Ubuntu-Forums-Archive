---
title: "Wireless setup problem - can't build ndiswrapper"
date: 2006-05-04
forum: General Help
---

### Post by Doctor Moley on 2006-05-04
Hi everyone,

I've just installed Ubuntu Breezy Badger and am trying to set up a wireless Internet connection on it. 

I'm using a Cisco/Linksys Wireless-G USB dongle (WUSB54G) and do not have access to a wired Internet connection.

I've downloaded the appropriate driver (rt2500usb) and installed ndiswrapper from the Ubuntu CD. When I checked to see if it was working, it said the hardware was detected and OK etc., but in the network settings it was not recognized.

I read in the Wiki that when setting it up, the ndiswrapper off the CD shouldn't be used, so I tried downloading it and building it. However, I can't get that to work. When I run 'make install' (I think) I get the following messages and error:

make -C driver
make[1]: Entering directory `/home/david/ndiswrapper-1.15/driver'
Can't find kernel build files in /lib/modules/2.6.12-9-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/david/ndiswrapper-1.15/driver'
make: *** [all] Error 2

I checked the directory that the kernel build files should be in, and it is non-existent. I'm stuck for what to do next. Help!

---

### Post by nanotube on 2006-05-04
> **Doctor Moley]Hi everyone,

I've just installed Ubuntu Breezy Badger and am trying to set up a wireless Internet connection on it. 

I'm using a Cisco/Linksys Wireless-G USB dongle (WUSB54G) and do not have access to a wired Internet connection.

I've downloaded the appropriate driver (rt2500usb) and installed ndiswrapper from the Ubuntu CD. When I checked to see if it was working, it said the hardware was detected and OK etc., but in the network settings it was not recognized.

I read in the Wiki that when setting it up, the ndiswrapper off the CD shouldn't be used, so I tried downloading it and building it. However, I can't get that to work. When I run 'make install' (I think) I get the following messages and error:

make -C driver
make[1]: Entering directory `/home/david/ndiswrapper-1.15/driver'
Can't find kernel build files in /lib/modules/2.6.12-9-386/build said:**
> : *** [prereq_check] Error 1
make[1]: Leaving directory `/home/david/ndiswrapper-1.15/driver'
make: *** [all] Error 2

I checked the directory that the kernel build files should be in, and it is non-existent. I'm stuck for what to do next. Help!
install the kernel headers. package "linux-kernel-headers" iirc.

---

### Post by laffytaffy on 2006-05-10
Doctor,
I have the exact same problem/message. I have the kernel headers, gcc, kernel tree, ect. installed that everyone talks about. Still nothing. I don't know why it has to be so difficult! Breezy 5.10. Please post if you have a solution, I'll do the same. Best.

---


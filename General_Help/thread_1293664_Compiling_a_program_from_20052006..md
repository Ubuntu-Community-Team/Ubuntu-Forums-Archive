---
title: "Compiling a program from 2005/2006."
date: 2009-10-17
forum: General Help
---

### Post by dragos240 on 2009-10-17
It has some compile errors due to being old etc.

Here are the errors:

./shell1
mkdir: cannot create directory `/home/harley/Desktop/nin_rt2570': File exists
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/harley/Desktop/nin_rt2570/rtusb_main.o
/home/harley/Desktop/nin_rt2570/rtusb_main.c:40: error: expected ‘)’ before string constant
/home/harley/Desktop/nin_rt2570/rtusb_main.c:100: error: unknown field ‘owner’ specified in initializer
/home/harley/Desktop/nin_rt2570/rtusb_main.c:100: warning: initialization from incompatible pointer type
/home/harley/Desktop/nin_rt2570/rtusb_main.c: In function ‘usb_rtusb_probe’:
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1784: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1793: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1802: error: ‘struct net_device’ has no member named ‘weight’
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: ‘dev_base’ undeclared (first use in this function)
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: (Each undeclared identifier is reported only once
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: for each function it appears in.)
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: ‘struct net_device’ has no member named ‘next’
make[2]: *** [/home/harley/Desktop/nin_rt2570/rtusb_main.o] Error 1
make[1]: *** [_module_/home/harley/Desktop/nin_rt2570] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
nin_rt2570.ko failed to build!
make: *** [module] Error 1

---

### Post by igknighted on 2009-10-17
Do you know what compiler it was designed for?  Chances are it is not the same one Ubuntu uses by default.  Also, changes to the kernel could very likely have  made it incompatible (in fact, almost certainly if it is a wireless driver... the wireless stacks have been completely rewritten).  You could go back to the old kernel it was designed for, or find a newer version.

---

### Post by dragos240 on 2009-10-18
It is a modified wireless driver for the rt2570 chipset. It is used for sending signals to the nintendo DS. For homebrew purposes.

---

### Post by igknighted on 2009-10-18
Hmm, that's a tough one.  Any chance you can install the version of ubuntu it was made for in a small partition for when you want to use it?  Short of working with the source to fix all the changes, I'm not sure what you could do.  Have you tried the developers website/mailing list to get any info on the current state of the driver?  Maybe the changes have been integrated by now...

---

### Post by dragos240 on 2009-10-19
It was made to be used with knoppix 4.0.2. Which won't boot up.

---

### Post by P4man on 2009-10-19
Perhaps you can create a VM with virtual box ( **not** the OSE version in the repo's, but PEUL version from VB website) and0 install/boot knoppix in a VM and filter the USB wifi stick so the VM has access to it. Assuming it is a USB wifi stick, if its not then.. hmm

---

### Post by dragos240 on 2009-10-19
> **P4man said:**
> Perhaps you can create a VM with virtual box ( **not** the OSE version in the repo's, but PEUL version from VB website) and0 install/boot knoppix in a VM and filter the USB wifi stick so the VM has access to it. Assuming it is a USB wifi stick, if its not then.. hmm

What's the difference between the open version and the closed one?

---

### Post by Giblet5 on 2009-10-19
> **dragos240 said:**
> It has some compile errors due to being old etc.

Here are the errors:

./shell1
mkdir: cannot create directory `/home/harley/Desktop/nin_rt2570': File exists
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/harley/Desktop/nin_rt2570/rtusb_main.o
/home/harley/Desktop/nin_rt2570/rtusb_main.c:40: error: expected ‘)’ before string constant
/home/harley/Desktop/nin_rt2570/rtusb_main.c:100: error: unknown field ‘owner’ specified in initializer
/home/harley/Desktop/nin_rt2570/rtusb_main.c:100: warning: initialization from incompatible pointer type
/home/harley/Desktop/nin_rt2570/rtusb_main.c: In function ‘usb_rtusb_probe’:
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1784: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1793: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1802: error: ‘struct net_device’ has no member named ‘weight’
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: ‘dev_base’ undeclared (first use in this function)
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: (Each undeclared identifier is reported only once
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: for each function it appears in.)
/home/harley/Desktop/nin_rt2570/rtusb_main.c:1824: error: ‘struct net_device’ has no member named ‘next’
make[2]: *** [/home/harley/Desktop/nin_rt2570/rtusb_main.o] Error 1
make[1]: *** [_module_/home/harley/Desktop/nin_rt2570] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
nin_rt2570.ko failed to build!
make: *** [module] Error 1


This has nothing to do with old code and everything to do with poorly-written code.

You can fix it if you know C. C hasn't changed much since the 70's...

Take a look at line 40 of /home/harley/Desktop/nin_rt2570/rtusb_main.c and fix the code. There's a missing ')' or a missing quotation mark.

Then compile again.

Attack the first error ONLY.

---

### Post by K.Mandla on 2009-10-19
> **Giblet5 said:**
> This has nothing to do with old code and everything to do with poorly-written code.
That was my interpretation of the error too. I'm afraid I don't have any advice for fixing it though, because I have all the coding abilities of a brick. :|

---

### Post by P4man on 2009-10-20
> **dragos240 said:**
> What's the difference between the open version and the closed one?

The closed one supports USB devices in the VM, the OSE version doesnt

---


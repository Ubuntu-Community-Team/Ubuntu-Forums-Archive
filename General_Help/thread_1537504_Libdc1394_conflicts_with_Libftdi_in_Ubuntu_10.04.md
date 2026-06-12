---
title: "Libdc1394 conflicts with Libftdi in Ubuntu 10.04"
date: 2010-07-23
forum: General Help
---

### Post by ilganeli on 2010-07-23
Hello, I have run into a conflict when using libdc1394 and libftdi in Ubuntu 10.04. When linking both into a program, it becomes impossible to open a USB connection via libftdi. The same program runs perfectly in ubuntu 9.1. 

It appears that libdc1394 has recently been updated to use libusb-1.0 to enable support for IIDC-over-USB which is why it is now conflicting with libftdi.

When we look at the following ldd in Ubuntu 10.04 we see that 
dc1394 uses libusb-1.0 and libftdi uses libusb-0.1. 


ldd /usr/lib/libdc1394.so
	linux-gate.so.1 =>  (0xb77cf000)
	libraw1394.so.11 => /usr/lib/libraw1394.so.11 (0xb774c000)
	libusb-1.0.so.0 => /usr/lib/libusb-1.0.so.0 (0xb773f000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb771d000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb76f7000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb759d000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7584000)
	/lib/ld-linux.so.2 (0xb77d0000)

ldd /usr/lib/libftdipp.so.1
	linux-gate.so.1 =>  (0xb783f000)
	libftdi.so.1 => /usr/lib/libftdi.so.1 (0xb782b000)
	libusb-0.1.so.4 => /usr/lib/libusb-0.1.so.4 (0xb7821000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb772f000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb76f6000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb75b1000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7593000)
	/lib/ld-linux.so.2 (0xb7840000)


In ubuntu 9.1, the ldd for libdc1394 shows : 
ldd /usr/lib/libdc1394.so
	linux-gate.so.1 =>  (0xb771c000)
	libraw1394.so.11 => /usr/lib/libraw1394.so.11 (0xb7696000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb765d000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7518000)
	/lib/ld-linux.so.2 (0xb771d000)


Which does not include libusb-1.0. Please note that doing ls -l /usr/lib/libdc1394 shows the same version (22.1.4) for the library on both 9.1 and 10.04.

Does anyone know how I can resolve my issues? Thank you.

---

### Post by ilganeli on 2010-07-26
I was able to resolve this issue by using the in-development 
libftdi library which uses the updated version of libusb - libusb-1.0. It is possible to contact the people maintaining libftdi to get access to the git repository.

---


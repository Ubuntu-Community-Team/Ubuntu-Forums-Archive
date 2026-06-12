---
title: "USB to Serial devices"
date: 2009-12-12
forum: General Help
---

### Post by jepeto68 on 2009-12-12
Hi
I have 3 USB to Serial devices with the FTDI chip
If i start connecting them one by one the first one will be assigned as /dev/ttyUSB0 the second as /dev/ttyUSB1 and the third as /dev/ttyUSB2
Now if i disconnect the first one (/dev/ttyUSB0) the other 2 devices will be reassigned from /dev/ttyUSB1 to /dev/ttyUSB0 and from /dev/ttyUSB2 to /dev/ttyUSB1

My question is: Is there any way to statically assign each device (or maybe the USB port) to a certain path so in any case they will not get reassigned by the system?

OS: KUBUNTU 9.10

Thanks

---


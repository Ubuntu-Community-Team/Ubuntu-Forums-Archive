---
title: "mutiple serial ports"
date: 2010-03-09
forum: General Help
---

### Post by loki_dre on 2010-03-09
Hello,
I can use 
cat /proc/tty/driver/usbserial 
usbserinfo:1.0 driver:2.0
0: module:pl2303 name:"pl2303" vendor:067b product:2303 num_ports:1 port:1 path:usb-0000:00:1d.0-1
1: module:pl2303 name:"pl2303" vendor:067b product:2303 num_ports:1 port:1 path:usb-0000:00:1a.1-1

to find out that my usb serial ports point to:
/dev/ttyUSB0
/dev/ttyUSB1

but how do I programmable find out which one is which based on where they are plugged into the computer?

the ports maybe unplugged and plugged back in but they will always use the same individual usb port!

---


---
title: "serial converter help"
date: 2010-10-20
forum: General Help
---

### Post by shamir50 on 2010-10-20
when i run "dmesg"i getthe following.
eth:no ipv6 routers present
usb: 3-1 new full speed usbdevice usingohci_hcd and address 2
usb 3-1 configuration #1 chosen from choice 1
usbscore registered new interface driver usbserial
usb serial support register for generic
usbcore register new interface driver usbserial generic
usbserial  usb serial driver core
 usbserial support register for pl2303
pl2303 3-1:1.0:pl2303 converter detected
usb 3-1:pl2303 converter now attached to ttyUSB0
usbcore register new interface driver  pl2303
pl2303:prolific pl2303 usb serial adapter driver
clocksource tsc unstable {delta =253295191 ns
 
is this device register or not also what the last line about thanks

---

### Post by Jebtrix on 2010-10-20
Looks to be registered fine on /dev/usb/ttyUSB0

As for the tsc clock error, is there more lines you didn't post? Usually there is another message about the kernel switched to different clock source.

---

### Post by shamir50 on 2010-10-20
no that the last line also im trying to setup minicom  but i cannot save  change

---


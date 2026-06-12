---
title: "configuring/using JTAG ICE 3 programmer / avr  issue"
date: 2011-07-20
forum: General Help
---

### Post by F.G. on 2011-07-20
hi folks,

so, i'm tying to figure out how to use a JTAGICE3 programmer with Ubuntu and the Crossworks avr compiler, and am pretty stumped as to how to get everything talking to each other.  on the advice of another thread i've added the line:
```
SUBSYSTEM=="usb", ACTION=="add", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2110", MODE="0666"
```
to a file in /etc/udev/rules.d i've named 70-bob.rules now if run: 
```
lsusb -v -d 03eb:2110
``` 
i can get all the info about it. when i look in /dev/bus/usb/001 the device pops up with one number or another when i plug it in. so it seems to be there, although I was kind of expecting it to pop up as a /dev/ttyUSB* device.
if i run avrp i get:
```
bob@bob-1005PX:~$ avrp -s /dev/bus/usb/001/035
Error: Not a valid programmer type reported
       Possibly no programmer connected
/dev/bus/usb/001/035: No programmer found

```
and if i use it as the port for Crossworks avr ide i get:
```
tcgetattr inappropriate ioctl for device(25)
```
so, is this i'm guessing that /dev/bus/usb/001/* is not the jtag being treated as a serial device?? 
so does anyone know what i'm doing wrong and how i can fix it? i'm pretty green about these things, though i really need to get it going somehow.  i know that the avr Crossworks CrossStudio ide may not support the JTAGICE3 programmer, though i feel like i've not setup the device properly to be used at all, anyway.

so, if anyone has some experience in this area and can give me some pointers / advice i'd be very gratefull.
thanks,
f.g.

---

### Post by F.G. on 2011-07-20
bump?

---


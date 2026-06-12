---
title: "Leogics pt-1001 pen tablet stopped working"
date: 2012-01-18
forum: General Help
---

### Post by leomahdi on 2012-01-18
Hi

My computer stopped responding to a Leogics pt-1001 pen tablet. It worked perfectly fine before, a couple of months back when I got the tablet but now it doesn't. It still works on windows xp so the tablet is not broken.

When I type 

cat /proc/bus/input/devices

I get this among others:

I: Bus=0003 Vendor=099a Product=2620 Version=0110
N: Name="  Digi Tablet"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=099a Product=2620 Version=0110
N: Name="  Digi Tablet"
P: Phys=usb-0000:00:1d.0-2/input2
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.2/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=1b
B: KEY=c01 0 1 0 0 0 0 0 0 0 0
B: ABS=1000003
B: MSC=10


Those two parts disappear when I disconnect the tablet, so the system obviously sees the device. 

I am using the latest version of Ubuntu 10.04 LTS - the Lucid Lynx 

Thank you for your support

---

### Post by 1script on 2012-01-18
I've noticed that sometimes when you disconnect a USB device and then re-connect it, it gets assigned a different device name, i.e. input8 instead of input7 it was before. It is most notable with virtual serial ports - it switches between /tty/USB0 and /tty/USB1 all the time - but maybe something like that happens in your case, too? Check if the driver looks for the device where it **actually** is, not where it was before.

---

### Post by leomahdi on 2012-01-18
K... How do I do that? :P Even with lsmod I can't tell which of the drivers belongs to the tablet.

Edit: I never had to install any drivers for it, just plug&play. I use an aspire one ZG5 laptop, it has 3 open usb-ports. I tried unplugging the mouse that I had plugged in atm, then replugging the the tablet, no change.

---


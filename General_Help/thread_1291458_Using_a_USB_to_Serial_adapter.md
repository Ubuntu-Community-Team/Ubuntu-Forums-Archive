---
title: "Using a USB to Serial adapter?"
date: 2009-10-14
forum: General Help
---

### Post by kachofool on 2009-10-14
Hey all,

I'm writing a program (in C++) that interfaces with devices that use a serial connection. I have (four) such devices but my computer only has 2 serial ports. I have an abundance of USB ports however... I was wondering if normal USB <-> Serial cables would work. Would I have to do anything special?

I found a seemingly simple modification that would let me 'convert' usb ports in /dev to serial ports.
hxxp://www.linux-usb.org/USB-guide/x356.html

Can anyone confirm that I can just grab an off-the-shelf USB->Serial adaptor and the posted link would work for me?

Regards,

KF

---

### Post by Jerry N on 2009-10-14
I think your biggest concern might be whether or not the serial device is compatible with a USB to serial cable. 

Edit:  I presently use a USB to parallel converter cable to operate an 18 year old HP laser printer.  My new cable works fine for both Win2000 and Ubuntu while one I have had around for 5 years or so works with Win2000 (with no drivers added) but not Ubuntu.   

Jerry

---

### Post by kachofool on 2009-10-15
Thanks for the reply... I have a sort of related question. Is there any way I can detect the number of serial ports available on my computer?

For example,

If I open up /proc/tty/driver/serial

I see something like this:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0
1: uart:16550A port:000002F8 irq:3 tx:0 rx:0
2: uart:unknown port:000003E8 irq:4
3: uart:unknown port:000002E8 irq:3

...I have 2 serial ports in the computer but I see 4 devices. What gives?

---


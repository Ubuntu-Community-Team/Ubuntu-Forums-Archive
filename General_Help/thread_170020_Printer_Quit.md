---
title: "Printer Quit"
date: 2006-05-03
forum: General Help
---

### Post by cssutto on 2006-05-03
At 1:00 AM, my printer worked fine.

Today it will not work and I get the following message when I go to System-Printers-print test

Paused: Unable to open USB device "usb://Hewlett-Packard/PSC%202170%20Series?serial=MY35GC927573": No such device

What do I do to correct this?

CSSJR

---

### Post by o_fortuna on 2006-05-03
[QUOTE=cssutto]At 1:00 AM, my printer worked fine.

Today it will not work and I get the following message when I go to System-Printers-print test

Paused: Unable to open USB device "usb://Hewlett-Packard/PSC%202170%20Series?serial=MY35GC927573": No such device

What do I do to correct this?

CSSJR[/QUOTE]
The first thing to try is to turn off the printer, unplug it, and leave it so for about a minute. Also, unplug the USB device. This is probably a problem with the printer (that's my experience). After a minute, plug the printer in, and plug in the USB cable again. If it still doesn't work, post the output of this command in the terminal (Applications-->Accessories-->Terminal)
```
dmesg | tail
```
That might tell if something went wrong in the USB connection.

---


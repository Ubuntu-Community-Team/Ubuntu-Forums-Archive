---
title: "Any software to capture and fire action on usb event?"
date: 2011-10-26
forum: General Help
---

### Post by spamalam on 2011-10-26
I have a usb device, a simple button but it has very flakey taiwan drivers for windows only.

I recall some time back having some usb driver software that would show different usb input codes for button down and button up events.

I was wondering, if there any simple software i can use to record an input event and then fire off a command or action if that event is hit?

I'd essentially like to have an event fired on button down.

---

### Post by aeiah on 2011-10-26
you may need drivers - not necessarily for that product, there may be several with the same internals or it may announce its self as a HID device or somesuch. what does lsusb show for the device?

---

### Post by tonysathre on 2011-10-26
This may help:

[http://stackoverflow.com/questions/873975/how-to-capture-raw-hid-input-on-linux](http://stackoverflow.com/questions/873975/how-to-capture-raw-hid-input-on-linux)

---

### Post by spamalam on 2011-11-03
lsusb not a thing, but dmesg:
[32220.123203] usb 1-1.2: USB disconnect, device number 12
[32225.173906] usb 1-1.2: new low speed USB device number 13 using ehci_hcd
[32225.276751] input: Panic Button as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input16
[32225.276881] generic-usb 0003:1130:0202.0008: input,hidraw0: USB HID v1.10 Device [Panic Button] on usb-0000:00:1a.0-1.2/input0
[32225.279081] input: Panic Button as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input17
[32225.279187] generic-usb 0003:1130:0202.0009: input,hidraw1: USB HID v1.10 Device [Panic Button] on usb-0000:00:1a.0-1.2/input1

---

### Post by spamalam on 2011-11-03
~$ ls -l /dev/input/by-id/
total 0
lrwxrwxrwx 1 root root  9 2011-11-03 19:50 usb-1130_Panic_Button-event-if00 -> ../event5
lrwxrwxrwx 1 root root  9 2011-11-03 19:50 usb-1130_Panic_Button-event-if01 -> ../event6

---

### Post by spamalam on 2011-11-04
okay so i seem to be a hit in google for my own thread, here's an answer for everyone:
[http://www.lunarlamp.co.uk/usb-panic-button-linux](http://www.lunarlamp.co.uk/usb-panic-button-linux)
[http://www.arcfn.com/2010/04/usb-panic-button-with-linux-and-python.html](http://www.arcfn.com/2010/04/usb-panic-button-with-linux-and-python.html)

The latter is what I'm using since I prefer python.

As this is registered as a generic-usb device and its two events recorded (down and up), I was able to track down the id code via google:
1130:0202
and got the above two hits.

and despite what I said before, lsusb showed something:
Bus 002 Device 004: ID 1130:0202 Tenx Technology, Inc. 
I missed it

---


---
title: "Using mouse buttons as keyboard shortcuts"
date: 2010-10-10
forum: General Help
---

### Post by cong06 on 2010-10-10
I have a Logitech wireless mouse (LX7 Cordless optical: [http://www.google.com/products/catalog?cid=9244743825054403800](http://www.google.com/products/catalog?cid=9244743825054403800)).

I would like to set it up so I could (in some occasions) use the mouse buttons as a remote for Amarok.

Is there a way that I could toggle between using the mouse "as a keyboard" and using the mouse as a mouse?
ie: I want to map the mouse buttons to any keyboard button (hopefully one that I can choose, or else the media buttons).

```

isaac@bohr:~$ dmesg | grep -i "logitech"
[162289.601836] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input10
[162289.601928] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input0
[162289.607590] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[162289.608302] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input11
[162289.608467] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input1
[162737.819387] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input12
[162737.819496] logitech 0003:046D:C517.0003: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input0
[162737.825319] logitech 0003:046D:C517.0004: fixing up Logitech keyboard report descriptor
[162737.825858] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input13
[162737.826038] logitech 0003:046D:C517.0004: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input1

```
Note: the receiver can take a wireless keyboard also. I don't have the keyboard with me, it's about 7 time zones away. I suspect that's why it's showing up in dmesg.

---


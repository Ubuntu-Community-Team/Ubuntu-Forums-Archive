---
title: "PS3 controller as Joypad on Ubuntu"
date: 2009-12-20
forum: General Help
---

### Post by D4Y.V on 2009-12-20
Dell Dimension C521 Ubuntu 9.10
I've found that it recognises it as an input device, but it doesn't recognise the inputs that it gives, I went into "/dev/input" and it turns out that "event14" is the PS3 controller.
I've also found that in "/dev/bus/usb/002" that a file called "014" is the PS3 controller.
When I plug the controller into the PC, A new file comes up under "/dev" called "/dev/usb". it contains "hiddev0".

I found these out via plug & unplugging the controller under these files.

I've been able to use it on Windows before, but Linux is a whole new game for me^^; I discovered that the controller had to be marked down somewhere in here, and apparently the computer DOES recognise it as a HID.
Also, I checked the System log viewer and whenever the controller is plugged in I get this log.
```
Dec 20 19:10:40 dave-desktop kernel: [13739.552297] sony 0003:054C:0268.000D: input,hiddev96,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:0b.0-7/input0
```If anyone can try to help me with the information displayed, I really have no idea what to do.

---

### Post by D4Y.V on 2009-12-20
I really need help with this! I need to beable to use my PS3 controller on things like PCSX and such!

---

### Post by D4Y.V on 2009-12-20
If nobody can help, then are there any links to websites on how to get it to work?

---

### Post by htomerif on 2010-01-20
Thats all very strange.  Im using 9.10 as well and it really just pops and goes when I plug it in under usb.  Im pretty sure youre not supposed to be using it on a /dev/input/event* interface though, rather a /dev/input/js* device.  I tried it on a completely clean install and it worked fine without installing anything really except "apt-get install joystick" to get jstest

doing "jstest /dev/input/js0" for me gives an output for the states of the various axes and buttons

The only problem I can see you might be having is needing to press the PS button to initiate communication, or perhaps using the wrong device name.

Also, for me , the controller doesnt seem to work when its stuck in blinky bluetooth pairing mode, and defiantly wouldnt work when its actually paired with something.

On a similar note though does anyone know how to get the f***er to work with bluetooth now that bluetooth has changed away from hidd to bluetoothd?

---


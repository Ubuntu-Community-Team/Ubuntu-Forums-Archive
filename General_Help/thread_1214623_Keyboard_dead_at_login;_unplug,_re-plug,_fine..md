---
title: "Keyboard dead at login; unplug, re-plug, fine."
date: 2009-07-16
forum: General Help
---

### Post by Bucky Ball on 2009-07-16
I have seen a lot of posts and people asking this question but nothing so far that fixes it.

The subject of this post says it all: boot up, I can select what I want to boot at grub, gets to the login and the usb keyboard is dead. Unplug it, plug it back in, it's fine until I switch off (doesn't seem to happen with a restart from memory). Have tried other keyboards.

I will post my dmesg when next it happens.

I am working on my in-law's which I built six months ago (and haven't seen since) and am only here for a couple of days so any help greatly appreciated.

:)

* This machine is also 8.04
** And to add to that, I have checked out the BIOS and it shows 1 usb mouse and 1 usb keyboard present. They are blanked out and unchangeable.

---

### Post by Bucky Ball on 2009-07-16
Also, this from dmesg:

```
[  168.439056] usb 4-4: USB disconnect, address 3
[  170.289363] usb 4-4: new low speed USB device using ohci_hcd and address 4
[  170.505208] usb 4-4: configuration #1 chosen from 1 choice
[  170.516295] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/input/input7
[  170.561544] input,hidraw1: USB HID v1.11 Keyboard [Microsoft Wired Keyboard 600] on usb-0000:00:04.0-4
[  170.573185] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.1/input/input8
[  170.633447] input,hidraw2: USB HID v1.11 Device [Microsoft Wired Keyboard 600] on usb-0000:00:04.0-4
```Is input hidraw1 *and* 2 correct? From what I can work out, is it disconnecting address 3 then loading the keyboard twice? It is the correct keyboard identified, BTW.

---

### Post by Bucky Ball on 2009-07-16
Sorry to bump ...

---

### Post by savsav on 2009-07-21
This is also happening to me .

I have kubuntu 9.04

---

### Post by Bucky Ball on 2009-07-21
Okay, it fixed itself when I added this option for some reason, in /etc/X11/xorg.conf:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
       ** Option         "CoreKeyboard"**
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
```At least I think this is what fixed it, either way it's fixed. You might need "xorg" after it. Don't remember. I am now 750kms away from that machine so can't really check at the moment. Good luck. :)

---


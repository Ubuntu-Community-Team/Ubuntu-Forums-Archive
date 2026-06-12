---
title: "Keyboard problem"
date: 2011-05-25
forum: General Help
---

### Post by rapattack1 on 2011-05-25
Hi i got a thing pop up that said something about the keyboard...something about enabling or disabling something. I was trying to close it so as not to commit to whatever it is but it would not close and now whenever i boot up i can't type anything. A quite temporary solution is to unplug and replug the usb keyboard then it works for that one session. I was doing dozens of things when the thing popped up so i don't know what it was. I was online at the time and never saw that thing before. I think applet is the word for it. This only happened yesterday or the day before. Does anyone know what this could be?

---

### Post by stinkeye on 2011-05-25
Check in keyboard preferences that you haven't enabled some of the accessibility features.
You can also set the keyboard layout back to default in the layouts tab.

---

### Post by rapattack1 on 2011-05-25
OK this is my preferences. Do i uncheck the things like in your capture? Don't really understand this stuff. I didn't change it so i don't know how it got that way. The layouts tab...i can't see anything about defaults...

---

### Post by stinkeye on 2011-05-25
There are some shortcut keys that will turn the features on.
Unchecking the top option will disable you accidently toggling the feature on.

You could also make sure accessibility options are set back to default by running in the terminal..
```
gconftool-2 --recursive-unset /desktop/gnome/accessibility/keyboard
```

---

### Post by rapattack1 on 2011-05-26
OK sorry there is no change after unchecking that box and using that command.
I also clicked on that defaults box and rebooted. Problem is unchanged :0(

---

### Post by stinkeye on 2011-05-26
OK, I'm just guessing at what you may have changed.
So when this happens, if you hold down a key does it start typing.

---

### Post by rapattack1 on 2011-05-26
I definately didn't change anything except for that moment i don't know what happened. I was trying to close it.
I don't know what you mean by hold down a key. I try to type and i get a sound like 'no'....

Just realised your from Oz too lol. Still got the same problem today :0)

---

### Post by rapattack1 on 2011-06-02
Is there any chance this is now a process that happens during bootup or startup? I don't know really what i am talking about but would like some help. Gets very annoying having to get up everytime and replug the usb kb after booting into the system

carla@carla-desktop:~$ lsusb
Bus 002 Device 006: ID 0e8f:0021 GreenAsia Inc. 
Bus 002 Device 005: ID 17a0:0001  
Bus 002 Device 004: ID 04a9:2207 Canon, Inc. CanoScan 1220U
Bus 002 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
carla@carla-desktop:~$ dmesg | grep usb
[    0.252841] usbcore: registered new interface driver usbfs
[    0.252850] usbcore: registered new interface driver hub
[    0.253082] usbcore: registered new device driver usb
[    0.385920] usb usb1: configuration #1 chosen from 1 choice
[    0.474453] usb usb2: configuration #1 chosen from 1 choice
[    1.244357] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    1.462555] usb 2-1: configuration #1 chosen from 1 choice
[    1.768022] usb 2-2: new low speed USB device using ohci_hcd and address 3
[    1.981559] usb 2-2: configuration #1 chosen from 1 choice
[    1.987959] usbcore: registered new interface driver hiddev
[    1.992613] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[    1.992664] generic-usb 0003:04F3:0230.0001: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:02.0-1/input0
[    1.997629] input: GASIA USB KB V11 as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input4
[    1.997669] generic-usb 0003:0E8F:0021.0002: input,hidraw1: USB HID v1.10 Keyboard [GASIA USB KB V11] on usb-0000:00:02.0-2/input0
[    2.009573] input: GASIA USB KB V11 as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input5
[    2.009611] generic-usb 0003:0E8F:0021.0003: input,hidraw2: USB HID v1.10 Device [GASIA USB KB V11] on usb-0000:00:02.0-2/input1
[    2.009623] usbcore: registered new interface driver usbhid
[    2.009624] usbhid: v2.6:USB HID core driver
[    2.288021] usb 2-3: new full speed USB device using ohci_hcd and address 4
[    2.510572] usb 2-3: configuration #1 chosen from 1 choice
[    2.824018] usb 2-8: new full speed USB device using ohci_hcd and address 5
[    3.042616] usb 2-8: configuration #1 chosen from 1 choice
[   12.911066] usbcore: registered new interface driver snd-usb-audio
[  196.227397] usb 2-2: USB disconnect, address 3
[  199.080064] usb 2-2: new low speed USB device using ohci_hcd and address 6
[  199.293467] usb 2-2: configuration #1 chosen from 1 choice
[  199.303757] input: GASIA USB KB V11 as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input6
[  199.303911] generic-usb 0003:0E8F:0021.0004: input,hidraw1: USB HID v1.10 Keyboard [GASIA USB KB V11] on usb-0000:00:02.0-2/input0
[  199.318298] input: GASIA USB KB V11 as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/input/input7
[  199.318354] generic-usb 0003:0E8F:0021.0005: input,hidraw2: USB HID v1.10 Device [GASIA USB KB V11] on usb-0000:00:02.0-2/input1

The latest thing i noticed is that the keyboard works when logging in with my username and password but as soon as i go to type in a url in the browser i can't.

---

### Post by rapattack1 on 2011-06-08
Well after the 'update manager' gave me some updates a couple of times the keyboard problem is gone.....i hope for good!!!

---


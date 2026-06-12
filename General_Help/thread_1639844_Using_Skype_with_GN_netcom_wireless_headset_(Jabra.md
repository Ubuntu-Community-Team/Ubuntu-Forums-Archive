---
title: "Using Skype with GN netcom wireless headset (Jabra gn9350)"
date: 2010-12-07
forum: General Help
---

### Post by zainka on 2010-12-07
Hi

I try to use the GN Netcom GN9350 wireless headset in Skype. Installing the device, or more correctly just plugging it in to the USB hole,  shows the following in dmesg.

    [quote="dmesg after plugin device GN9350"][482522.636015] usb 3-2: new full speed USB device using uhci_hcd and address 3
    [482522.834699] input: GN Netcom GN 9350 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.3/input/input4
    [482522.834815] generic-usb 0003:0B0E:9350.0003: input,hidraw2: USB HID v1.00 Device [GN Netcom GN 9350] on usb-0000:00:1d.1-2/input3
    [482523.620644] 3:1:1: endpoint lacks sample rate attribute bit, cannot set.
    [482523.622625] 3:2:1: endpoint lacks sample rate attribute bit, cannot set.
    [482523.661146] usbcore: registered new interface driver snd-usb-audio
    [482524.317657] 3:2:1: endpoint lacks sample rate attribute bit, cannot set.
    [482524.320640] 3:1:1: endpoint lacks sample rate attribute bit, cannot set.
    [482524.477672] 3:1:1: endpoint lacks sample rate attribute bit, cannot set.
    [482524.511668] 3:2:1: endpoint lacks sample rate attribute bit, cannot set.
    [482524.957657] 3:1:1: endpoint lacks sample rate attribute bit, cannot set.
    [482800.161090] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

    And lsusb said
    Bus 003 Device 003: ID 0b0e:9350 GN Netcom

[/quote]

So its there, however, I do not know if the "endpoint lacks sample rate attribute bit" is related or is related but one do not need to concern about it, etc.
Atleast there is assigned an driver, i.e "registered new interface driver snd-usb-audio", so the device should be up and I should be able to chose it somehow. However Skype does not show any other options but Pulse Audio Server and all sound goes offcourse by default to my headset and mic I/O.

I would like to route audio and mic to/from gn9350 for skype only.

I am using XFCE

---

### Post by sforces on 2011-07-15
Did you ever get your issue resolved?

I'm on Ubuntu 11.04 and have the same GN 9350 headset and do have it working just fine with Skype. But the oddest thing is when I press on the button on the headset's base to switch it to use USB, it logs me off from my Ubuntu session. Then when I put it back on the base, it automatically switches back to the phone and again logs me off from my Ubuntu session.](*,)

---


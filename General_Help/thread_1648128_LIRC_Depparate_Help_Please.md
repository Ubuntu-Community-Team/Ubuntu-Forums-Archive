---
title: "LIRC Depparate Help Please"
date: 2010-12-18
forum: General Help
---

### Post by ptmuldoon on 2010-12-18
I've been at this for over 3 days now, and completely ready to toss in the towel, i'm so frustrated.

I have a custom build box, that has a TopSeed Transreceiver included in the case, and can't get ANY remote to work with it.  I'm probably doing something wrong as I'm still new with Ubuntu, and have read all sorts of Wiki's to no eval in getting thing to work.

I've purge and removed lirc half a dozen times, and just don't know what else to do.  This is all on a Fresh 10.10 install.  I'll even reinstall the entire OS again if helps.

The output of lsusb is as follows;

> 
Bus 004 Device 003: ID 1784:0011 TopSeed Technology Corp. 
Bus 004 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and dmesg | grep -i usb shows this:
> 
[    0.530527] usbcore: registered new interface driver usbfs
[    0.530527] usbcore: registered new interface driver hub
[    0.530527] usbcore: registered new device driver usb
[    0.761479] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.762620] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.771782] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.772092] hub 1-0:1.0: USB hub found
[    0.773364] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.783784] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.784076] hub 2-0:1.0: USB hub found
[    0.784259] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.785391] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.842113] hub 3-0:1.0: USB hub found
[    0.843695] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.898213] hub 4-0:1.0: USB hub found
[    0.898413] uhci_hcd: USB Universal Host Controller Interface driver
[    1.525045] usb 4-3: new low speed USB device using ohci_hcd and address 2
[    1.841007] usbcore: registered new interface driver hiddev
[    1.849521] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:06.0/usb4/4-3/4-3:1.0/input/input2
[    1.850354] generic-usb 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:06.0-3/input0
[    1.850627] usbcore: registered new interface driver usbhid
[    1.850637] usbhid: USB HID core driver
[    2.028052] usb 4-4: new full speed USB device using ohci_hcd and address 3
[    2.523767] mceusb 4-4:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver on usb4:3
[    2.523858] usbcore: registered new interface driver mceusb
[    2.544026] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    2.544040] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    2.568085] usb 3-3: new low speed USB device using ohci_hcd and address 2
[    2.588410] usbcore: registered new interface driver lirc_mceusb
[    2.808360] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3:1.0/input/input4
[    2.808683] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:04.0-3/input0
[    2.907839] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3:1.1/input/input5
[    2.908230] generic-usb 0003:413C:2003.0003: input,hidraw2: USB HID v1.10 Device [DELL DELL USB Keyboard] on usb-0000:00:04.0-3/input1


Again, I'm desperate for any help anyone can give this newbie.

Thanks
PT

---


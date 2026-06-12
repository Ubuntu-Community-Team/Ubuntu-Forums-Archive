---
title: "usb_set_interface failed - logitech usb devices"
date: 2010-05-16
forum: General Help
---

### Post by jipajapa on 2010-05-16
Hello,

I'm not sure if this is the correct category, but none of the others seemed appropriate. I'm having problems getting multiple usb devices to play nicely together. I'm using the following usb devices:

ralink rt2870 usb wireless
Logitech wireless keyboard - K350 
Logitech wireless mouse M305
Logitech clearchat pro wireless usb headset

uname -a
```
Linux bistro 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686

```lsusb looks like this

$ lsusb
```
Bus 004 Device 003: ID 046d:0a0b Logitech, Inc. 
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 003: ID 148f:2870 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The system begins to hang and applications start to freeze if I try to use all the usb devices listed above (e.g. everything works fine until I plug in the headset).  The following messages show up in kernel.log

```
May 16 19:11:33 bistro kernel: [  671.076990] usbcore: deregistering interface driver snd-usb-audio
May 16 19:12:34 bistro kernel: [    0.247851] usbcore: registered new interface driver usbfs
May 16 19:12:34 bistro kernel: [    0.247861] usbcore: registered new interface driver hub
May 16 19:12:34 bistro kernel: [    0.247879] usbcore: registered new device driver usb
May 16 19:12:34 bistro kernel: [    0.427954] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May 16 19:12:34 bistro kernel: [    0.428359] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
May 16 19:12:34 bistro kernel: [    0.477345] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
May 16 19:12:34 bistro kernel: [    0.477415] usb usb1: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    0.477439] hub 1-0:1.0: USB hub found
May 16 19:12:34 bistro kernel: [    0.477876] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
May 16 19:12:34 bistro kernel: [    0.521354] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
May 16 19:12:34 bistro kernel: [    0.521409] usb usb2: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    0.521430] hub 2-0:1.0: USB hub found
May 16 19:12:34 bistro kernel: [    0.521477] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May 16 19:12:34 bistro kernel: [    0.521871] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
May 16 19:12:34 bistro kernel: [    0.577656] usb usb3: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    0.577681] hub 3-0:1.0: USB hub found
May 16 19:12:34 bistro kernel: [    0.578182] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
May 16 19:12:34 bistro kernel: [    0.654301] usb usb4: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    0.654326] hub 4-0:1.0: USB hub found
May 16 19:12:34 bistro kernel: [    0.654388] uhci_hcd: USB Universal Host Controller Interface driver
May 16 19:12:34 bistro kernel: [    1.075554] usb 2-2: new high speed USB device using ehci_hcd and address 3
May 16 19:12:34 bistro kernel: [    1.136080] hub 2-0:1.0: unable to enumerate USB device on port 2
May 16 19:12:34 bistro kernel: [    1.372043] usb 2-4: new high speed USB device using ehci_hcd and address 5
May 16 19:12:34 bistro kernel: [    1.507432] usb 2-4: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    1.514236] Initializing USB Mass Storage driver...
May 16 19:12:34 bistro kernel: [    1.514332] scsi8 : SCSI emulation for USB Mass Storage devices
May 16 19:12:34 bistro kernel: [    1.514414] usbcore: registered new interface driver usb-storage
May 16 19:12:34 bistro kernel: [    1.514417] USB Mass Storage support registered.
May 16 19:12:34 bistro kernel: [    1.514499] usb-storage: device found at 5
May 16 19:12:34 bistro kernel: [    1.514501] usb-storage: waiting for device to settle before scanning
May 16 19:12:34 bistro kernel: [    1.796042] usb 4-1: new full speed USB device using ohci_hcd and address 2
May 16 19:12:34 bistro kernel: [    2.017336] usb 4-1: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    2.324041] usb 4-2: new full speed USB device using ohci_hcd and address 3
May 16 19:12:34 bistro kernel: [    2.527231] usb 4-2: not running at top speed; connect to a high speed hub
May 16 19:12:34 bistro kernel: [    2.554318] usb 4-2: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    2.864043] usb 4-3: new full speed USB device using ohci_hcd and address 4
May 16 19:12:34 bistro kernel: [    3.088312] usb 4-3: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    3.396042] usb 3-1: new full speed USB device using ohci_hcd and address 2
May 16 19:12:34 bistro kernel: [    3.617644] usb 3-1: configuration #1 chosen from 1 choice
May 16 19:12:34 bistro kernel: [    5.089172] usbcore: registered new interface driver hiddev
May 16 19:12:34 bistro kernel: [    5.094374] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/in
put/input3
May 16 19:12:34 bistro kernel: [    5.094471] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Re
ceiver] on usb-0000:00:04.0-1/input0
May 16 19:12:34 bistro kernel: [    5.105319] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.1/in
put/input4
May 16 19:12:34 bistro kernel: [    5.105451] generic-usb 0003:046D:C52F.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logit
ech USB Receiver] on usb-0000:00:04.0-1/input1
May 16 19:12:34 bistro kernel: [    5.112264] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-
3:1.3/input/input5
May 16 19:12:34 bistro kernel: [    5.112360] generic-usb 0003:046D:0A0B.0003: input,hidraw2: USB HID v1.00 Device [Logitech Logit
ech USB Headset] on usb-0000:00:04.0-3/input3
May 16 19:12:34 bistro kernel: [    5.116762] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/in
put/input6
May 16 19:12:34 bistro kernel: [    5.116850] generic-usb 0003:046D:C52B.0004: input,hidraw3: USB HID v1.11 Keyboard [Logitech USB
 Receiver] on usb-0000:00:02.0-1/input0
May 16 19:12:34 bistro kernel: [    5.123886] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.1/in
put/input7
May 16 19:12:34 bistro kernel: [    5.124053] generic-usb 0003:046D:C52B.0005: input,hiddev97,hidraw4: USB HID v1.11 Mouse [Logite
ch USB Receiver] on usb-0000:00:02.0-1/input1
May 16 19:12:34 bistro kernel: [    5.135639] generic-usb 0003:046D:C52B.0006: hiddev98,hidraw5: USB HID v1.11 Device [Logitech US
B Receiver] on usb-0000:00:02.0-1/input2
May 16 19:12:34 bistro kernel: [    5.135668] usbcore: registered new interface driver usbhid
May 16 19:12:34 bistro kernel: [    5.135671] usbhid: v2.6:USB HID core driver
May 16 19:12:34 bistro kernel: [    5.448392] rtusb init --->
May 16 19:12:34 bistro kernel: [    5.452195] usbcore: registered new interface driver rt2870
May 16 19:12:34 bistro kernel: [    6.512785] usb-storage: device scan complete
May 16 19:12:34 bistro kernel: [    6.514147] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
May 16 19:12:34 bistro kernel: [    6.514628] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
May 16 19:12:34 bistro kernel: [    6.515124] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
May 16 19:12:34 bistro kernel: [    6.515623] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
May 16 19:12:44 bistro kernel: [   20.447997] -->RTUSBVenderReset
May 16 19:12:44 bistro kernel: [   20.450998] <--RTUSBVenderReset
May 16 19:14:58 bistro kernel: [    0.247840] usbcore: registered new interface driver usbfs
May 16 19:14:58 bistro kernel: [    0.247851] usbcore: registered new interface driver hub
May 16 19:14:58 bistro kernel: [    0.247869] usbcore: registered new device driver usb
May 16 19:14:58 bistro kernel: [    0.427940] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May 16 19:14:58 bistro kernel: [    0.428343] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
May 16 19:14:58 bistro kernel: [    0.477329] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
May 16 19:14:58 bistro kernel: [    0.477399] usb usb1: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    0.477422] hub 1-0:1.0: USB hub found
May 16 19:14:58 bistro kernel: [    0.477857] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
May 16 19:14:58 bistro kernel: [    0.521336] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
May 16 19:14:58 bistro kernel: [    0.521392] usb usb2: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    0.521413] hub 2-0:1.0: USB hub found
May 16 19:14:58 bistro kernel: [    0.521460] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May 16 19:14:58 bistro kernel: [    0.521854] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
May 16 19:14:58 bistro kernel: [    0.577778] usb usb3: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    0.577804] hub 3-0:1.0: USB hub found
May 16 19:14:58 bistro kernel: [    0.578305] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
May 16 19:14:58 bistro kernel: [    0.654285] usb usb4: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    0.654310] hub 4-0:1.0: USB hub found
May 16 19:14:58 bistro kernel: [    0.654371] uhci_hcd: USB Universal Host Controller Interface driver
May 16 19:14:58 bistro kernel: [    1.047614] usb 2-2: new high speed USB device using ehci_hcd and address 3
May 16 19:14:58 bistro kernel: [    1.181440] usb 2-2: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    1.404044] usb 2-4: new high speed USB device using ehci_hcd and address 5
May 16 19:14:58 bistro kernel: [    1.539448] usb 2-4: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    1.546150] Initializing USB Mass Storage driver...
May 16 19:14:58 bistro kernel: [    1.546260] scsi8 : SCSI emulation for USB Mass Storage devices
May 16 19:14:58 bistro kernel: [    1.546336] usbcore: registered new interface driver usb-storage
May 16 19:14:58 bistro kernel: [    1.546338] USB Mass Storage support registered.
May 16 19:14:58 bistro kernel: [    1.546420] usb-storage: device found at 5
May 16 19:14:58 bistro kernel: [    1.546422] usb-storage: waiting for device to settle before scanning
May 16 19:14:58 bistro kernel: [    1.844058] usb 3-1: new full speed USB device using ohci_hcd and address 2
May 16 19:14:58 bistro kernel: [    2.065795] usb 3-1: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    2.372042] usb 4-1: new full speed USB device using ohci_hcd and address 2
May 16 19:14:58 bistro kernel: [    2.593357] usb 4-1: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    2.900042] usb 4-3: new full speed USB device using ohci_hcd and address 3
May 16 19:14:58 bistro kernel: [    3.124353] usb 4-3: configuration #1 chosen from 1 choice
May 16 19:14:58 bistro kernel: [    5.106974] usbcore: registered new interface driver hiddev
May 16 19:14:58 bistro kernel: [    5.113078] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.0/in
put/input4
May 16 19:14:58 bistro kernel: [    5.113705] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB
 Receiver] on usb-0000:00:02.0-1/input0
May 16 19:14:58 bistro kernel: [    5.120125] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb3/3-1/3-1:1.1/in
put/input5
May 16 19:14:58 bistro kernel: [    5.120260] generic-usb 0003:046D:C52B.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logite
ch USB Receiver] on usb-0000:00:02.0-1/input1
May 16 19:14:58 bistro kernel: [    5.131875] generic-usb 0003:046D:C52B.0003: hiddev97,hidraw2: USB HID v1.11 Device [Logitech US
B Receiver] on usb-0000:00:02.0-1/input2
May 16 19:14:58 bistro kernel: [    5.136487] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/in
put/input6
May 16 19:14:58 bistro kernel: [    5.136586] generic-usb 0003:046D:C52F.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Re
ceiver] on usb-0000:00:04.0-1/input0
May 16 19:14:58 bistro kernel: [    5.147419] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.1/in
put/input7
May 16 19:14:58 bistro kernel: [    5.147527] generic-usb 0003:046D:C52F.0005: input,hiddev98,hidraw4: USB HID v1.11 Device [Logit
ech USB Receiver] on usb-0000:00:04.0-1/input1
May 16 19:14:58 bistro kernel: [    5.154365] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-
3:1.3/input/input8
May 16 19:14:58 bistro kernel: [    5.154470] generic-usb 0003:046D:0A0B.0006: input,hidraw5: USB HID v1.00 Device [Logitech Logit
ech USB Headset] on usb-0000:00:04.0-3/input3
May 16 19:14:58 bistro kernel: [    5.154493] usbcore: registered new interface driver usbhid
May 16 19:14:58 bistro kernel: [    5.154496] usbhid: v2.6:USB HID core driver
May 16 19:14:58 bistro kernel: [    5.340807] rtusb init --->
May 16 19:14:58 bistro kernel: [    5.342694] usbcore: registered new interface driver rt2870
May 16 19:14:58 bistro kernel: [    6.544789] usb-storage: device scan complete
May 16 19:14:58 bistro kernel: [    6.546286] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
May 16 19:14:58 bistro kernel: [    6.546754] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
May 16 19:14:58 bistro kernel: [    6.547255] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
May 16 19:14:58 bistro kernel: [    6.547754] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
May 16 19:14:58 bistro kernel: [    6.624678] usbcore: registered new interface driver snd-usb-audio
May 16 19:15:02 bistro kernel: [   14.485830] -->RTUSBVenderReset
May 16 19:15:02 bistro kernel: [   14.485955] <--RTUSBVenderReset
May 16 19:28:39 bistro kernel: [  830.963518] usb 4-3: USB disconnect, address 3
May 16 19:30:48 bistro kernel: [  960.336182]  [<c044646d>] usb_kill_urb+0x6d/0xa0
May 16 19:30:48 bistro kernel: [  960.336205]  [<c0445057>] usb_hcd_flush_endpoint+0xb7/0x110
May 16 19:30:48 bistro kernel: [  960.336214]  [<c0446f5e>] usb_disable_endpoint+0x4e/0x80
May 16 19:30:48 bistro kernel: [  960.336223]  [<c0446fb6>] usb_disable_device+0x26/0x100
May 16 19:30:48 bistro kernel: [  960.336231]  [<c0441aae>] usb_disconnect+0x9e/0x120
May 16 19:30:48 bistro kernel: [  960.336250]  [<c0447c55>] ? usb_control_msg+0xd5/0x130
May 16 19:32:48 bistro kernel: [ 1080.336164]  [<c044646d>] usb_kill_urb+0x6d/0xa0
May 16 19:32:48 bistro kernel: [ 1080.336186]  [<c0445057>] usb_hcd_flush_endpoint+0xb7/0x110
May 16 19:32:48 bistro kernel: [ 1080.336196]  [<c0446f5e>] usb_disable_endpoint+0x4e/0x80
May 16 19:32:48 bistro kernel: [ 1080.336205]  [<c0446fb6>] usb_disable_device+0x26/0x100
May 16 19:32:48 bistro kernel: [ 1080.336213]  [<c0441aae>] usb_disconnect+0x9e/0x120
May 16 19:32:48 bistro kernel: [ 1080.336232]  [<c0447c55>] ? usb_control_msg+0xd5/0x130
May 16 19:34:48 bistro kernel: [ 1200.336177]  [<c044646d>] usb_kill_urb+0x6d/0xa0
May 16 19:34:48 bistro kernel: [ 1200.336199]  [<c0445057>] usb_hcd_flush_endpoint+0xb7/0x110
May 16 19:34:48 bistro kernel: [ 1200.336208]  [<c0446f5e>] usb_disable_endpoint+0x4e/0x80
May 16 19:34:48 bistro kernel: [ 1200.336217]  [<c0446fb6>] usb_disable_device+0x26/0x100
May 16 19:34:48 bistro kernel: [ 1200.336225]  [<c0441aae>] usb_disconnect+0x9e/0x120
May 16 19:34:48 bistro kernel: [ 1200.336244]  [<c0447c55>] ? usb_control_msg+0xd5/0x130
May 16 19:36:48 bistro kernel: [ 1320.336157]  [<c044646d>] usb_kill_urb+0x6d/0xa0
May 16 19:36:48 bistro kernel: [ 1320.336180]  [<c0445057>] usb_hcd_flush_endpoint+0xb7/0x110
May 16 19:36:48 bistro kernel: [ 1320.336189]  [<c0446f5e>] usb_disable_endpoint+0x4e/0x80
May 16 19:36:48 bistro kernel: [ 1320.336199]  [<c0446fb6>] usb_disable_device+0x26/0x100
May 16 19:36:48 bistro kernel: [ 1320.336207]  [<c0441aae>] usb_disconnect+0x9e/0x120
May 16 19:36:48 bistro kernel: [ 1320.336225]  [<c0447c55>] ? usb_control_msg+0xd5/0x130
May 16 19:38:48 bistro kernel: [ 1440.336140]  [<c044646d>] usb_kill_urb+0x6d/0xa0
May 16 19:38:48 bistro kernel: [ 1440.336163]  [<c0445057>] usb_hcd_flush_endpoint+0xb7/0x110
May 16 19:38:48 bistro kernel: [ 1440.336172]  [<c0446f5e>] usb_disable_endpoint+0x4e/0x80
May 16 19:38:48 bistro kernel: [ 1440.336181]  [<c0446fb6>] usb_disable_device+0x26/0x100
May 16 19:38:48 bistro kernel: [ 1440.336189]  [<c0441aae>] usb_disconnect+0x9e/0x120
May 16 19:38:48 bistro kernel: [ 1440.336208]  [<c0447c55>] ? usb_control_msg+0xd5/0x130
May 16 19:40:48 bistro kernel: [ 1560.336166]  [<c044646d>] usb_kill_urb+0x6d/0xa0
May 16 19:40:48 bistro kernel: [ 1560.336188]  [<c0445057>] usb_hcd_flush_endpoint+0xb7/0x110
May 16 19:40:48 bistro kernel: [ 1560.336198]  [<c0446f5e>] usb_disable_endpoint+0x4e/0x80
May 16 19:40:48 bistro kernel: [ 1560.336207]  [<c0446fb6>] usb_disable_device+0x26/0x100
May 16 19:40:48 bistro kernel: [ 1560.336215]  [<c0441aae>] usb_disconnect+0x9e/0x120
May 16 19:40:48 bistro kernel: [ 1560.336234]  [<c0447c55>] ? usb_control_msg+0xd5/0x130

```There are also a zillion or so of these
```
[  892.140143] 3:2:1: usb_set_interface failed
```Any suggestions would be appreciated. 

Cheers,
Sam

---

### Post by AlexeyTyapkin on 2010-07-14
it is nano reciever failure. Contact Logitech support they'll replace it.

---


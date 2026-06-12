---
title: "need high-speed usb, not full-speed"
date: 2010-01-08
forum: General Help
---

### Post by moparisthebest on 2010-01-08
I have a WinTV-HVR950 that works fine to watch TV on the computer except when ubuntu decides to detect it as a full-speed (USB1) and not a high-speed (USB2) device.  I am plugging it in the same port and the same way as I did before, but it doesn't work the vast majority of the time, and I haven't been able to make it work at all recently.

Here is the problem (from /var/log/messages):
```
what it says now:
Jan  8 17:50:47 killer-linux kernel: [ 3999.801284] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jan  8 17:50:47 killer-linux kernel: [ 3999.947066] usb 4-1: not running at top speed; connect to a high speed hub
Jan  8 17:50:47 killer-linux kernel: [ 3999.978166] usb 4-1: configuration #1 chosen from 1 choice
Jan  8 17:50:47 killer-linux kernel: [ 3999.981129] em28xx: New device WinTV HVR-980 @ 12 Mbps (2040:6513, interface 0, class 0)
Jan  8 17:50:47 killer-linux kernel: [ 3999.981132] em28xx: Device initialization failed.
Jan  8 17:50:47 killer-linux kernel: [ 3999.981134] em28xx: Device must be connected to a high-speed USB 2.0 port.

What it used to say:
Jan  7 20:44:20 killer-linux kernel: [  302.680043] usb 1-2: new high speed USB device using ehci_hcd and address 3
Jan  7 20:44:20 killer-linux kernel: [  302.835503] usb 1-2: configuration #1 chosen from 1 choice
Jan  7 20:44:20 killer-linux kernel: [  302.913695] Linux video capture interface: v2.00
Jan  7 20:44:20 killer-linux kernel: [  302.959542] em28xx: New device WinTV HVR-980 @ 480 Mbps (2040:6513, interface 0, class 0)
Jan  7 20:44:20 killer-linux kernel: [  302.959818] em28xx #0: chip ID is em2882/em2883
Jan  7 20:44:21 killer-linux kernel: [  303.159042] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 13 65 d0 12 5c 03 82 1e 6a 18
Jan  7 20:44:21 killer-linux kernel: [  303.159064] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159073] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159082] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159091] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159100] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159108] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
Jan  7 20:44:21 killer-linux kernel: [  303.159117] em28xx #0: i2c eeprom 70: 32 00 38 00 37 00 33 00 30 00 31 00 39 00 30 00
Jan  7 20:44:21 killer-linux kernel: [  303.159126] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
Jan  7 20:44:21 killer-linux kernel: [  303.159134] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 38 00 30 00 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159143] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
Jan  7 20:44:21 killer-linux kernel: [  303.159152] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 4e 8b
Jan  7 20:44:21 killer-linux kernel: [  303.159161] em28xx #0: i2c eeprom c0: 21 f0 74 02 01 00 01 79 ac 00 00 00 00 00 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159169] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
Jan  7 20:44:21 killer-linux kernel: [  303.159178] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 4e 8b
Jan  7 20:44:21 killer-linux kernel: [  303.159187] em28xx #0: i2c eeprom f0: 21 f0 74 02 01 00 01 79 ac 00 00 00 00 00 00 00
Jan  7 20:44:21 killer-linux kernel: [  303.159196] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x1a8925dd
Jan  7 20:44:21 killer-linux kernel: [  303.159198] em28xx #0: EEPROM info:
Jan  7 20:44:21 killer-linux kernel: [  303.159199] em28xx #0:	AC97 audio (5 sample rates)
Jan  7 20:44:21 killer-linux kernel: [  303.159201] em28xx #0:	500mA max power
Jan  7 20:44:21 killer-linux kernel: [  303.159203] em28xx #0:	Table at 0x24, strings=0x1e82, 0x186a, 0x0000
Jan  7 20:44:21 killer-linux kernel: [  303.159916] em28xx #0: Identified as Hauppauge WinTV HVR 950 (card=16)
Jan  7 20:44:21 killer-linux kernel: [  303.161861] tveeprom 4-0050: Hauppauge model 65201, rev A1C0, serial# 2198350
Jan  7 20:44:21 killer-linux kernel: [  303.161865] tveeprom 4-0050: tuner model is Xceive XC3028 (idx 120, type 71)
Jan  7 20:44:21 killer-linux kernel: [  303.161868] tveeprom 4-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
Jan  7 20:44:21 killer-linux kernel: [  303.161870] tveeprom 4-0050: audio processor is None (idx 0)
Jan  7 20:44:21 killer-linux kernel: [  303.161872] tveeprom 4-0050: has radio
Jan  7 20:44:21 killer-linux kernel: [  303.164834] tvp5150 4-005c: chip found @ 0xb8 (em28xx #0)
Jan  7 20:44:21 killer-linux kernel: [  303.179471] tuner 4-0061: chip found @ 0xc2 (em28xx #0)
Jan  7 20:44:21 killer-linux kernel: [  303.223922] xc2028 4-0061: creating new instance
Jan  7 20:44:21 killer-linux kernel: [  303.223925] xc2028 4-0061: type set to XCeive xc2028/xc3028 tuner
Jan  7 20:44:21 killer-linux kernel: [  303.223934] usb 1-2: firmware: requesting xc3028-v27.fw
Jan  7 20:44:21 killer-linux kernel: [  303.247867] xc2028 4-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Jan  7 20:44:21 killer-linux kernel: [  303.300060] xc2028 4-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
Jan  7 20:44:22 killer-linux kernel: [  304.240019] xc2028 4-0061: Loading firmware for type=MTS (4), id 000000000000b700.
Jan  7 20:44:22 killer-linux kernel: [  304.255647] xc2028 4-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
Jan  7 20:44:22 killer-linux kernel: [  304.460123] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/input/input6
Jan  7 20:44:22 killer-linux kernel: [  304.460236] em28xx #0: Config register raw data: 0xd0
Jan  7 20:44:22 killer-linux kernel: [  304.460984] em28xx #0: AC97 vendor ID = 0xffffffff
Jan  7 20:44:22 killer-linux kernel: [  304.461359] em28xx #0: AC97 features = 0x6a90
Jan  7 20:44:22 killer-linux kernel: [  304.461361] em28xx #0: Empia 202 AC97 audio processor detected
Jan  7 20:44:22 killer-linux kernel: [  304.630437] tvp5150 4-005c: tvp5150am1 detected.
Jan  7 20:44:22 killer-linux kernel: [  304.730981] em28xx #0: v4l2 driver version 0.1.2
Jan  7 20:44:22 killer-linux kernel: [  304.836993] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
Jan  7 20:44:22 killer-linux kernel: [  304.850106] usbcore: registered new interface driver em28xx
Jan  7 20:44:22 killer-linux kernel: [  304.850111] em28xx driver loaded
Jan  7 20:44:22 killer-linux kernel: [  304.867545] em28xx-audio.c: probing for em28x1 non standard usbaudio
Jan  7 20:44:22 killer-linux kernel: [  304.867548] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
Jan  7 20:44:22 killer-linux kernel: [  304.867870] Em28xx: Initialized (Em28xx Audio Extension) extension
Jan  7 20:44:22 killer-linux kernel: [  304.990346] tvp5150 4-005c: *** unknown tvp5150 chip detected.
Jan  7 20:44:22 killer-linux kernel: [  304.990348] tvp5150 4-005c: *** Rom ver is 62.4
Jan  7 20:44:22 killer-linux kernel: [  305.073204] xc2028 4-0061: attaching existing instance
Jan  7 20:44:22 killer-linux kernel: [  305.073207] xc2028 4-0061: type set to XCeive xc2028/xc3028 tuner
Jan  7 20:44:22 killer-linux kernel: [  305.073209] em28xx #0/2: xc3028 attached
Jan  7 20:44:22 killer-linux kernel: [  305.073212] DVB: registering new adapter (em28xx #0)
Jan  7 20:44:22 killer-linux kernel: [  305.073215] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
Jan  7 20:44:22 killer-linux kernel: [  305.073466] Successfully loaded em28xx-dvb
Jan  7 20:44:22 killer-linux kernel: [  305.073468] Em28xx: Initialized (Em28xx dvb Extension) extension
Jan  7 20:46:34 killer-linux kernel: [  436.980490] tvp5150 4-005c: tvp5150am1 detected.
Jan  7 20:46:35 killer-linux kernel: [  437.280033] xc2028 4-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
Jan  7 20:46:36 killer-linux kernel: [  438.240169] xc2028 4-0061: Loading firmware for type=MTS (4), id 000000000000b700.
Jan  7 20:46:36 killer-linux kernel: [  438.255661] xc2028 4-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
```

The important thing is it used to accept it as a high-speed device and now it only wants to accept it as a full-speed device.  The simple solution here would be to blacklist ohci_hcd from being loaded and it would have to use ehci_hcd, but ubuntu in her infinite wisdom has them compiled into the kernel so I don't have that option.  Any help please? :D

---

### Post by ibuclaw on 2010-01-08
Hmm - sounds like a job for udev...

What is the ID of the device?
```
lsusb
```

edit:
> 
Jan  7 20:44:20 killer-linux kernel: [  302.680043] **usb 1-2**: new high speed USB device using ehci_hcd and address 3
Jan  7 20:44:20 killer-linux kernel: [  302.835503] **usb 1-2**: configuration #1 chosen from 1 choice
...
...
Jan  8 17:50:47 killer-linux kernel: [ 3999.801284] **usb 4-1**: new full speed USB device using uhci_hcd and address 2
Jan  8 17:50:47 killer-linux kernel: [ 3999.947066] **usb 4-1**: not running at top speed; connect to a high speed hub
Jan  8 17:50:47 killer-linux kernel: [ 3999.978166] **usb 4-1**: configuration #1 chosen from 1 choice

Apparently you **are** plugging it into a different port...
Not being an expert on why that is - could be anyone's guess really. Have you tried rebooting your workstation?

Regards
Iain

---

### Post by moparisthebest on 2010-01-08
> **tinivole said:**
> Hmm - sounds like a job for udev...

What is the ID of the device?
```
lsusb
```

edit:

Apparently you **are** plugging it into a different port...
Not being an expert on why that is - could be anyone's guess really. Have you tried rebooting your workstation?

Regards
Iain

I understand it looks like it is being plugged into a different port, but every time I plug it in those numbers are different, I don't know why.

I thought udev might be the answer at first, but as far as I am aware udev can't specify which driver to use for a device, correct?  So it won't help out here.

But, here is lsusb:
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c525 Logitech, Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 2040:6513 Hauppauge WinTV HVR-980
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Again, I have no explanation for the '1.1 root hubs', since they are all 2.0.  I have also tested that this same port supports 2.0 because I plugged in a flash drive and it used the ehci_hcd high-speed driver for it.

I have rebooted many times, to no avail.

edit:
It just worked again, it is very picky about what driver it wants to use when, note I am still using the same port, here is the output of /var/log/messages:
```
Jan  8 22:43:00 killer-linux kernel: [  874.041971] usb 1-5: new high speed USB device using ehci_hcd and address 4
Jan  8 22:43:01 killer-linux kernel: [  874.202292] usb 1-5: configuration #1 chosen from 1 choice
Jan  8 22:43:01 killer-linux kernel: [  874.203572] em28xx: New device WinTV HVR-980 @ 480 Mbps (2040:6513, interface 0, class 0)
Jan  8 22:43:01 killer-linux kernel: [  874.204740] em28xx #0: chip ID is em2882/em2883
Jan  8 22:43:01 killer-linux kernel: [  874.418978] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 13 65 d0 12 5c 03 82 1e 6a 18
Jan  8 22:43:01 killer-linux kernel: [  874.418987] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.418995] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.419003] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.419011] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.419018] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.419026] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
Jan  8 22:43:01 killer-linux kernel: [  874.419033] em28xx #0: i2c eeprom 70: 32 00 38 00 37 00 33 00 30 00 31 00 39 00 30 00
Jan  8 22:43:01 killer-linux kernel: [  874.419041] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
Jan  8 22:43:01 killer-linux kernel: [  874.419048] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 38 00 30 00 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.419056] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
Jan  8 22:43:01 killer-linux kernel: [  874.419064] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 4e 8b
Jan  8 22:43:01 killer-linux kernel: [  874.419071] em28xx #0: i2c eeprom c0: 21 f0 74 02 01 00 01 79 ac 00 00 00 00 00 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.419079] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
Jan  8 22:43:01 killer-linux kernel: [  874.419087] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 4e 8b
Jan  8 22:43:01 killer-linux kernel: [  874.419094] em28xx #0: i2c eeprom f0: 21 f0 74 02 01 00 01 79 ac 00 00 00 00 00 00 00
Jan  8 22:43:01 killer-linux kernel: [  874.419103] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x1a8925dd
Jan  8 22:43:01 killer-linux kernel: [  874.419105] em28xx #0: EEPROM info:
Jan  8 22:43:01 killer-linux kernel: [  874.419106] em28xx #0:  AC97 audio (5 sample rates)
Jan  8 22:43:01 killer-linux kernel: [  874.419108] em28xx #0:  500mA max power
Jan  8 22:43:01 killer-linux kernel: [  874.419110] em28xx #0:  Table at 0x24, strings=0x1e82, 0x186a, 0x0000
Jan  8 22:43:01 killer-linux kernel: [  874.419852] em28xx #0: Identified as Hauppauge WinTV HVR 950 (card=16)
Jan  8 22:43:01 killer-linux kernel: [  874.422700] tveeprom 0-0050: Hauppauge model 65201, rev A1C0, serial# 2198350
Jan  8 22:43:01 killer-linux kernel: [  874.422704] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
Jan  8 22:43:01 killer-linux kernel: [  874.422707] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
Jan  8 22:43:01 killer-linux kernel: [  874.422709] tveeprom 0-0050: audio processor is None (idx 0)
Jan  8 22:43:01 killer-linux kernel: [  874.422711] tveeprom 0-0050: has radio
Jan  8 22:43:01 killer-linux kernel: [  874.432767] tvp5150 0-005c: chip found @ 0xb8 (em28xx #0)
Jan  8 22:43:01 killer-linux kernel: [  874.444644] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
Jan  8 22:43:01 killer-linux kernel: [  874.444735] xc2028 0-0061: creating new instance
Jan  8 22:43:01 killer-linux kernel: [  874.444737] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Jan  8 22:43:01 killer-linux kernel: [  874.444744] usb 1-5: firmware: requesting xc3028-v27.fw
Jan  8 22:43:01 killer-linux kernel: [  874.448662] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Jan  8 22:43:01 killer-linux kernel: [  874.510015] xc2028 0-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
Jan  8 22:43:02 killer-linux kernel: [  875.458438] xc2028 0-0061: Loading firmware for type=MTS (4), id 000000000000b700.
Jan  8 22:43:02 killer-linux kernel: [  875.480816] xc2028 0-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
Jan  8 22:43:02 killer-linux kernel: [  875.745182] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/input/input6
Jan  8 22:43:02 killer-linux kernel: [  875.745336] em28xx #0: Config register raw data: 0xd0
Jan  8 22:43:02 killer-linux kernel: [  875.771263] em28xx #0: AC97 vendor ID = 0xffffffff
Jan  8 22:43:02 killer-linux kernel: [  875.771583] em28xx #0: AC97 features = 0x6a90
Jan  8 22:43:02 killer-linux kernel: [  875.771584] em28xx #0: Empia 202 AC97 audio processor detected
Jan  8 22:43:02 killer-linux kernel: [  875.980477] tvp5150 0-005c: tvp5150am1 detected.
Jan  8 22:43:02 killer-linux kernel: [  876.100984] em28xx #0: v4l2 driver version 0.1.2
Jan  8 22:43:03 killer-linux kernel: [  876.221204] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
Jan  8 22:43:03 killer-linux kernel: [  876.221208] em28xx-audio.c: probing for em28x1 non standard usbaudio
Jan  8 22:43:03 killer-linux kernel: [  876.221210] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
Jan  8 22:43:03 killer-linux kernel: [  876.320817] xc2028 0-0061: attaching existing instance
Jan  8 22:43:03 killer-linux kernel: [  876.320821] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Jan  8 22:43:03 killer-linux kernel: [  876.320823] em28xx #0/2: xc3028 attached
Jan  8 22:43:03 killer-linux kernel: [  876.320825] DVB: registering new adapter (em28xx #0)
Jan  8 22:43:03 killer-linux kernel: [  876.320828] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
Jan  8 22:43:03 killer-linux kernel: [  876.321099] Successfully loaded em28xx-dvb
Jan  8 22:43:03 killer-linux kernel: [  876.500517] tvp5150 0-005c: tvp5150am1 detected.
Jan  8 22:43:03 killer-linux kernel: [  876.862794] tvp5150 0-005c: tvp5150am1 detected.
```

So if someone could point me to a way to force the driver short of recompiling the kernel, I would appreciate it.

---

### Post by moparisthebest on 2010-01-12
Alright, I ended up recompiling the ubuntu kernel with the original .config and one change, uhci_hcd is now a module I can blacklist.  Now everything works as expected.  

While I solved my personal problem, I would like to leave this thread un-solved because there should be a way to force linux to use a specific driver that I have been unable to find.

---


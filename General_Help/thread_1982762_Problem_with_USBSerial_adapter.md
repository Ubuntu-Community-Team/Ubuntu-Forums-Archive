---
title: "Problem with USB/Serial adapter"
date: 2012-05-19
forum: General Help
---

### Post by signpainter on 2012-05-19
Hi folks,

I try to connect a datalogger (Gigalog S [www.controlord.fr/gigalog/gigalogDs.htm]("http://www.controlord.fr/gigalog/gigalogDs.htm")) to my PC running Ubuntu 11.04. The datalogger offers the possibility to connect via USB to the PC. In fact it has a built-in usb/serial-adapter. For Windows there is a driver supplied by Controlord. 

Anyhow, when I connect the device to my PC the adapter is recognized and dmesg gives
```

[   46.901096] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   47.067892] usb 3-2: config 1 has an invalid descriptor of length 1, skipping remainder of the config
[   47.067895] usb 3-2: config 1 has 1 interface, different from the descriptor's value: 2
[   47.067899] usb 3-2: config 1 interface 0 altsetting 0 has 0 endpoint descriptors, different from the interface descriptor's value: 1
[   47.116388] cdc_acm 3-2:1.0: This device cannot do calls on its own. It is not a modem.
[   47.116563] usbcore: registered new interface driver cdc_acm
[   47.116564] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```and lsusb shows
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 046d:092e Logitech, Inc. QuickCam Chat
Bus 007 Device 002: ID 04d9:a015 Holtek Semiconductor, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 11ff:3341  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03eb:6121 Atmel Corp.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The adapter is the Atmel one. As it is not automatically attached to ttyUSBxx I tried to load the driver using
```
sudo modprobe usbserial vendor=0x03eb product=0x6121
```After entering this dmesg shows new entries
```
[  113.054887] usbcore: registered new interface driver usbserial [  113.054898] USB Serial support registered for generic [  113.054911] usbserial_generic 3-2:1.0: Generic device with no bulk out, not allowed. [  113.054916] usbserial_generic: probe of 3-2:1.0 failed with error -5 [  113.054926] usbcore: registered new interface driver usbserial_generic [  113.054928] usbserial: USB Serial Driver core 
```Seems like there is a problem loading the driver!? I searched the web but wasn't able to find any hint on what might go wrong.

Do you have any clue? Any idea how to solve this?

Thanks.

signpainter

---

### Post by signpainter on 2012-05-20
Hmm, no ideas, hints?

---


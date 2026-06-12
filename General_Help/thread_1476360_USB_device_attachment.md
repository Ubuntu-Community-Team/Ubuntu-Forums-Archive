---
title: "USB device attachment"
date: 2010-05-07
forum: General Help
---

### Post by hhoyt on 2010-05-07
Lucid Lynx, but a general linux query:   I have some Prolific USB to serial adapters that are used by a wine app.   My problem is that linux seems to dynamically attach the devices which causes headaches for my sym links as the attached /dev/USBx happily changes with every boot.    Is there a way I can control the assignment ? (encl dmesg snippet)  TIA, Howard    20.891639] usb 1-2.2: FTDI USB Serial Device converter now attached to ttyUSB0 [   20.891770] usbcore: registered new interface driver ftdi_sio [   20.891774] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver [   20.902205] usb 3-2.1: pl2303 converter now attached to ttyUSB1 [   20.902249] pl2303 3-2.2:1.0: pl2303 converter detected [   20.923923] dell-wmi: No known WMI GUID found [   20.928225] usb 3-2.2: pl2303 converter now attached to ttyUSB2 [   20.928259] usbcore: registered new interface driver pl2303

---


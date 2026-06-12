---
title: "USB serial device stops after sometime"
date: 2010-11-04
forum: General Help
---

### Post by cheenujunk on 2010-11-04
Hi,
 I am able to use USB in serial mode for reading using 
cu,
 screen,
 minicom,
 jpnevulator,
 and others, but after some time the **output stops, **

$ jpnevulator -r -t /dev/ttyUSB0
 ... (some 10 lines)
 30 30 30 42 30 30 30 30 30 30 30 30 45 00 53 41 
30 30 30 30 30 30 30 30 42 30 30 30 30 30 30 30 
30 45 00 (hanged)

It happens with all utils i listed above. 

Dont understand the reason. To help, these are other info required with USB Serial port.

 lsusb info -- 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004  Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device  003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port   lsmod  info -- Module                  Size  Used by nls_iso8859_1            3261  1  nls_cp437               4931  1  vfat                    9201  1   fat                    48240  1 vfat pl2303                 11756  0   usbserial              33100  1 pl2303 

 dmesg info --
 [  444.332046] usb 3-1: new full speed USB device using uhci_hcd and address 3 
[  444.663215] usbcore: registered new interface driver usbserial 
[  444.663312] USB Serial support registered for generic
 [  444.666733] usbcore: registered new interface driver usbserial_generic 
[  444.666742] usbserial: USB Serial Driver core
 [  444.697012] USB Serial support registered for pl2303 
[  444.697091] pl2303 3-1:1.0: pl2303 converter detected 
[  444.709264] usb 3-1: pl2303 converter now attached to ttyUSB0 
[  444.709313] usbcore: registered new interface driver pl2303
 [  444.709319] pl2303: Prolific PL2303 USB to serial adaptor driver 

lsmod infor ---
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
pl2303                 11756  0 
usbserial              33100  1 pl2303

Can anyone let me know what might be the reason. It seems strange, I dont understand why it hangs in the middle of reading the port.

---

### Post by cheenujunk on 2010-11-06
is there anyone to help on this issue ?

---


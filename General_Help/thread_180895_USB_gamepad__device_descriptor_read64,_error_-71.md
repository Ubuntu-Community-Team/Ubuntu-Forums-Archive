---
title: "USB gamepad : device descriptor read/64, error -71"
date: 2006-05-23
forum: General Help
---

### Post by kelda on 2006-05-23
Hello,

I obtained a 'no-brand' USB gamepad and couldn't suceed in making it working. (Tried on a breezy & dapper, same result)

syslog output (tested all usb ports, the usb printer & my SE phone work perfectly) :

> 
May 23 10:14:40 localhost kernel: [4294979.964000] ohci_hcd 0000:00:02.0: wakeup
May 23 10:14:41 localhost kernel: [4294980.426000] usb 1-1: new low speed USB device using ohci_hcd and address 15
May 23 10:14:41 localhost kernel: [4294980.508000] usb 1-1: device descriptor read/64, error -71
May 23 10:14:41 localhost kernel: [4294980.709000] usb 1-1: device descriptor read/64, error -71
May 23 10:14:41 localhost kernel: [4294980.883000] usb 1-1: new low speed USB device using ohci_hcd and address 16
May 23 10:14:41 localhost kernel: [4294980.963000] usb 1-1: device descriptor read/64, error -71
May 23 10:14:41 localhost kernel: [4294981.144000] usb 1-1: device descriptor read/64, error -71
May 23 10:14:42 localhost kernel: [4294981.321000] usb 1-1: new low speed USB device using ohci_hcd and address 17
May 23 10:14:42 localhost kernel: [4294981.725000] usb 1-1: device not accepting address 17, error -71
May 23 10:14:42 localhost kernel: [4294981.798000] usb 1-1: new low speed USB device using ohci_hcd and address 18
May 23 10:14:42 localhost kernel: [4294982.202000] usb 1-1: device not accepting address 18, error -71
May 23 10:15:15 localhost kernel: [4295015.215000] ohci_hcd 0000:00:02.1: wakeup
May 23 10:15:16 localhost kernel: [4295015.495000] usb 2-1: new low speed USB device using ohci_hcd and address 10
May 23 10:15:16 localhost kernel: [4295015.575000] usb 2-1: device descriptor read/64, error -71
May 23 10:15:16 localhost kernel: [4295015.775000] usb 2-1: device descriptor read/64, error -71
May 23 10:15:16 localhost kernel: [4295015.949000] usb 2-1: new low speed USB device using ohci_hcd and address 11
May 23 10:15:16 localhost kernel: [4295016.029000] usb 2-1: device descriptor read/64, error -71
May 23 10:15:16 localhost kernel: [4295016.210000] usb 2-1: device descriptor read/64, error -71
May 23 10:15:17 localhost kernel: [4295016.387000] usb 2-1: new low speed USB device using ohci_hcd and address 12
May 23 10:15:17 localhost kernel: [4295016.794000] usb 2-1: device not accepting address 12, error -71
May 23 10:15:17 localhost kernel: [4295016.867000] usb 2-1: new low speed USB device using ohci_hcd and address 13
May 23 10:15:17 localhost kernel: [4295017.271000] usb 2-1: device not accepting address 13, error -71
May 23 10:15:36 localhost kernel: [4295035.965000] ohci_hcd 0000:00:02.1: wakeup
May 23 10:15:36 localhost kernel: [4295036.245000] usb 2-2: new low speed USB device using ohci_hcd and address 14
May 23 10:15:37 localhost kernel: [4295036.325000] usb 2-2: device descriptor read/64, error -71
May 23 10:15:37 localhost kernel: [4295036.506000] usb 2-2: device descriptor read/64, error -71
May 23 10:15:37 localhost kernel: [4295036.681000] usb 2-2: new low speed USB device using ohci_hcd and address 15
May 23 10:15:37 localhost kernel: [4295036.776000] usb 2-2: device descriptor read/64, error -71
May 23 10:15:37 localhost kernel: [4295036.960000] usb 2-2: device descriptor read/64, error -71
May 23 10:15:37 localhost kernel: [4295037.134000] usb 2-2: new low speed USB device using ohci_hcd and address 16
May 23 10:15:38 localhost kernel: [4295037.538000] usb 2-2: device not accepting address 16, error -71
May 23 10:15:38 localhost kernel: [4295037.611000] usb 2-2: new low speed USB device using ohci_hcd and address 17
May 23 10:15:38 localhost kernel: [4295038.030000] usb 2-2: device not accepting address 17, error -71


dmesg output :

> 

[4294918.215000] ohci_hcd 0000:00:02.1: wakeup
[4294918.499000] usb 2-3: new low speed USB device using ohci_hcd and address 6
[4294918.598000] usb 2-3: device descriptor read/64, error -71
[4294918.779000] usb 2-3: device descriptor read/64, error -71
[4294918.953000] usb 2-3: new low speed USB device using ohci_hcd and address 7
[4294919.033000] usb 2-3: device descriptor read/64, error -71
[4294919.215000] usb 2-3: device descriptor read/64, error -71
[4294919.389000] usb 2-3: new low speed USB device using ohci_hcd and address 8
[4294919.793000] usb 2-3: device not accepting address 8, error -71
[4294919.866000] usb 2-3: new low speed USB device using ohci_hcd and address 9
[4294920.275000] usb 2-3: device not accepting address 9, error -71
[4294937.192000] usb 1-3: new low speed USB device using ohci_hcd and address 7
[4294937.272000] usb 1-3: device descriptor read/64, error -71
[4294937.455000] usb 1-3: device descriptor read/64, error -71
[4294937.633000] usb 1-3: new low speed USB device using ohci_hcd and address 8
[4294937.713000] usb 1-3: device descriptor read/64, error -71
[4294937.894000] usb 1-3: device descriptor read/64, error -71
[4294938.068000] usb 1-3: new low speed USB device using ohci_hcd and address 9
[4294938.472000] usb 1-3: device not accepting address 9, error -71
[4294938.564000] usb 1-3: new low speed USB device using ohci_hcd and address 10
[4294938.968000] usb 1-3: device not accepting address 10, error -71
[4294956.692000] usb 1-2: new low speed USB device using ohci_hcd and address 11
[4294956.772000] usb 1-2: device descriptor read/64, error -71
[4294956.953000] usb 1-2: device descriptor read/64, error -71
[4294957.127000] usb 1-2: new low speed USB device using ohci_hcd and address 12
[4294957.207000] usb 1-2: device descriptor read/64, error -71
[4294957.388000] usb 1-2: device descriptor read/64, error -71
[4294957.565000] usb 1-2: new low speed USB device using ohci_hcd and address 13
[4294957.972000] usb 1-2: device not accepting address 13, error -71
[4294958.045000] usb 1-2: new low speed USB device using ohci_hcd and address 14
[4294958.449000] usb 1-2: device not accepting address 14, error -71


> 
# uname -rvo
2.6.12-10-k7 #1 Fri Apr 28 13:58:48 UTC 2006 GNU/Linux


> 
# lsmod | grep usb
usbhid                 35552  0
usb_storage            74560  1
usblp                  12736  0
usbserial              29864  0
usbcore               118396  9 usbhid,usb_storage,cdc_acm,usblp,usbserial,ndiswrapper,ehci_hcd,ohci_hcd
scsi_mod              135944  5 usb_storage,sr_mod,sbp2,sd_mod,libata
ide_core              139028  5 usb_storage,ide_cd,ide_disk,ide_generic,amd74xx


None of the subjects I found with these error messages talk about a gamepad.

Does anyone have any clue ? :-)

Thanks !

---

### Post by airtonix on 2006-06-10
try grepping for "gamepad", for it oo have a no name usb gampepad...

 ```
lsmod | grep gameport
gameport               15496  1 analog
```

```
lsmod | grep usb
usbhid                 38368  0
usbcore               129668  4 usbhid,uhci_hcd,ohci_hcd
```

but i have no items in the /dev/input starting with js.

```
ls /dev/input/
event0  event1  event3  mice  mouse0  ts0
```:-k

ts0 seems to be the mouse, so is mice, and mouse0 too.
event0 is also another link to the mouse, event1 im not sure about...and event3 is the keyboard.

so either its at event1 or maybe over at /dev/bus/usb somewhere? :-k not sure

---


---
title: "USB mouse doesn't work after hot plug. I have Ubuntu 9.10 In the last month I mention"
date: 2011-05-16
forum: General Help
---

### Post by Light-kun on 2011-05-16
I have Ubuntu 9.10
In the last month I mentioned, that if I start PC without mouse connected and then plug it after X loaded it doesn't work.
messages:
# plugging in:
```
May 16 14:09:27 localhost kernel: [10042.625013] usb 5-1: new full speed USB device using uhci_hcd and address 3
May 16 14:09:27 localhost kernel: [10042.814241] usb 5-1: configuration #1 chosen from 1 choice
May 16 14:09:27 localhost kernel: [10042.820301] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input15
May 16 14:09:27 localhost kernel: [10042.820600] generic-usb 0003:09DA:054F.0005: input,hiddev96,hidraw0: USB HID v1.11 Keyboard [A4TECH USB Device] on usb-0000:00:1d.0-1/input0
May 16 14:09:27 localhost kernel: [10042.822730] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input16
May 16 14:09:27 localhost kernel: [10042.822908] generic-usb 0003:09DA:054F.0006: input,hidraw1: USB HID v1.11 Mouse [A4TECH USB Device] on usb-0000:00:1d.0-1/input1
```
#turning off:
```
May 16 14:09:54 localhost kernel: [10069.970909] usb 5-1: USB disconnect, address 3

```# on again:
```
May 16 14:10:06 localhost kernel: [10081.408930] usb 5-1: new full speed USB device using uhci_hcd and address 4
May 16 14:10:06 localhost kernel: [10081.604334] usb 5-1: configuration #1 chosen from 1 choice
May 16 14:10:06 localhost kernel: [10081.620498] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input17
May 16 14:10:06 localhost kernel: [10081.620803] generic-usb 0003:09DA:054F.0007: input,hiddev96,hidraw0: USB HID v1.11 Keyboard [A4TECH USB Device] on usb-0000:00:1d.0-1/input0
May 16 14:10:06 localhost kernel: [10081.625077] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input18
May 16 14:10:06 localhost kernel: [10081.625165] generic-usb 0003:09DA:054F.0008: input,hidraw1: USB HID v1.11 Mouse [A4TECH USB Device]  on usb-0000:00:1d.0-1/input1

```
uname -a
```
Linux localhost 2.6.31-23-generic #74-Ubuntu SMP Mon Feb 28 21:32:57 UTC 2011 i686 GNU/Linux
```

lsmod|grep usb
```
usb_storage            52768  0 
usbhid                 38208  0 
btusb                  11856  1 
```

---


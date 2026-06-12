---
title: "USB Mouse/Keyboard Detected but Unresponsive"
date: 2012-06-04
forum: General Help
---

### Post by Halsafar on 2012-06-04
I have Ubuntu running on an HTPC which I use very often.  

Out of no where the usb connected devices seem to be detected but I can't use them.  Specifically a logitech mouse and keyboard, which have been working in this machine running Ubuntu for over a year.

The only thing I did recently was apt-get install sane so I could try and setup networking scanning.  Sometime after that I realized the mouse and keyboard stopped working. 

I suspect some permission problem with udev but not sure where to begin.


Here is /var/log/syslog when I plug in the USB receiver.
```

Jun  4 10:21:39 eldren kernel: [  146.056020] usb 5-2: new low-speed USB device number 3 using uhci_hcd
Jun  4 10:21:39 eldren mtp-probe: checking bus 5, device 3: "/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2"
Jun  4 10:21:39 eldren kernel: [  146.249399] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input6
Jun  4 10:21:39 eldren kernel: [  146.249527] logitech 0003:046D:C517.0004: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.2-2/input0
Jun  4 10:21:39 eldren mtp-probe: bus: 5, device: 3 was not an MTP device
Jun  4 10:21:39 eldren kernel: [  146.281046] logitech 0003:046D:C517.0005: fixing up Logitech keyboard report descriptor
Jun  4 10:21:39 eldren kernel: [  146.282131] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input7
Jun  4 10:21:39 eldren kernel: [  146.282381] logitech 0003:046D:C517.0005: input,hiddev0,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-2/input1


```

So clearly it detects the device.

Output of lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:5c11 Hewlett-Packard PhotoSmart C4200 Printer series
Bus 005 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 007 Device 002: ID 0764:0501 Cyber Power System, Inc. CP1500 AVR UPS
Bus 008 Device 002: ID 0a5c:2121 Broadcom Corp. BCM2210 Bluetooth

```

So again, clearly the device is there.

The mouse and keyboard work if I plug them into any other PC, so it is not a battery or hardware issue.

---

### Post by Halsafar on 2012-06-04
I did a chmod a+rw to /dev/bus/usb/005/003 (the correct information based on lsusb).  This did nothing.

I'm completely lost here.  Ubuntu clearly sees everything it needs to but it refuses to listen to the mouse.

I apt-get purge sane, it left behind some files in /lib/udev/rules.d, not entirely sure which are all sane's.  I do have a daily backup I can check.  

Based on a daily backup the only files changes in /lib/udev/rules.d is a 90-pulseaudio.rules

---


---
title: "Help needed compiling a module (first time)"
date: 2011-05-19
forum: General Help
---

### Post by hopelessone on 2011-05-19
Hi,

I wanna compile a module:

```
make -C /lib/modules/2.6.35-28-generic/build M=/home/darkstar/working/USBKBD modules
```

but i get error:
> darkstar@ubuntu:~/working$ make -C /lib/modules/2.6.35-28-generic/build M=/home/darkstar/working/USBKBD modules
make: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
scripts/Makefile.build:44: /home/darkstar/working/USBKBD/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/darkstar/working/USBKBD/Makefile'.  Stop.
make: *** [_module_/home/darkstar/working/USBKBD] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'


How can i fix this?
Thanks

---

### Post by hulkman on 2011-05-20
Can you give us a link to the package you are wanting to compile so we can try on our computers?

---

### Post by hopelessone on 2011-05-20
It's the usbkbd module...i'm trying to get a Saulabi 4k Gamepad to work...

> May 20 13:57:43 ubuntu kernel: [  168.380382] usb 3-1: new low speed USB device using uhci_hcd and address 2
May 20 13:57:43 ubuntu kernel: [  168.588401] input: ISAULABI   USBKeyStick as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
May 20 13:57:43 ubuntu kernel: [  168.588555] generic-usb 0003:0EF5:3000.0003: input,hidraw2: USB HID v1.00 Keyboard [ISAULABI   USBKeyStick] on usb-0000:00:1d.1-1/input0
May 20 13:58:08 ubuntu kernel: [  193.581336] generic-usb: probe of 0003:0EF5:3000.0004 failed with error -110
May 20 13:58:33 ubuntu kernel: [  218.581426] generic-usb: probe of 0003:0EF5:3000.0005 failed with error -110

Trying this thread:

[http://ubuntuforums.org/showthread.php?t=1689031](http://ubuntuforums.org/showthread.php?t=1689031)

---


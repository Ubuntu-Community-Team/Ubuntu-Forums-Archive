---
title: "libusb couldn't open USB device"
date: 2011-07-13
forum: General Help
---

### Post by foxy123 on 2011-07-13
I’ve got an odd problem with libusb. I am trying to use Heimdall, an open-source cross-platform tool to flash firmware to Samsung smart phones, a replacement for Odin. It uses libusb. So I’ve got the following error:
```
Initialising connection...
Detecting device...
libusb couldn't open USB device /dev/bus/usb/001/003: Permission denied.
libusb requires write access to USB device nodes.
ERROR: Failed to access device. libusb error: -3
```
I guess it is something to do with permissions but I wonder how I can fix it?

---

### Post by Del_ on 2012-08-24
You need to run heimdall as root, like this:
```
sudo heimdall flash --kernel zImage
```

---


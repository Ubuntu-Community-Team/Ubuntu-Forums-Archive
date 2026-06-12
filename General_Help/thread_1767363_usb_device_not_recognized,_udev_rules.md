---
title: "usb device not recognized, udev rules"
date: 2011-05-25
forum: General Help
---

### Post by seheatwole on 2011-05-25
I have a TotalPhase aardvark usb 2 I2C adapter that I want to use and am having trouble getting Ubuntu 10.04 to recognize it.

The device is supported for RHEL5 and I have gotten it working there.  The software runs in ubuntu 10.04 but device is not recognized.  The device comes with a set of rules that are placed in the /etc/udev/rules.d/ directory.  The file (99-totalphase.rules) contains:

# This file causes the mode of all Total Phase usb devices to be made
# writable for any user.

# Aarvark I2C/SPI Host Adapter
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0403", SYSFS{idProduct}=="e0d0", MODE="0666"
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="e0d0", MODE="0666"

# Beagle Protocol Analyzers
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="1679", SYSFS{idProduct}=="2001", MODE="0666"
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="1679", ATTR{idProduct}=="2001", MODE="0666"

# Cheetah SPI Host Adapter
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="1679", SYSFS{idProduct}=="2002", MODE="0666"
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="1679", ATTR{idProduct}=="2002", MODE="0666"

I know that there were changes to udev between 9 and 10 and didn't know if there were some simple changes I could make to get things working.  This same rules file works in RHEL 5.

Any ideas on how to fix this?

---

### Post by jason-hobbs on 2011-12-15
I don't think the udev rules are necessary. I have an Aardvark working on 11.10 64 bit without them. The trick is installing 32 bit compat libraries and making sure to set this environment variable before starting any totalphase software:

```

export LIBUSBTP=/lib32/libusb-0.1.so.4

```

If you don't, it won't complain, but it also won't recognize your adapter.

---


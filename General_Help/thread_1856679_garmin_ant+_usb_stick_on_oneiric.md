---
title: "garmin ant+ usb stick on oneiric"
date: 2011-10-08
forum: General Help
---

### Post by zeusfaber on 2011-10-08
I am having issues with the garmin ant+ usb stick on 11.10 (with all updates). It gets detected but should be showing up as a usb serial device and is not. It works properly under 10.04 after "sudo modprobe usbserial" but doesn't in 11.10. Anyone else having similar issues?

$ ls -al /dev/tty*USB*
ls: cannot access /dev/tty*USB*: No such file or directory

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 008: ID 0fcf:1008 Dynastream Innovations, Inc. 

$ dmesg
<snip>
[   81.451252] usbcore: registered new interface driver usbserial
[   81.451266] USB Serial support registered for generic
[   81.452025] usbcore: registered new interface driver usbserial_generic
[   81.452027] usbserial: USB Serial Driver core
[  516.683427] usb 2-2.2: new full speed USB device number 6 using uhci_hcd
<snip>

---

### Post by Christofferh on 2011-12-20
Hi
I'm trying to get my Garmin Forerunner 610 to work with Ubuntu 11.10 and having some difficulties as well.

```
# dmesg
[16521.997838] usb 2-1.5: USB disconnect, device number 5
[16526.798899] usb 2-1.5: new full speed USB device number 6 using ehci_hcd
```

At least it shows up in dmesg.

```
# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 041e:4087 Creative Technology, Ltd 
Bus 001 Device 004: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 001 Device 005: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 006: ID 0fcf:1008 Dynastream Innovations, Inc. 
Bus 002 Device 004: ID 0b0e:090a GN Netcom
```

It must be the Dynastream one becuase that is the one that is removed if I pull the USB2 stick away and Dynastream is the company behind ANT+ technology.

Now I'm just trying to figure out how to read the datastream from the USB device or even better be able to open it as a USB disk(if possible).

---

### Post by dutoitc on 2012-03-16
To make Forerunner610 mount as /dev/ttyUSB0, (or ant+ key),

create a new file at /etc/udev/rules.d/garmin-ant2.rules 
add this:
BUS=="usb", SYSFS{idVendor}=="0fcf", SYSFS{idProduct}=="1008", RUN+="/sbin/modprobe usbserial vendor=0x0fcf product=0x1008"
(one line)

Next you have to download data. The problem is that new watches using ant devices don't use garmin protocol, and nobody yet wrote a full application for forerunner610.

You can find gant, renamed garmin-ant-downloader in oneiric or you can get a copy at 
git clone git://github.com/DanAnkers/garmin-ant-downloader.git

While gant can talk to the watch and get some information, it cannot download fits.
I am trying to modify gant to make it work, as nobody work on it yet, but with no result.

You can also find some scripts in python, but the best success I have found was to download the gps trail, but no cardio and no fits...

I guess there is some work to do for that :-(

---


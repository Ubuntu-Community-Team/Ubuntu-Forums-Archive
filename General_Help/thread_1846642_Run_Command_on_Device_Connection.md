---
title: "Run Command on Device Connection"
date: 2011-09-19
forum: General Help
---

### Post by M1GEO on 2011-09-19
Hi.

I am looking to run a command (or maybe script) when a device is connected via USB.  Essentially, I want to run Google's ADB when my Android Phone is connected via USB.

Is there any way to do this? I have had a quick read of udev's man pages, and 'Googled' a bit, but I don't know exactly what to search for, and so far have turned up nothing.

Any advice would be greatly appreciated.

Cheers.

---

### Post by M1GEO on 2011-09-19
With a bit more Googling, I've found this page, which describes a little more about it, but I still don't understand how to get the device details from my phone.

[http://reactivated.net/writing_udev_rules.html#external-run](http://reactivated.net/writing_udev_rules.html#external-run)

---

### Post by M1GEO on 2011-09-19
For anyone that is interested, I figured it all out.

I created a rule for udev, which observes kernel USB actions, and looks for the vendor-id of 0BB4 (HTC, check yours here: [http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html)).  It then runs the script, /opt/phone_connected.sh, which completes my specified requirements.

Rule: /etc/udev/rules.d/phone_connected.rules
> SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666", GROUP="plugdev" RUN+="/opt/phone_connected.sh"

The script is a standard BASH script, starting with the usual "#!/bin/bash" and made executable.

Just for the record.

---

### Post by opensshd on 2012-09-12
nice ^

thank you :)

---


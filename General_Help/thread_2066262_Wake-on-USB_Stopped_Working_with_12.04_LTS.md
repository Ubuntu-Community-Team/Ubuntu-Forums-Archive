---
title: "Wake-on-USB Stopped Working with 12.04 LTS"
date: 2012-10-04
forum: General Help
---

### Post by jingo_man on 2012-10-04
I am running "Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-31-generic x86_64)" with the XBMC application installed, and set the system to boot into an XBMC specific desktop session on boot.

I followed the guide in their wiki to configure Wake-on-USB for the MCE Remote I have.
[http://wiki.xbmc.org/index.php?title=HOW-TO:Suspend_and_wake_in_Ubuntu](http://wiki.xbmc.org/index.php?title=HOW-TO:Suspend_and_wake_in_Ubuntu)

Everything worked fine until last night. Nothing was changed in the system setup, either the O/S or XBMC. I did a couple of reboots of the system from inside XBMC to force it's AirPlay feature to become network discoverable and usable from my other devices on the network (iPad and iMac), and since this, I can no longer wake the device from the MCE Remote.

From my troubleshooting, I have the following outputs:

> 
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 004: ID 15c2:0038 SoundGraph Inc. GD01 MX LCD Display/IR Receiver


> 
grep 0815 /sys/bus/usb/devices/*/idProduct
/sys/bus/usb/devices/3-3/idProduct:0815


> 
cat /etc/rc.local 
echo enabled > /sys/bus/usb/devices/3-3/power/wakeup

exit 0

(Note, in the last quoted section, I removed all the preceding lines of comments.)

To test that the wake-on-USB for this device is active, I test with:

> 
cat /sys/bus/usb/devices/3-3/power/wakeup
enabled


If I use the MCE Remote to power off the device, it powers off as expected, which in XBMC is set to "Shutdown Function" = "Suspend"

I note another thread on this site relating to problems of this kind, but mine was successfully doing this for months ahead of last night...
[http://ubuntuforums.org/showthread.php?p=11926504](http://ubuntuforums.org/showthread.php?p=11926504)


Can anyone help to resolve this issue? Or how to further troubleshoot.

Many thanks

jingo_man

---

### Post by felisucoibi on 2012-10-22
Hello, it happend to me too, I tkink is because an update from ubuntu 12.04.1 something changed in hte second week of October 2012... still not too many people with the problem, but it happend to me too.

---

### Post by jingo_man on 2012-10-22
Got mine up and running again...

I'd added an extra USB Bluetooth recurve, which happened to be on the same bus as the USB remote (though I thought the HDTV script calculated all devices on the same bus), and I also did a "sudo update-grub" with a reboot afterwards. From memory it took a reboot using XBMC menus rather than an ssh reboot command for it to start working.

This is a PITA for me as I have to quit XBMC regularly to access Flash streams on the HDTV, which needs the USB Bluetooth mouse each time.

Not entirely sure which was the fix though as didn't properly test each stage, though I am on 12.04.1 which must have occurred quite recently without me thinking about it.

---


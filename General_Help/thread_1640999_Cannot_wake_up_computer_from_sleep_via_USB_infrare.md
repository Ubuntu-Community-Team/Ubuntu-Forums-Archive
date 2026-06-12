---
title: "Cannot wake up computer from sleep via USB infrared remote"
date: 2010-12-08
forum: General Help
---

### Post by rouble on 2010-12-08
All,

I have an interesting issue. I have a computer running Ubuntu 10.10. I have a wireless USB Microsoft keyboard attached to this, and I have a [cheap USB infrared remote]("http://kragone.free.fr/Cyp_Se_WitheHome.jpg") also attached to it.

The wireless USB Microsoft keyboard can wake up the system from suspend. The USB infrared remote cannot.

To start off, I made sure my /proc/acpi/wakeup had wakeup enabled for all usb devices.
```
xbmc:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
USB1      S3    *enabled   pci:0000:00:1d.0
USB2      S3    *enabled   pci:0000:00:1d.1
USB3      S3    *enabled   pci:0000:00:1d.2
USB4      S3    *enabled   pci:0000:00:1d.3
USBE      S3    *enabled   pci:0000:00:1d.7
SLOT      S5    *disabled  pci:0000:00:1e.0
COMA      S5    *disabled  pnp:00:0b
```

Next, I checked the usb device status. This is where I found something interesting:
```
xbmc:~$ cat /sys/bus/usb/devices/usb5/power/wakeup
enabled
xbmc:~$ cat /sys/bus/usb/devices/usb5/5-1/power/wakeup
enabled
xbmc:~$ cat /sys/bus/usb/devices/usb5/5-2/power/wakeup
disabled
```

Notice that the usb5 bus is enabled for wakeup, but 5-2 (the USB infrared remote) is disabled. 5-1 (the wireless USB Microsoft keyboard) is enabled also. Does anyone have an idea as to why that is?

I have manually changed /sys/bus/usb/devices/usb5/5-2/power/wakeup to enabled, but this does not help (Do I need to restart any services after I do this?). Also, if I unplug, and replug the infrared remote it goes back to disabled. Why does it do that?

If anyone has any tips on where I can go from here, please let me know. 

For the record, I have tried all the usb ports on the box. The wireless USB Microsoft keyboard works on all ports, and the USB infrared remote works on none.

tia,
rouble

---

### Post by rickg100 on 2011-02-16
I'm having the same issue. Did you ever figure this out?

---

### Post by Rebelli0us on 2011-09-15
Same problem here.

I have a USB infrared remote that only wakes up Ubuntu intermittently. Works fine in Windows. If I edit /etc/rc.local, enabling ANY USBx enables ALL USB devices for wakeup, yet the infrared remove still wakes Ubuntu from S3 only intermittently.

---


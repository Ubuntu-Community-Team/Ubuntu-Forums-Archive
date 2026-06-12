---
title: "Cannot properly eject usb drive"
date: 2011-03-17
forum: General Help
---

### Post by JohnElway on 2011-03-17
I've noticed this problem occur occasionally and it's just happened to me right now. In Nautilus, I clicked the eject button for a usb drive and physically unplugged it from the usb port. However, the icon for the drive is still present and if I try to plug the device (or any other usb device) into ANY usb port, it is not recognized. Basically none of the usb ports work now. If I right-click the drive icon and select 'Safely Remove Drive', I get the following error message:

```
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:02.1/usb1/1-4)
SYNCHRONIZE CACHE: synchronize cache(10): transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
```

If I plug the device back in, right-click the icon and select 'Mount', I get this message:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I know I could easily restart my computer and everything would be fine, but I'm wondering if there's something I can do to easily get my usb ports working again without rebooting.

I was thinking that maybe there's a way to get Ubuntu to refresh it's hardware list, which led me to the HAL daemon. Unfortunately this service doesn't seem to exist in the version I'm using (10.04), so I'm unsure of what to do now. Is there any way to refresh the hardware in 10.04? Or is there a more sophisticated way to get my usb ports working again?

---

### Post by decrepit on 2011-03-17
sorry can't help get your usb back, but I'm wondering if this is a design problem.
I've recently migrated from fedora, that only had the option to "unmount drive". 
I guess "safely remove drive" does the same thing. 
But "eject" is obviously impossible, and can only apply to CD/DVD.

Probably you pulled it out before it was unmounted.

---


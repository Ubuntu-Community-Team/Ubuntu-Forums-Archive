---
title: "USB pen wont work"
date: 2012-04-23
forum: General Help
---

### Post by JCM_Pico on 2012-04-23
Hello,

I've an usb flash drive that cease to work... it's not recognized by the system... As far I can get when it is plugged in the usb it acts only as a card reader

dmesg output for the device
```
[  121.308266] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  121.441671] usb 1-1: New USB device found, idVendor=058f, idProduct=6366
[  121.441679] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  121.441685] usb 1-1: Product: Mass Storage Device
[  121.441689] usb 1-1: Manufacturer: Generic
[  121.441694] usb 1-1: SerialNumber: 058F63666433
[  121.441879] usb 1-1: configuration #1 chosen from 1 choice
[  121.443290] scsi3 : SCSI emulation for USB Mass Storage devices
[  121.443472] usb-storage: device found at 5
[  121.443476] usb-storage: waiting for device to settle before scanning
[  126.440398] usb-storage: device scan complete
[  126.569176] scsi 3:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[  126.570720] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  128.313453] sd 3:0:0:0: [sdb] Attached SCSI removable disk

``` 

If I try to mount it I get
```
mount /dev/sdb /media/usb0
mount: /dev/sdb: unknown device
```

Is there any way I can make it work again?

---

### Post by audiomick on 2012-04-23
This is a wild guess, but I could imagine that happening if the actual storage chip is broken, i.e. the computer  is seeing the electronics of the device, but not the storage, and decides that it is a card reader with no medium inserted.

I don't really know what to do about it, but I would try having a look at it with the Hard drive utility or Gparted and see what that finds.

---

### Post by JCM_Pico on 2012-04-23
In disk utility and gparted the device is represented has a card reader... so probably its just broken :mad:

---

### Post by techsupport on 2012-04-23
> **JCM_Pico said:**
> Hello,

I've an usb flash drive that cease to work... it's not recognized by the system... As far I can get when it is plugged in the usb it acts only as a card reader

dmesg output for the device
```
[  121.308266] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  121.441671] usb 1-1: New USB device found, idVendor=058f, idProduct=6366
[  121.441679] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  121.441685] usb 1-1: Product: Mass Storage Device
[  121.441689] usb 1-1: Manufacturer: Generic
[  121.441694] usb 1-1: SerialNumber: 058F63666433
[  121.441879] usb 1-1: configuration #1 chosen from 1 choice
[  121.443290] scsi3 : SCSI emulation for USB Mass Storage devices
[  121.443472] usb-storage: device found at 5
[  121.443476] usb-storage: waiting for device to settle before scanning
[  126.440398] usb-storage: device scan complete
[  126.569176] scsi 3:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[  126.570720] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  128.313453] sd 3:0:0:0: [sdb] Attached SCSI removable disk

```If I try to mount it I get
```
mount /dev/sdb /media/usb0
mount: /dev/sdb: unknown device
```Is there any way I can make it work again?

As long as you have Ubuntu OS running on a computer, you can plug that USB Pendrive into the USB port and try to format it with "Startup Disc Creator".  If it formats the drive, you may still be able to use it.  If not, it is time to buy a new one for $15-20. They are very inexpensive now. I've seen them for as little as $5

---

### Post by efflandt on 2012-04-23
Did you have a file system on that device, or did you dd an iso file directly to it?

If there was a recognized partition on it, the first partition would be /dev/sdb1 (not /dev/sdb, which is the entire flash disk).  Since dmesg does not list sdb1, either it is not properly partitioned, or there is something wrong with it.

While using Startup Disk Creator, at first I would often accidentally format the entire flash disk instead of the partition on it.  To fix that I would use gparted to create an "msdos partition table" and a partition.

---

### Post by JCM_Pico on 2012-04-23
Nop.... the device died :(

---

### Post by audiomick on 2012-04-23
Well, it happens. I hope there was nothing on there that you didn't have anywhere else.

---

### Post by JCM_Pico on 2012-04-24
There was no important data on it :p... only the sentimental value and that it was a very useful 16 Gb drive

Thanks for all the help

---


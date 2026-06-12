---
title: "USB Device is detected but not mounted"
date: 2009-09-04
forum: General Help
---

### Post by giscardf on 2009-09-04
Hi guys,

I have a customized kernel (for an embeeded system) and up until today I was not using USB no it (however the customer asked for). So I did set all USB options on the kernel (including the CONFIG_SCSI) and rebuild it.

When I boot using the recompiled kernel everythings seems to be right. Whan I plug a USB on the PC a message is shows a new device was connected but none driver calimed for it (what is normal). Using the dmesg I can see a new usb device attached.

When I perform a cat /proc/scsi/scsi it also prints the device attached (including its vendor name and some other information). However when I try to mound the device on sda[0-9]/sdb[0-9] I get a message saying the /dev/X is not a block device.

On my guess for some reason the kernel is detecting the device but is not being able to map it to a valid /dev. The kernel points the Host: scsi1 Channel:00 Id:00 Lun:00 for the device, what should be mapped to sdb, right?

Do your guys have any idea on how to solve that?

Thanks and Regards

---

### Post by giscardf on 2009-09-04
Well,

I have been read some stuffs from on google, so I could find out that usually dmesg shows that an usb device was attached and also display the /dev/sdx where the device can be found.

However in my case such /dev/sdx is not displayed, only the messages about a new device attached. I am not sure, but it seems that on my kernel compilation I did not enabled the "feature" responsible to perform this "auto map" from my scsi device to the properly /dev one. SO I believe I will probably have to use mknod to perform that.

Does someone know how to create a device for the following scsi address "Host: scsi1 Channel: 00 Id:00 Lun:00"?

Thanks and Regards

---

### Post by sedawk on 2009-09-04
Do you have another Linux box to compare dmesg output, e.g. a Ubuntu box?

Some USB devices do not have a partition table, so you will
not see that /dev/sdb1, /dev/sdb2 info.
(But you should still get a new device file like /dev/sdb) 

I think the "service" responsible on linux 
for creating device files nowadays is udev.
You might have to make sure that udev properly works on your
system.

I'm not sure if creating devices with mknod is recommended
anymore.

Here is what I get after plugging in a
USB memory stick (/dev/sdb, 1 Partition /dev/sdb1):

brw-rw---- 1 root disk 8,  0 2009-09-04 14:18 sda
brw-rw---- 1 root disk 8,  1 2009-09-04 14:18 sda1
brw-rw---- 1 root disk 8,  2 2009-09-04 12:18 sda2
brw-rw---- 1 root disk 8,  3 2009-09-04 12:18 sda3
brw-rw---- 1 root disk 8,  4 2009-09-04 14:18 sda4
brw-rw---- 1 root disk 8,  5 2009-09-04 14:18 sda5
brw-rw---- 1 root disk 8,  6 2009-09-04 12:18 sda6
brw-rw---- 1 root disk 8,  7 2009-09-04 12:18 sda7
brw-rw---- 1 root disk 8, 16 2009-09-04 16:22 sdb
brw-rw---- 1 root disk 8, 17 2009-09-04 16:22 sdb1

So sdc is 8,32-47, sdd is 8,48-63 and so on?

---

### Post by giscardf on 2009-09-04
Here we go with all information that I have

==== DEFAULT COMPILED KERNEL ====
BASE KERNEL AS DOWNLOADED FROM RED HAT VERSION 7.3

THERE IS NO /proc/scsi/scsi

[root@mime root]# dmesg
usb.c: registered new driver usbdevfs
usb.c: registered new driver hub
PCI: Found IRQ 11 for device 00:13.0
PCI: Sharing IRQ 11 with 00:0e.0
usb-ohci.c: USB OHCI at membase 0xc88bb000, IRQ 11
usb-ohci.c: usb-00:13.0, Compaq Computer Corporation USB Open Host Controller
usb.c: new USB bus registered, assigned bus number 1
hub.c: USB hub found
hub.c: 2 ports detected
hub.c: USB new device connect on bus1/2, assigned device number 2
usb.c: USB device 2 (vend/prod 0x781/0x5151) is not claimed by any active driver

[root@mime proc]# cat /proc/partitions
major minor  #blocks  name     rio rmerge rsect ruse wio wmerge wsect wuse running use aveq

  22     0    3981096 hdc 5276 12294 140248 64470 1622 14305 127336 781050 0 36390 845520
  22     1      48163 hdc1 18 25 86 20 8 8 32 1340 0 1360 1360
  22     2    3156772 hdc2 5255 12263 140138 64450 1614 14297 127304 779710 0 36370 844160
  22     3     763087 hdc3 1 0 8 0 0 0 0 0 0 0 0

==== CUSTOM COMPILED KERNEL ====
THIS KERNEL HAS A CONFIG FILE CREATED BY MYSELF AND HAS NO
DYNAMIC MODULE, I.E, I CREATED A MONOLITC KERNEL (ANSWER YES
INSTEAD OF M).
THE BASE KERNEL IS 2.4.18-3, THAT I GOT FROM RED HAT 7.3, THAT
IS WHAT WE DID HAVE 5 YEARS AGO...:-)

MY CONFIG FILES IS:
CONIG_HOTPLUG=y
CONFIG_SCSI=y

CONFIG_USB=y
CONFIG_USB_DEBUG=y
CONFIG_USB_DEVICEFS=y
# CONFIG_USB_BANDWIDTH is not set
CONFIG_USB_LONG_TIMEOUT=y
# CONFIG_USB_UHCI is not set
# CONFIG_USB_UHCI_ALT is not set
CONFIG_USB_OHCI=y
#CONFIG_USB_AUDIO is not set
#CONFIG_USB_BLUETOOTH is not set
CONFIG_USB_STORAGE=y
CONFIG_USB_STORAGE_DEBUG=y
CONFIG_USB_STORAGE_DATAFAB=y
CONFIG_USB_STORAGE_FREECOM=y
CONFIG_USB_STORAGE_ISD200=y
CONFIG_USB_STORAGE_DPCM=y
CONFIG_USB_STORAGE_HP8200e=y
CONFIG_USB_STORAGE_SDDR09=y
CONFIG_USB_STORAGE_JUMPSHOT=y
# CONFIG_USB_ACM is not set
# CONFIG_USB_PRINTER is not set
# CONFIG_USB_DC2XX is not set
# CONFIG_USB_MDC800 is not set



[root@mime root]# cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: SanDisk  Model: Cruzer Micro     Rev: 8.01
  Type:   Direct-Access                    ANSI SCSI revision: 02

[root@mime root]# dmesg
hub.c: USB new device connect on bus1/2, assigned device number 3
WARNING: USB Mass Storage data integrity not assured
USB Mass Storage device found at 3

[root@mime root]# cat /proc/scsi/usb-storage-0/0
   Host scsi0: usb-storage
       Vendor: SanDisk
      Product: Cruzer Micro
Serial Number: 1741510C5B125F7F
     Protocol: Transparent SCSI
    Transport: Bulk
         GUID: 078151511741510c5b125f7f
     Attached: Yes

[root@mime root]# cat /proc/partitions
major minor  #blocks  name

  22     0    3981096 hdc
  22     1      48163 hdc1
  22     2    3156772 hdc2
  22     3     763087 hdc3

THE SAME HAPPENS FOR sdb, sda1, sdb1, ...
[root@mime root]# mount -t auto /dev/sda /mnt/usb/
mount: /dev/sda is not a valid block device



There are some odd things, why the default kernel does not use SCSI to mound the devices? And my compiled kernel does use scsi to mound usb devices? Is that because of the CONFIG_SCSI enabled? I don't think so... anyway, there are two important things

1) I cannot use the default kernel (bacause it uses the RTC on irq_8 and I my driver does use the IRQ8 too).

2) I did try to rebuild the kernel using default .config file from red hat 7.3 but I am getting a failure.

Thanks in advance

---

### Post by giscardf on 2009-09-04
Just remembering that USB works for default kernel, but doesn't for the custome one.

Using the default kernel it is always mapped to /dev/sda1

Regards

---

### Post by giscardf on 2009-09-04
Hi guys,

Just to put something else here... 
I am digging on the internet the whole day, and it seems that I was supposed to "mount" the usb-storage device like a scsi one.... I believe this is something used at the beginning of usb support on linux.... so I do need someone with "old" experience, that will probably know how to do that....

The things are a lot easier today, I mean, we just plug and everything happens (btw, that is why I love ubuntu...:-)

Regards

---


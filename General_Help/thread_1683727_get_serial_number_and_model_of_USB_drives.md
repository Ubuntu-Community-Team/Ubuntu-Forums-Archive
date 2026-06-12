---
title: "get serial number and model of USB drives"
date: 2011-02-08
forum: General Help
---

### Post by izghitu on 2011-02-08
Hi,

I have Ubuntu 10.04 LTS.

I have a script that prompts you to insert a USB HDD/memory stick then  it needs to determine its serial and model and save it to a file.

The script can determine the device file of the inserted drive(ex: /dev/sdc) and if *hdparm -I /dev/sdc*  works then all is ok. The problem is that not all USB HDDs/memory  sticks work with hdparm. When it does not work I get the following:
```
root@izghitu:~# hdparm -I /dev/sdc

/dev/sdc:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange 
```The other command to get the serial for USB devices of any kind is *lsusb -v* or *lsusb -D /path/to/bus/address*

The problem of the first one(*lsusb -v*) is that it lists all USB  devices and there's no way for me to script it to detect the inserted  USB drive/memory stick and get the serial/model for it.

The problem with the second one(*lsusb -D /path/to/bus/address*) is that I do not know how to get the correct USB bus address of the inserted USB drive/memory stick.

So my questions are:
Is there any other way to get the serial number/model of a USB HDD/memory stick using its /dev/sdc device file?
Is there any way to link the /dev/sdc device file with the /dev/bus/usb/address device file so I can then use the *lsusb -D* command to get the required info?
Any other ideas?

Please help

Thanks

---

### Post by izghitu on 2011-02-08
I found a workaround. Whenever a USB drive/memory stick is inserted I can see this in dmesg:
```

[366230.279366] sd 9:0:0:0: [sdd] Attached SCSI removable disk

```

*9* from the *9:0:0:0:* thing can be used to determine the right device:
```

root@izghitu:~# cat /proc/scsi/usb-storage/9
   Host scsi9: usb-storage
       Vendor: USB
      Product: Flash Disk
Serial Number: 7006AD3DCCBF2DF1
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:

```

---

### Post by Rytron on 2011-03-11
> **izghitu said:**
> cat /proc/scsi/usb-storage/9

Works a charm. Thanks.

---


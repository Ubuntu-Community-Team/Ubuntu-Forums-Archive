---
title: "booting takes more than 2 minutes on a recent computer"
date: 2010-10-28
forum: General Help
---

### Post by schw3rt on 2010-10-28
my laptop(dell xps m1330) takes around 2'30" to boot, I don't remember when it started but it wasn't always that slow.
even looking at bootcharts I cant seem to figure out what that could be

full-size bootchart here: [http://bayimg.com/dAaMdaAdC](http://bayimg.com/dAaMdaAdC)
any suggestion is more than welcome

btw it powers down in less than 5 seconds

---

### Post by Quackers on 2010-10-29
I wish I could understand a bootchart output too :-(
Just out of interest, are any unnecessary usb devices plugged in at bootup?

---

### Post by oldfred on 2010-10-29
In addition to USB devices, does BIOS show floppy configured but you do not have one. 
One user had a CD in the tray and the system wanted to run fsck on the CD.
If you are mounting a NTFS partition and it needs chkdsk it can slow things down. Also fsck on all Linux partitions.

I like to look at logs in system, admin, log file viewer and see if something retries many times or has errors or a large gap in time.

---

### Post by schw3rt on 2010-10-29
nothing usb plugged,
no cd in the tray,
only the / partition mounting

I'm rebooting right now to check the logs

---

### Post by schw3rt on 2010-10-29
the only gap I see in the logs is
```
schwert-laptop kernel: [    2.273183] usb 3-2.1: configuration #1 chosen from 1 choice
schwert-laptop kernel: [    2.350046] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
schwert-laptop kernel: [    2.485187] usb 3-2.2: configuration #1 chosen from 1 choice
schwert-laptop kernel: [    2.562056] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
schwert-laptop kernel: [    2.693144] usb 3-2.3: configuration #1 chosen from 1 choice
schwert-laptop kernel: [    2.784191] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc0001ee80490]
schwert-laptop kernel: [   27.024543] udev: starting version 151
```

it also appears that I loose a lot of time(30") between the moment I enter my password in gdm and the moment my desktop becomes functional

---

### Post by oldfred on 2010-10-29
Do you have a firewire device attached. It looks like it is taking awhile to load that.

---

### Post by schw3rt on 2010-11-01
no firewire or anything else plugged in at startup except the power cord

---


---
title: "USB flash not recognizing"
date: 2012-08-21
forum: General Help
---

### Post by Blue1005 on 2012-08-21
I have a centon 16gb usb flash drive. I was trying to make it a bootable device for an OS and something went wrong. Now it says 0kb memory are on it and will not let me format it on win7. When i plug it in to UBUNTU it will not even recognize that it has been plugged it. Is there anything I can do to reset and or fix this issue?

---

### Post by mcduck on 2012-08-21
> **Blue1005 said:**
> I have a centon 16gb usb flash drive. I was trying to make it a bootable device for an OS and something went wrong. Now it says 0kb memory are on it and will not let me format it on win7. When i plug it in to UBUNTU it will not even recognize that it has been plugged it. Is there anything I can do to reset and or fix this issue?

Do you mean the device is not recognized, or that the partition/filesystem isn't recognized and mounted for you. Big difference between the two... ;)

Open a terminal and run "*tail -f /var/log/syslog*" and then plug in the drive. You should see messages about how the system recognizes the device, and possibly error messages related to accessing it or the filesystem.

If you don't see *any* messages appearign when you plug in the drive, there's nothing you can do apart from throwing the broken drive away and buying a new one.

However if the device is actually recognized, you could simply try deleting the existing partitions on it, and creatign & formatting a new one. The Disk Management tool included by default should be enough to do this, but feel free using Gparted or fdisk or something else if you want. :)

---

### Post by Blue1005 on 2012-08-21
the device on Ubuntu is not recognized at all. On win 7 it is recognized but shows 0kb of space. There has to be some way to fix it, i cant imagine a usb drive just bricking and being irreparable.

---

### Post by jroa on 2012-08-21
You could give this a try.

[http://www.wikihow.com/Repair-a-USB-Flash-Drive]("http://www.wikihow.com/Repair-a-USB-Flash-Drive")

---

### Post by mcduck on 2012-08-21
> **Blue1005 said:**
> the device on Ubuntu is not recognized at all. On win 7 it is recognized but shows 0kb of space. There has to be some way to fix it, i cant imagine a usb drive just bricking and being irreparable.

Not recognized at all meaning you ran the command I told you, and plugging in the device resulted in no log messages? In that case it is permanently dead.

edit: just to make it more clear, this is the log messages for a functional USB drive. Even a drive with broken partitions or filesystems should output at least some of these messages, possibly followed by some errors:
```
Aug 21 12:40:03 Hyperion kernel: [ 3162.068280] usb 2-1.1: new high-speed USB device number 4 using ehci_hcd
Aug 21 12:40:03 Hyperion mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Aug 21 12:40:03 Hyperion mtp-probe: bus: 2, device: 4 was not an MTP device
Aug 21 12:40:03 Hyperion kernel: [ 3162.190484] Initializing USB Mass Storage driver...
Aug 21 12:40:03 Hyperion kernel: [ 3162.191046] scsi6 : usb-storage 2-1.1:1.0
Aug 21 12:40:03 Hyperion kernel: [ 3162.191167] usbcore: registered new interface driver usb-storage
Aug 21 12:40:03 Hyperion kernel: [ 3162.191172] USB Mass Storage support registered.
Aug 21 12:40:03 Hyperion kernel: [ 3162.212904] usbcore: registered new interface driver uas
Aug 21 12:40:04 Hyperion kernel: [ 3163.188889] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
Aug 21 12:40:04 Hyperion kernel: [ 3163.191522] sd 6:0:0:0: Attached scsi generic sg2 type 0
Aug 21 12:40:04 Hyperion kernel: [ 3163.192318] sd 6:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
Aug 21 12:40:04 Hyperion kernel: [ 3163.193046] sd 6:0:0:0: [sdb] Write Protect is off
Aug 21 12:40:04 Hyperion kernel: [ 3163.193054] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
Aug 21 12:40:04 Hyperion kernel: [ 3163.193806] sd 6:0:0:0: [sdb] No Caching mode page present
Aug 21 12:40:04 Hyperion kernel: [ 3163.193816] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 12:40:04 Hyperion kernel: [ 3163.199554] sd 6:0:0:0: [sdb] No Caching mode page present
Aug 21 12:40:04 Hyperion kernel: [ 3163.199564] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 12:40:04 Hyperion kernel: [ 3163.290975]  sdb: sdb1
Aug 21 12:40:04 Hyperion kernel: [ 3163.295236] sd 6:0:0:0: [sdb] No Caching mode page present
Aug 21 12:40:04 Hyperion kernel: [ 3163.295240] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 12:40:04 Hyperion kernel: [ 3163.295242] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by Blue1005 on 2012-08-21
> **jroa said:**
> You could give this a try.

[http://www.wikihow.com/Repair-a-USB-Flash-Drive](http://www.wikihow.com/Repair-a-USB-Flash-Drive)


Definitely wont let me do that...

---

### Post by Blue1005 on 2012-08-21
> **mcduck said:**
> Not recognized at all meaning you ran the command I told you, and plugging in the device resulted in no log messages? In that case it is permanently dead.

edit: just to make it more clear, this is the log messages for a functional USB drive. Even a drive with broken partitions or filesystems should output at least some of these messages, possibly followed by some errors:
```
Aug 21 12:40:03 Hyperion kernel: [ 3162.068280] usb 2-1.1: new high-speed USB device number 4 using ehci_hcd
Aug 21 12:40:03 Hyperion mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Aug 21 12:40:03 Hyperion mtp-probe: bus: 2, device: 4 was not an MTP device
Aug 21 12:40:03 Hyperion kernel: [ 3162.190484] Initializing USB Mass Storage driver...
Aug 21 12:40:03 Hyperion kernel: [ 3162.191046] scsi6 : usb-storage 2-1.1:1.0
Aug 21 12:40:03 Hyperion kernel: [ 3162.191167] usbcore: registered new interface driver usb-storage
Aug 21 12:40:03 Hyperion kernel: [ 3162.191172] USB Mass Storage support registered.
Aug 21 12:40:03 Hyperion kernel: [ 3162.212904] usbcore: registered new interface driver uas
Aug 21 12:40:04 Hyperion kernel: [ 3163.188889] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
Aug 21 12:40:04 Hyperion kernel: [ 3163.191522] sd 6:0:0:0: Attached scsi generic sg2 type 0
Aug 21 12:40:04 Hyperion kernel: [ 3163.192318] sd 6:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
Aug 21 12:40:04 Hyperion kernel: [ 3163.193046] sd 6:0:0:0: [sdb] Write Protect is off
Aug 21 12:40:04 Hyperion kernel: [ 3163.193054] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
Aug 21 12:40:04 Hyperion kernel: [ 3163.193806] sd 6:0:0:0: [sdb] No Caching mode page present
Aug 21 12:40:04 Hyperion kernel: [ 3163.193816] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 12:40:04 Hyperion kernel: [ 3163.199554] sd 6:0:0:0: [sdb] No Caching mode page present
Aug 21 12:40:04 Hyperion kernel: [ 3163.199564] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 12:40:04 Hyperion kernel: [ 3163.290975]  sdb: sdb1
Aug 21 12:40:04 Hyperion kernel: [ 3163.295236] sd 6:0:0:0: [sdb] No Caching mode page present
Aug 21 12:40:04 Hyperion kernel: [ 3163.295240] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 12:40:04 Hyperion kernel: [ 3163.295242] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```


I will run it when i get home and see what it does. But by not recognizing i mean it will not pop up when i plug it in. Im not a super techie person so i have only tried different computers and OS' so far.

---

### Post by coredatarecovery on 2012-09-13
Have you cleaned the contacts on the drive?
sometimes corrosion or dirt will keep these devices from working properly.

---

### Post by Manhi40 on 2012-09-25
Have you tried the command lsusb?
it will show you if the system is recognizing your drive at all

---


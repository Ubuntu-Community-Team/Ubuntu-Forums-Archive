---
title: "unable to list ipod with fdisk -l"
date: 2011-01-04
forum: General Help
---

### Post by ymn_ayk on 2011-01-04
Here is my fdisk -l output:

[COLOR="black"][COLOR="DimGray"]yaman:/home/aykut# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2f09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14263   114567516   83  Linux
/dev/sda2           14264       14593     2650725    5  Extended
/dev/sda5           14264       14593     2650693+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004e9ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux[/COLOR][/COLOR]


And /var/log/messages:

[COLOR="DimGray"]yaman:/home/aykut# tail /var/log/messages
Jan  4 15:54:18 yaman kernel: [18250.388804] usb 5-3.2: SerialNumber: 000A27001A38E519
Jan  4 15:54:18 yaman kernel: [18250.734065] usb 5-3.2: USB disconnect, address 51
Jan  4 15:54:19 yaman kernel: [18251.193606] usb 5-3.2: new high speed USB device using ehci_hcd and address 52
Jan  4 15:54:19 yaman kernel: [18251.414788] usb 5-3.2: configuration #1 chosen from 2 choices
Jan  4 15:54:19 yaman kernel: [18251.475808] scsi747 : SCSI emulation for USB Mass Storage devices
Jan  4 15:54:19 yaman kernel: [18251.478052] usb 5-3.2: New USB device found, idVendor=05ac, idProduct=1262
Jan  4 15:54:19 yaman kernel: [18251.478052] usb 5-3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan  4 15:54:19 yaman kernel: [18251.478052] usb 5-3.2: Product: iPod
Jan  4 15:54:19 yaman kernel: [18251.478052] usb 5-3.2: Manufacturer: Apple Inc.
Jan  4 15:54:19 yaman kernel: [18251.478052] usb 5-3.2: SerialNumber: 000A27001A38E519 [/COLOR]   

I'm very confused!
What is the problem?
Thanks!

---

### Post by tredegar on 2011-01-04
ipods are not "disks", so will not show up with **fdisk**

When I plug in my itouch, it shows up in "Places" as **iPod** and when I open this with nautilus the location bar reads **afc://somerandonHEXsrting**

**afc** stands for "Apple File Control"

I can drag music to and from it using rhythmbox

---

### Post by psusi on 2011-01-04
Apple is the devil and uses proprietary communication protocols rather than behaving as a standard usb removable disk.

---

### Post by ymn_ayk on 2011-01-06
> **tredegar said:**
> ipods are not "disks", so will not show up with **fdisk**

When I plug in my itouch, it shows up in "Places" as **iPod** and when I open this with nautilus the location bar reads **afc://somerandonHEXsrting**

**afc** stands for "Apple File Control"

I can drag music to and from it using rhythmbox

Hi! I was able to see ipod with fdisk -l until now. I'm not sure, but I think we can consider ipod as "disk". 
I don't have any "Places" in my filesystem. I think it's a simple mount point.
Thanks

---

### Post by ymn_ayk on 2011-01-06
Ok,
there is a new thing to consider.
I can able to list with fdisk -l my ipod as a /dev/sde for 2-3 seconds, and then it disappears.
Oppss!!

---

### Post by ymn_ayk on 2011-01-06
Resolved!!
I have a usb device for multiple connections. It works with electricity, it wasn't connected to the electricity. 
Uppsss!

---


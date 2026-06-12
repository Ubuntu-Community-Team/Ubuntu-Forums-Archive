---
title: "Ipod not mounting anymore on 9.04"
date: 2009-10-09
forum: General Help
---

### Post by james.exe on 2009-10-09
For some reason, my ipod nano 4g doesn't appear to be mounted on my computer even though the screen of the actual ipod says that it's indeed connected. When I type "lsusb" into the terminal, this is my output
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:1263 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
```

Apparently, my computer is in fact reading the ipod but it does not appear on neither rhythmbox or my home folder. Is there anything I can do to fix this? My ipod was working fine before.

---

### Post by kanikilu on 2009-10-09
This might be completely unrelated, but have you by any chance connected this iPod to a computer (Win/Mac) running iTunes 9? I think I read somewhere that there is a new database structure that breaks compatibility with 3rd party applications like SharePod, etc., which I would assume would affect similar applications on linux (Amarok, Banshee, ...).

If not, is there anything in dmesg that might hint to why it's not mounting?

---

### Post by james.exe on 2009-10-09
I haven't updated to itunes 9 yet. A lot of code came up after typing "dmesg" and I'm not too sure how much of it is relevant to the ipod so I included the 12 lines above where it says "Apple iPod"

```
[   67.214753] wlan0: associated
[   67.217583] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   77.564033] wlan0: no IPv6 routers present
[ 1217.520195] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 1217.655479] usb 1-2: configuration #1 chosen from 2 choices
[ 1217.768216] Initializing USB Mass Storage driver...
[ 1217.769465] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1217.770875] usbcore: registered new interface driver usb-storage
[ 1217.770898] USB Mass Storage support registered.
[ 1217.776638] usb-storage: device found at 3
[ 1217.776653] usb-storage: waiting for device to settle before scanning
[ 1222.776590] usb-storage: device scan complete
[ 1222.779120] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1222.801936] sd 2:0:0:0: [sdb] 1946049 4096-byte hardware sectors: (7.97 GB/7.42 GiB)
[ 1222.802665] sd 2:0:0:0: [sdb] Write Protect is off
[ 1222.802684] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1222.802698] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1222.822474] sd 2:0:0:0: [sdb] 1946049 4096-byte hardware sectors: (7.97 GB/7.42 GiB)
[ 1222.823170] sd 2:0:0:0: [sdb] Write Protect is off
[ 1222.823190] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1222.823203] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1222.823229]  sdb: sdb1
[ 1222.830517] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 1222.830848] sd 2:0:0:0: Attached scsi generic sg1 type 0

```

Thanks for the reply btw

---

### Post by james.exe on 2009-10-10
bump

---

### Post by james.exe on 2009-10-10
bump

---

### Post by james.exe on 2009-10-10
bump

---

### Post by james.exe on 2009-10-10
bump

---

### Post by james.exe on 2009-10-10
bump

---

### Post by james.exe on 2009-10-11
bump

---

### Post by kanikilu on 2009-10-13
It looks like the iPod is being detected as sdb1. But you say it's not mounting? Can you post the output of the **mount** command from the Terminal?

Also, you could try mounting it manually, see the "Mounting the iPod" section of this page:

[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

Just replace /dev/sdc2 with /dev/sdb1. Also, you may want to use the UUID of the device instead of the path (/dev/sdb1). To find the UUID, type **ls -la /dev/disk/by-uuid** and look for the UUID that corresponds to the iPod.

---


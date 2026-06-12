---
title: "External USB HDD on 8.10 server"
date: 2010-02-26
forum: General Help
---

### Post by ScottMartin on 2010-02-26
I am having problems getting an External USB (cradle) HDD connected to our 8.10 server.

I currently have a RAID 1 on using a 3ware controller.
I wanted to add the USB for rsync.

The drive was formatted as ext3 and can be seen on other systems.

sda is my internal drive(s), RAID 1

```

? sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59466   477660613+  83  Linux
/dev/sda2           59467       60786    10602900    5  Extended
/dev/sda5           59467       60786    10602868+  82  Linux swap / Solaris

```

```

? cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: AMCC     Model: 9650SE-4LP DISK  Rev: 3.08
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: Optiarc  Model: DVD RW AD-7200A  Rev: 1.06
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi10 Channel: 00 Id: 00 Lun: 00
  Vendor:          Model:                  Rev:     
  Type:   Direct-Access                    ANSI  SCSI revision: 02

```

```

? dmesg
[14773194.349559] sd 9:0:0:0: [sdb] Attached SCSI disk
[14773194.349671] sd 9:0:0:0: Attached scsi generic sg2 type 0
[14781460.828395] usb 5-4: USB disconnect, address 7
[14781464.880030] usb 5-4: new high speed USB device using ehci_hcd and address 8
[14781465.031096] usb 5-4: configuration #1 chosen from 1 choice
[14781465.031421] scsi10 : SCSI emulation for USB Mass Storage devices
[14781465.031497] usb-storage: device found at 8
[14781465.031499] usb-storage: waiting for device to settle before scanning
[14781470.030148] usb-storage: device scan complete
[14781470.045258] scsi 10:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[14781470.080970] sd 10:0:0:0: [sdb] Attached SCSI disk
[14781470.081077] sd 10:0:0:0: Attached scsi generic sg2 type 0

```

```

 ? ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb

```

Messages shows the drive seen by kernel?
(So this means the BIOS has USB enabled, correct?)

```

Feb 23 16:41:44 ubuntu kernel: [14781460.828395] usb 5-4: USB disconnect, address 7
Feb 23 16:41:48 ubuntu kernel: [14781464.880030] usb 5-4: new high speed USB device using ehci_hcd and address 8
Feb 23 16:41:49 ubuntu kernel: [14781465.031096] usb 5-4: configuration #1 chosen from 1 choice
Feb 23 16:41:49 ubuntu kernel: [14781465.031421] scsi10 : SCSI emulation for USB Mass Storage devices
Feb 23 16:41:54 ubuntu kernel: [14781470.045258] scsi 10:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Feb 23 16:41:54 ubuntu kernel: [14781470.080970] sd 10:0:0:0: [sdb] Attached SCSI disk
Feb 23 16:41:54 ubuntu kernel: [14781470.081077] sd 10:0:0:0: Attached scsi generic sg2 type 0

```

My thought is sdb is my 2nd raid drive and the new drive should be sdc?

Any other thoughts on this, or what other actions I can perform?

Regards,
Scott.

---

### Post by ScottMartin on 2010-02-28
No comments on this? Any ideas?

Regards,
Scott.

---

### Post by ScottMartin on 2010-03-02
More Info: Any help would be appreciated

Kernel problem? 

```

 ? uname -r
2.6.27-11-server

```


```

 ? sudo lsusb
Bus 005 Device 008: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b39:1001 Omnidirectional Control Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by ScottMartin on 2010-03-02
This has been solved. I changed the USB cradle with another brand and it loads.

```

? sudo lsusb
**Bus 005 Device 009: ID 04fc:0c25 Sunplus Technology Co., Ltd **
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b39:1001 Omnidirectional Control Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Previous cradle was:
Bus 005 Device 008: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp.

---


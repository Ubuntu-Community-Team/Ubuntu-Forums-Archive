---
title: "sudo fdisk -l cant recognise my external hd"
date: 2011-02-12
forum: General Help
---

### Post by crunchichichi on 2011-02-12
as titled.
but I found my hard disk in disk utility named as /dev/sdb

I tried to mount it but still doesnt work

thanks

---

### Post by psusi on 2011-02-12
Too vague.  Be more specific.

---

### Post by bhaverkamp on 2011-02-12
Post the output of fdisk. There should be partitions. You really don't want to mount the raw disk. You can really screw things up. Your looking for something like /dev/sdb1.

---

### Post by crunchichichi on 2011-02-12
I installed MountManager

when I plugged my external hd
it comes out a bubble saying: New storage device with unknown file system was detected: /dev/sdb

Is my hard disk corrupted? :confused:

I cant remember my hard disk is in fat32 or ntfs...

what should I do?

---

### Post by crunchichichi on 2011-02-12
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37384   300281856   83  Linux
/dev/sda2           37384       38914    12286977    5  Extended
/dev/sda5           37384       38914    12286976   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc84b2af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

---

### Post by bhaverkamp on 2011-02-12
In a console window do a tail -f /var/log/messages

Then unplug and replug your external hd.

Post the messages.

---

### Post by crunchichichi on 2011-02-12
> **bhaverkamp said:**
> In a console window do a tail -f /var/log/messages

Then unplug and replug your external hd.

Post the messages.

debbie@debbie-L1010:~$ tail -f /var/log/messages
Feb 13 00:22:09 debbie-L1010 kernel: [41115.197079] sd 10:0:0:0: [sdb] Cache data unavailable
Feb 13 00:22:09 debbie-L1010 kernel: [41115.199449] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 13 00:22:09 debbie-L1010 kernel: [41115.201154] sd 10:0:0:0: [sdb] Cache data unavailable
Feb 13 00:22:09 debbie-L1010 kernel: [41115.242411]  sdb: sdb1
Feb 13 00:22:09 debbie-L1010 kernel: [41115.246825] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 13 00:22:09 debbie-L1010 kernel: [41115.248152] sd 10:0:0:0: [sdb] Cache data unavailable
Feb 13 00:22:09 debbie-L1010 kernel: [41115.248160] sd 10:0:0:0: [sdb] Attached SCSI disk
Feb 13 00:22:40 debbie-L1010 kernel: [41146.128033] usb 1-3: reset high speed USB device using ehci_hcd and address 10
Feb 13 00:23:11 debbie-L1010 kernel: [41177.168026] usb 1-3: reset high speed USB device using ehci_hcd and address 10
Feb 13 00:23:42 debbie-L1010 kernel: [41208.148025] usb 1-3: reset high speed USB device using ehci_hcd and address 10
Feb 13 00:24:07 debbie-L1010 kernel: [41233.354254] usb 1-3: USB disconnect, address 10
Feb 13 00:24:07 debbie-L1010 kernel: [41233.358120] sd 10:0:0:0: [sdb] Unhandled error code
Feb 13 00:24:07 debbie-L1010 kernel: [41233.358124] sd 10:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Feb 13 00:24:07 debbie-L1010 kernel: [41233.358128] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 60 00 3f 00 00 08 00
Feb 13 00:24:10 debbie-L1010 kernel: [41236.024027] ehci_hcd 0000:00:1a.7: PCI INT C disabled
Feb 13 00:24:14 debbie-L1010 kernel: [41239.860024] ehci_hcd 0000:00:1a.7: BAR 0: set to [mem 0xf2504800-0xf2504bff] (PCI address [0xf2504800-0xf2504bff])
Feb 13 00:24:14 debbie-L1010 kernel: [41239.860110] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Feb 13 00:24:14 debbie-L1010 kernel: [41240.128028] usb 1-3: new high speed USB device using ehci_hcd and address 11
Feb 13 00:24:14 debbie-L1010 kernel: [41240.263107] usb-storage 1-3:1.0: Quirks match for vid 05e3 pid 0702: 520
Feb 13 00:24:14 debbie-L1010 kernel: [41240.263135] scsi11 : usb-storage 1-3:1.0
Feb 13 00:24:15 debbie-L1010 kernel: [41241.273371] scsi 11:0:0:0: Direct-Access     SAMSUNG  HM160JC          0811 PQ: 0 ANSI: 0
Feb 13 00:24:15 debbie-L1010 kernel: [41241.275452] sd 11:0:0:0: Attached scsi generic sg2 type 0
Feb 13 00:24:15 debbie-L1010 kernel: [41241.275957] sd 11:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Feb 13 00:24:15 debbie-L1010 kernel: [41241.279090] sd 11:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 13 00:24:15 debbie-L1010 kernel: [41241.280818] sd 11:0:0:0: [sdb] Cache data unavailable
Feb 13 00:24:15 debbie-L1010 kernel: [41241.283442] sd 11:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 13 00:24:15 debbie-L1010 kernel: [41241.284954] sd 11:0:0:0: [sdb] Cache data unavailable
Feb 13 00:24:15 debbie-L1010 kernel: [41241.328665]  sdb: sdb1
Feb 13 00:24:15 debbie-L1010 kernel: [41241.331933] sd 11:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 13 00:24:15 debbie-L1010 kernel: [41241.333308] sd 11:0:0:0: [sdb] Cache data unavailable
Feb 13 00:24:15 debbie-L1010 kernel: [41241.333316] sd 11:0:0:0: [sdb] Attached SCSI disk
Feb 13 00:24:46 debbie-L1010 kernel: [41272.144034] usb 1-3: reset high speed USB device using ehci_hcd and address 11
Feb 13 00:25:17 debbie-L1010 kernel: [41303.124024] usb 1-3: reset high speed USB device using ehci_hcd and address 11
Feb 13 00:25:48 debbie-L1010 kernel: [41334.160027] usb 1-3: reset high speed USB device using ehci_hcd and address 11
Feb 13 00:26:19 debbie-L1010 kernel: [41365.200038] usb 1-3: reset high speed USB device using ehci_hcd and address 11
Feb 13 00:26:50 debbie-L1010 kernel: [41396.176025] usb 1-3: reset high speed USB device using ehci_hcd and address 11
Feb 13 00:27:21 debbie-L1010 kernel: [41427.152035] usb 1-3: reset high speed USB device using ehci_hcd and address 11
Feb 13 00:27:21 debbie-L1010 kernel: [41427.288360] sd 11:0:0:0: [sdb] Unhandled error code
Feb 13 00:27:21 debbie-L1010 kernel: [41427.288365] sd 11:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Feb 13 00:27:21 debbie-L1010 kernel: [41427.288372] sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 60 00 3f 00 00 08 00
Feb 13 00:27:52 debbie-L1010 kernel: [41458.128028] usb 1-3: reset high speed USB




  device using ehci_hcd and address 11
Feb 13 00:28:23 debbie-L1010 kernel: [41489.104035] usb 1-3: reset high speed USB device using ehci_hcd and address 11






not sure the process finished or not

---

### Post by crunchichichi on 2011-02-12
debbie@debbie-L1010:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/exthd
Error reading $MFT: Input/output error
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by wojox on 2011-02-12
What does this say?

```
sudo blkid
```

```
lsusb
```

---

### Post by crunchichichi on 2011-02-12
> **wojox said:**
> What does this say?

```
sudo blkid
```

```
lsusb
```

sudo blkid is keep loading..........

```
lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0c24:0022 Taiyo Yuden 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05c8:0114 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 012: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---


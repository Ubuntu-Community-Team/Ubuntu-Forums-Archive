---
title: "[jaunty 64bit] usb issues (data loss etc)"
date: 2009-08-23
forum: General Help
---

### Post by imhotep_ on 2009-08-23
hi guys.

following error occurs:
```

[  454.516563] usb 1-5: new high speed USB device using ehci_hcd and address 10
[  454.649816] usb 1-5: configuration #1 chosen from 1 choice
[  454.653128] scsi10 : SCSI emulation for USB Mass Storage devices
[  454.653284] usb-storage: device found at 10
[  454.653287] usb-storage: waiting for device to settle before scanning
[  459.652292] usb-storage: device scan complete
[  459.653234] scsi 10:0:0:0: Direct-Access     Sony     PSP              1.00 PQ: 0 ANSI: 0 CCS
[  459.675365] sd 10:0:0:0: [sdb] 8005632 512-byte hardware sectors: (4.09 GB/3.81 GiB)
[  459.680577] sd 10:0:0:0: [sdb] Write Protect is off
[  459.680582] sd 10:0:0:0: [sdb] Mode Sense: 00 ce 20 00
[  459.680587] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  459.682456] sd 10:0:0:0: [sdb] 8005632 512-byte hardware sectors: (4.09 GB/3.81 GiB)
[  459.682819] sd 10:0:0:0: [sdb] Write Protect is off
[  459.682823] sd 10:0:0:0: [sdb] Mode Sense: 00 ce 20 00
[  459.682827] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  459.682837]  sdb: sdb1
[  459.688740] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[  459.688858] sd 10:0:0:0: Attached scsi generic sg2 type 0

```so far, so good, i tried to disable the ehci_hcd module, but it isn't there :confused:
(i read somewhere that the module could be the culprit of my issues, namely
data loss and connection losses as mentioned right underneath ... it just takes forever and/or hangs completely with ubuntu resetting the device and so on.)
any suggestions?

```

[  146.788545] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  146.900048] usb 1-5: device descriptor read/64, error -32
[  147.120536] usb 1-5: device descriptor read/64, error -32
[  147.336568] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  147.448554] usb 1-5: device descriptor read/64, error -32
[  147.704071] usb 1-5: device descriptor read/64, error -32
[  147.916036] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  147.936620] usb 1-5: device descriptor read/8, error -32
[  148.056634] usb 1-5: device descriptor read/8, error -32
[  148.276037] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  148.297245] usb 1-5: device descriptor read/8, error -32
[  148.417248] usb 1-5: device descriptor read/8, error -32
[  148.520636] sd 8:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  148.520648] end_request: I/O error, dev sdb, sector 385696
[  148.520891] usb 1-5: USB disconnect, address 3
[  148.521455] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  148.521462] end_request: I/O error, dev sdb, sector 385936
[  148.526427] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  148.526436] end_request: I/O error, dev sdb, sector 386176
[  148.526487] Buffer I/O error on device sdb1, logical block 78
[  148.526491] lost page write due to I/O error on sdb1
[  148.526498] Buffer I/O error on device sdb1, logical block 79
[  148.526502] lost page write due to I/O error on sdb1
[  148.526509] Buffer I/O error on device sdb1, logical block 80
[  148.526513] lost page write due to I/O error on sdb1
[  148.526519] Buffer I/O error on device sdb1, logical block 81
[  148.526522] lost page write due to I/O error on sdb1
[  148.526528] Buffer I/O error on device sdb1, logical block 82
[  148.526531] lost page write due to I/O error on sdb1
[  148.526537] Buffer I/O error on device sdb1, logical block 83
[  148.526540] lost page write due to I/O error on sdb1
[  148.526546] Buffer I/O error on device sdb1, logical block 84
[  148.526549] lost page write due to I/O error on sdb1
[  148.526555] Buffer I/O error on device sdb1, logical block 85
[  148.526558] lost page write due to I/O error on sdb1
[  148.526564] Buffer I/O error on device sdb1, logical block 86
[  148.526567] lost page write due to I/O error on sdb1
[  148.526573] Buffer I/O error on device sdb1, logical block 87
[  148.526576] lost page write due to I/O error on sdb1
[  148.534433] FAT: unable to read inode block for updating (i_pos 35877)
[  148.534593] FAT: FAT read failed (blocknr 150)
[  148.534638] FAT: FAT read failed (blocknr 78)
[  148.534654] FAT: unable to read inode block for updating (i_pos 35877)
[  148.534713] FAT: FAT read failed (blocknr 150)
[  148.534737] FAT: FAT read failed (blocknr 78)
[  148.534751] FAT: unable to read inode block for updating (i_pos 35877)
[  148.545351] FAT: bread failed in fat_clusters_flush
[  148.545386] sd 8:0:0:0: [sdb] READ CAPACITY failed
[  148.545390] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  148.545397] sd 8:0:0:0: [sdb] Sense not available.
[  148.545430] sd 8:0:0:0: [sdb] Write Protect is off
[  148.545434] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  148.545438] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  148.564113] sd 8:0:0:0: [sdb] READ CAPACITY failed
[  148.564122] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  148.564129] sd 8:0:0:0: [sdb] Sense not available.
[  148.564206] sd 8:0:0:0: [sdb] Write Protect is off
[  148.564210] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  148.564215] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  148.576339] sd 8:0:0:0: [sdb] READ CAPACITY failed
[  148.576347] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  148.576354] sd 8:0:0:0: [sdb] Sense not available.
[  148.576428] sd 8:0:0:0: [sdb] Write Protect is off
[  148.576433] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  148.576437] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  148.740053] sd 8:0:0:0: [sdb] READ CAPACITY failed
[  148.740062] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  148.740069] sd 8:0:0:0: [sdb] Sense not available.
[  148.740144] sd 8:0:0:0: [sdb] Write Protect is off
[  148.740149] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  148.740153] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  149.373285] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  149.496573] usb 1-5: device descriptor read/64, error -32

```

some more info:
kernel 2.6.31.5-generic on jaunty
64 bit AMD dual core, 4 gb ram
nforce3 250 chipset

---

### Post by imhotep_ on 2009-08-23
sorry to solve this myself now, but the following worked for me, so as a help: ...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832)

thanks anyway

---


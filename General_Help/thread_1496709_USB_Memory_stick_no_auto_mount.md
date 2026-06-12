---
title: "USB Memory stick no auto mount"
date: 2010-05-29
forum: General Help
---

### Post by coolclassic on 2010-05-29
My 16gb usb memory stick now fails to mount. The device can be seen in gparted but partition is shown as unknown. Tried to format but error message popped up "failed". The device is shown in dmesg see below. I had tried to use the device to create a bootable usb but this did not work and the problems happen there after. Any advice?
dmesg:

usb 2-2: new high speed USB device using ehci_hcd and address 3
[41796.814297] usb 2-2: configuration #1 chosen from 1 choice
[41796.943922] Initializing USB Mass Storage driver...
[41796.944228] scsi2 : SCSI emulation for USB Mass Storage devices
[41796.944452] usbcore: registered new interface driver usb-storage
[41796.944459] USB Mass Storage support registered.
[41796.948661] usb-storage: device found at 3
[41796.948668] usb-storage: waiting for device to settle before scanning
[41801.940469] usb-storage: device scan complete
[41801.941393] scsi 2:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[41801.943766] sd 2:0:0:0: Attached scsi generic sg2 type 0
[41801.954934] sd 2:0:0:0: [sdb] 32768000 512-byte logical blocks: (16.7 GB/15.6 GiB)
[41801.955466] sd 2:0:0:0: [sdb] Write Protect is off
[41801.955472] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[41801.955474] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[41801.958025] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[41801.958035]  sdb: sdb1
[41802.208054] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[41802.208070] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[42124.865193] usb 2-2: USB disconnect, address 3
[42127.870251] usb 2-2: new high speed USB device using ehci_hcd and address 4
[42128.063882] usb 2-2: configuration #1 chosen from 1 choice
[42128.065257] scsi3 : SCSI emulation for USB Mass Storage devices
[42128.065571] usb-storage: device found at 4
[42128.065575] usb-storage: waiting for device to settle before scanning
[42133.060532] usb-storage: device scan complete
[42133.062190] scsi 3:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[42133.064527] sd 3:0:0:0: Attached scsi generic sg2 type 0
[42133.083879] sd 3:0:0:0: [sdb] 32768000 512-byte logical blocks: (16.7 GB/15.6 GiB)
[42133.086632] sd 3:0:0:0: [sdb] Write Protect is off
[42133.086638] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[42133.086641] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[42133.089624] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[42133.089636]  sdb: sdb1
[42133.340683] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[42133.340695] sd 3:0:0:0: [sdb] Attached SCSI removable disk

---

### Post by coolclassic on 2010-05-29
here is fdisk -l


Disk /dev/sdb: 16.8 GB, 16777216000 bytes
182 heads, 62 sectors/track, 2903 cylinders
Units = cylinders of 11284 * 512 = 5777408 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000107d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2904    16379904    b  W95 FAT32

---


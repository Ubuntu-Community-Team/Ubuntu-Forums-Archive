---
title: "Boot hangs for 60 seconds under 3.0.0-14-generic"
date: 2011-12-28
forum: General Help
---

### Post by jamkeb on 2011-12-28
Recently installed Xubuntu on Lenovo X100e. After upgrade to kernel 3.0.0-14 the boot-process pauses for 60 seconds (where it did not under previous kernel).

dmesg from 3.0.0-14-generic
```
[    1.869365]  sda: sda1 sda2
[    1.870021] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.871701] Initializing USB Mass Storage driver...
[    1.871795] usbcore: registered new interface driver usb-storage
[    1.871798] USB Mass Storage support registered.
[    1.883152] usb 2-1: USB disconnect, device number 2
[    1.894346] scsi1 : usb-storage 2-1:1.0
[    1.894701] usbcore: registered new interface driver ums-realtek
[    2.167195] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   62.368067] init: ureadahead main process (307) terminated with status 5
[   62.524456] udevd[357]: starting version 173
[   62.575896] Adding 4194300k swap on /dev/mapper/vgrootfs-lvswap.  Priority:-1 extents:1 across:4194300k 
[   62.583948] lp: driver loaded but no devices found
[   62.669166] EXT4-fs (dm-0): re-mounted. Opts: discard,errors=remount-ro
[   62.765450] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: discard
[   62.813137] EXT4-fs (dm-2): mounted filesystem with ordered data mode. Opts: discard
[   62.820072] wmi: Mapper loaded
```


dmesg from previous kernel:
```
[    1.957417]  sda: sda1 sda2
[    1.958132] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.287928] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    2.536587] init: ureadahead main process (338) terminated with status 5
[    2.697427] udevd[389]: starting version 173
[    2.759565] Adding 4194300k swap on /dev/mapper/vgrootfs-lvswap.  Priority:-1 extents:1 across:4194300k 
[    2.763529] lp: driver loaded but no devices found
[    2.864775] EXT4-fs (dm-0): re-mounted. Opts: discard,errors=remount-ro
[    2.924370] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: discard
[    2.942611] EXT4-fs (dm-2): mounted filesystem with ordered data mode. Opts: discard
[    3.031240] wmi: Mapper loaded
```

It appears to hang between EXT4-fs and ureadahead. This happens every boot under 3.0.0-14, but not when switching back to previous kernel.

Details: Xubuntu 11.10 (LVM and GPT) on a Lenovo x100e with Intel 320 SSD.

I don't know how to solve this, and I don't even know which logs to look in to find more information!

---

### Post by boomsb on 2012-01-04
I've noticed the same thing for a while now. Posting a recent dmesg log file which shows that udevd appears to take 60+ seconds to boot, during which time the machine appears to be locked with no HD or system activity.

Should probably also mention I've got LVM file system spanning a couple of drives for fun and excitement.

```

[    3.276588] EXT3-fs (sda5): orphan cleanup on readonly fs
[    3.276606] ext3_orphan_cleanup: deleting unreferenced inode 204015
[    3.276657] ext3_orphan_cleanup: deleting unreferenced inode 204014
[    3.276671] ext3_orphan_cleanup: deleting unreferenced inode 204013
[    3.276683] ext3_orphan_cleanup: deleting unreferenced inode 204009
[    3.276696] ext3_orphan_cleanup: deleting unreferenced inode 204007
[    3.276708] EXT3-fs (sda5): 5 orphan inodes deleted
[    3.276713] EXT3-fs (sda5): recovery complete
[    3.285042] EXT3-fs (sda5): mounted filesystem with ordered data mode
[    3.328106] firewire_core: created device fw0: GUID 00be51de006cf049, S400
[   78.232250] udevd[388]: starting version 173
[   78.285990] lp: driver loaded but no devices found
[   78.303641] Adding 9406020k swap on /dev/sda6.  Priority:-1 extents:1 across:9406020k
[   78.343796] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   78.343869] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   78.344797] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   78.380929] wmi: Mapper loaded

```

Edit:
Appears mine is a confirmed bug with udev and lvm2.

[https://answers.launchpad.net/ubuntu/+question/181615](https://answers.launchpad.net/ubuntu/+question/181615)

---


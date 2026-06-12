---
title: "external usb hdd spins up at login/logout"
date: 2010-01-25
forum: General Help
---

### Post by ckmod on 2010-01-25
Hi folks,

I am setting up an ubuntu box as a NAS for my private LAN. I am doing a nightly backup on an external usb drive (details see below). Here is the entry in /etc/fstab:
UUID=d7659f24-9c6c-4962-b767-f260d8e5bdc5 /media/backup1  ext4    rw,nodev,nosuid,noauto,noatime 0       0

Since I want to save energy I would like to put the hdd to sleep for the rest of the day. 

Searching the ubuntu forums an the internet I have come up with the following script to put the hdd to sleep:

```

#!/bin/bash
MOUNTPOINT=/media/backup1
DRIVE=/dev/sdb5
umount $MOUNTPOINT
# set power management
/sbin/hdparm -q -M 128 $DRIVE
/sbin/hdparm -q -S 12 $DRIVE
/sbin/hdparm -q -B 255 $DRIVE
/sbin/hdparm -q -y $DRIVE
eject $DRIVE
```This works fine and puts the hdd to sleep.

BUT: Whenever I do a login or logout at the gnome GUI the external drive spins up and will not go to sleep again.

Do you have any idea what is accessing the drive at login/logout?

Cheers,
Claus


Here further details on the hdd: Samsung SPINPOINT F2 ECOGREEN 1.5TB HD154UI CACHE 32MB RPM 5400 3.5IN 

Output of hdparm -I /dev/sdb5
```
ATA device, with non-removable media
        Model Number:       WDC WD5000AAKS-00TMA0
        Serial Number:      WD-WCAPW1454620
        Firmware Revision:  12.01C01
Standards:
        Supported: 7 6 5 4
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  976773168
        Logical/Physical Sector size:           512 bytes
        device size with M = 1024*1024:      476940 MBytes
        device size with M = 1000*1000:      500107 MBytes (500 GB)
        cache/buffer size  = 16384 KBytes
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 0
        Recommended acoustic management value: 128, current value: 128
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    64-bit World wide name
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12] (vendor specific)
                unknown 206[13] (vendor specific)
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
        122min for SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee2aaec102a
        NAA             : 5
        IEEE OUI        : 0014ee
        Unique ID       : 2aaec102a
Checksum: correct
```

---


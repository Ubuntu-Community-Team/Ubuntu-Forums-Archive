---
title: "hdparm set password / secure erase problem"
date: 2012-09-07
forum: General Help
---

### Post by anodec on 2012-09-07
Hi,

I'm trying to secure erase some drives. It works on one drive, but not on the other one:

Works on /dev/sdb:
> ubuntu@ubuntu:~$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
        Model Number:       WDC WD5000AADS-00S9B0                   
        Serial Number:      WD-WCAVbleeeeep
        Firmware Revision:  01.00A01
        Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
        Supported: 8 7 6 5 
        Likely used: 8
Configuration:
        Logical		max	current
        cylinders	16383	16383
        heads		16	16
        sectors/track	63	63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  976773168
        Logical/Physical Sector size:           512 bytes
        device size with M = 1024*1024:      476940 MBytes
        device size with M = 1000*1000:      500107 MBytes (500 GB)
        cache/buffer size  = unknown
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16	Current = 0
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled	Supported:
           *	SMART feature set
            	Security Mode feature set
           *	Power Management feature set
           *	Write cache
           *	Look-ahead
           *	Host Protected Area feature set
           *	WRITE_BUFFER command
           *	READ_BUFFER command
           *	NOP cmd
           *	DOWNLOAD_MICROCODE
            	Power-Up In Standby feature set
           *	SET_FEATURES required to spinup after power up
            	SET_MAX security extension
            	Automatic Acoustic Management feature set
           *	48-bit Address feature set
           *	Device Configuration Overlay feature set
           *	Mandatory FLUSH_CACHE
           *	FLUSH_CACHE_EXT
           *	SMART error logging
           *	SMART self-test
           *	General Purpose Logging feature set
           *	64-bit World wide name
           *	WRITE_UNCORRECTABLE_EXT command
           *	{READ,WRITE}_DMA_EXT_GPL commands
           *	Segmented DOWNLOAD_MICROCODE
           *	Gen1 signaling speed (1.5Gb/s)
           *	Gen2 signaling speed (3.0Gb/s)
           *	Native Command Queueing (NCQ)
           *	Host-initiated interface power management
           *	Phy event counters
           *	NCQ priority information
           *	DMA Setup Auto-Activate optimization
           *	Software settings preservation
           *	SMART Command Transport (SCT) feature set
           *	SCT Long Sector Access (AC1)
           *	SCT LBA Segment Access (AC2)
           *	SCT Error Recovery Control (AC3)
           *	SCT Features Control (AC4)
           *	SCT Data Tables (AC5)
            	unknown 206[12] (vendor specific)
            	unknown 206[13] (vendor specific)


Security: 
        Master password revision code = 65534
        	supported
        not	enabled
        not	locked
        not	frozen
        not	expired: security count
        	supported: enhanced erase
        106min for SECURITY ERASE UNIT. 106min for ENHANCED SECURITY ERASE UNIT.


Logical Unit WWN Device Identifier: 50014ee157e553c5
        NAA		: 5
        IEEE OUI	: 0014ee
        Unique ID	: 157e553c5
Checksum: correct



ubuntu@ubuntu:~$ sudo hdparm --user-master u --security-set-pass p /dev/sdb
security_password="p"

/dev/sdb:
 Issuing SECURITY_SET_PASS command, password="p", user=user, mode=high



ubuntu@ubuntu:~$ sudo hdparm --user-master u --security-erase p /dev/sdb
security_password="p"

/dev/sdb:
 Issuing SECURITY_ERASE command, password="p", user=user

(takes a long time to return ~2 hours)


Not working on /dev/sdc:
> 
ubuntu@ubuntu:~$ sudo hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
        Model Number:       WDC WD5000AAKS-65TMA0                   
        Serial Number:      WD-WCAPbleeeeep
        Firmware Revision:  12.01C01
Standards:
        Supported: 7 6 5 4 
        Likely used: 8
Configuration:
        Logical		max	current
        cylinders	16383	16383
        heads		16	16
        sectors/track	63	63
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
        R/W multiple sector transfer: Max = 16	Current = 0
        Recommended acoustic management value: 128, current value: 128
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled	Supported:
           *	SMART feature set
           *	Power Management feature set
           *	Write cache
           *	Look-ahead
           *	WRITE_BUFFER command
           *	READ_BUFFER command
           *	NOP cmd
           *	DOWNLOAD_MICROCODE
            	Power-Up In Standby feature set
           *	SET_FEATURES required to spinup after power up
           *	Automatic Acoustic Management feature set
           *	48-bit Address feature set
           *	Device Configuration Overlay feature set
           *	Mandatory FLUSH_CACHE
           *	FLUSH_CACHE_EXT
           *	SMART error logging
           *	SMART self-test
           *	General Purpose Logging feature set
           *	64-bit World wide name
           *	Segmented DOWNLOAD_MICROCODE
           *	Gen1 signaling speed (1.5Gb/s)
           *	Gen2 signaling speed (3.0Gb/s)
           *	Native Command Queueing (NCQ)
           *	Phy event counters
           *	DMA Setup Auto-Activate optimization
            	Device-initiated interface power management
           *	Software settings preservation
           *	SMART Command Transport (SCT) feature set
           *	SCT Long Sector Access (AC1)
           *	SCT LBA Segment Access (AC2)
           *	SCT Error Recovery Control (AC3)
           *	SCT Features Control (AC4)
           *	SCT Data Tables (AC5)
            	unknown 206[12] (vendor specific)
            	unknown 206[13] (vendor specific)


Security: 
        128min for SECURITY ERASE UNIT. 


Logical Unit WWN Device Identifier: 50014ee2002cb38f
        NAA		: 5
        IEEE OUI	: 0014ee
        Unique ID	: 2002cb38f
Checksum: correct




ubuntu@ubuntu:~$ sudo hdparm --user-master u --security-set-pass p /dev/sdc
security_password="p"

/dev/sdc:
 Issuing SECURITY_SET_PASS command, password="p", user=user, mode=high
SECURITY_SET_PASS: Input/output error



ubuntu@ubuntu:~$ sudo hdparm --user-master u --security-erase p /dev/sdc
security_password="p"

/dev/sdc:
 Issuing SECURITY_ERASE command, password="p", user=user
ERASE_PREPARE: Input/output error



ubuntu@ubuntu:~$ sudo hdparm --user-master u --security-erase NULL /dev/sdc
security_password=""

/dev/sdc:
 Issuing SECURITY_ERASE command, password="", user=user
ERASE_PREPARE: Input/output error


It's a different drive, but it says "128min for SECURITY ERASE UNIT." so I assume it can be erased.

Anyone know how to solve this?

---


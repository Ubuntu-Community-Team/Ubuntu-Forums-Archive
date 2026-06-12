---
title: "Low speed hard disk SATA."
date: 2009-11-13
forum: General Help
---

### Post by olegto on 2009-11-13
Hi, there!
  I ask some help. I don't know what to do with my hard disk, when I start copy from system disk to second hard disk, it's very slow and I don't may to work (my mouse is not move, and some program freeze, in another bad case, I have to reboot my computer).
  My hardware( Core 2 Duo 1.86 MhZ, Video Card Gforse, Memory 1 Gb, Hard 
Disk Western 250Gb (2 items).
  Here some information:
[PHP]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sdb5 during installation
UUID=9a48bddb-2c46-4779-9480-779277097111  /              ext4         errors=remount-ro      0  1  
# /home was on /dev/sdb7 during installation
UUID=612699e4-6938-4ec7-b50a-6e8d3b998f78  /home          ext4         defaults               0  2  
# /tmp was on /dev/sdb6 during installation
UUID=63cab08b-4e05-47a7-8050-579b7d05e014  /tmp           ext4         defaults               0  2  
# swap was on /dev/sda1 during installation
UUID=ca08634a-480c-4063-993e-7d193e47714f  none           swap         sw                     0  0  
# swap was on /dev/sdb1 during installation
UUID=b5a72a52-0ca3-4af6-b093-a3aeac4c16c3  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sda5                                  /media/sda5    ext4         users,user             0  0 
[/PHP]

---

### Post by Giblet5 on 2009-11-13
Strange.

It sounds like one, or both, of the drives are not operating in DMA mode. That would use the CPU a lot, causing all kinds of bad behavior.

It would be interesting to copy a large file and run the 'top' command to see what processes are using the most CPU time.

Do you have an option within BIOS setup to alter the drive access mode (PIO, UDMA, etc)?

---

### Post by tommcd on 2009-11-13
To check if DMA is enabled open a terminal and run:
```
sudo hdparm -I /dev/sdb
```
There should be something like this in the output:
```
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
```
The *udma6 indicates the DMA mode. You can repeat this for /dev/sda.
DMA problems are uncommon these days with modern systems. It won't hurt to check though

---

### Post by Giblet5 on 2009-11-13
> **tommcd said:**
> To check if DMA is enabled open a terminal and run:
```
sudo hdparm -I /dev/sdb
```
There should be something like this in the output:
```
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
```
The *udma6 indicates the DMA mode. You can repeat this for /dev/sda.
DMA problems are uncommon these days with modern systems. It won't hurt to check though

I've got an old HP box that somehow prevents automatic use of dma, and I had to jump through several hurdles to enable it.

(Ever edited a BIOS file with DOS debug.exe before? Burning that altered image, untested, to flash is a leap of faith...)

---

### Post by olegto on 2009-11-13
I don't know much about how HardDisk work and behave. I entered yours command and get that for sdb (System disk):
[PHP]
/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD2500AAKS-00VSA0                   
	Serial Number:      WD-WMART0548949
	Firmware Revision:  01.01B01
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
	LBA48  user addressable sectors:  488397168
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:      238475 MBytes
	device size with M = 1000*1000:      250059 MBytes (250 GB)
	cache/buffer size  = 16384 KBytes
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
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
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	DMA Setup Auto-Activate optimization
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
	50min for SECURITY ERASE UNIT. 50min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee055b881af
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 055b881af
Checksum: correct

[/PHP]

And second Hard disk:
[PHP]
/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD2500AAKS-00VSA0                   
	Serial Number:      WD-WMART0548949
	Firmware Revision:  01.01B01
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
	LBA48  user addressable sectors:  488397168
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:      238475 MBytes
	device size with M = 1000*1000:      250059 MBytes (250 GB)
	cache/buffer size  = 16384 KBytes
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
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
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	    	DMA Setup Auto-Activate optimization
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
	50min for SECURITY ERASE UNIT. 50min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee055b881af
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 055b881af
Checksum: correct
[/PHP]

---

### Post by olegto on 2009-11-13
> **Giblet5 said:**
> Strange.

It sounds like one, or both, of the drives are not operating in DMA mode. That would use the CPU a lot, causing all kinds of bad behavior.

It would be interesting to copy a large file and run the 'top' command to see what processes are using the most CPU time.

Do you have an option within BIOS setup to alter the drive access mode (PIO, UDMA, etc)?

No, I don't change anything in Bios, only I changed time setup and I changed Usb to Usb 2. Thanks everyone for help.

---

### Post by Giblet5 on 2009-11-13
Everything looks perfect.

What size files are we talking? How many?

I can try to reproduce it with that info. If I can reproduce it, I can probably figure out how to correct it.

---

### Post by olegto on 2009-11-14
> **Giblet5 said:**
> Everything looks perfect.

What size files are we talking? How many?

I can try to reproduce it with that info. If I can reproduce it, I can probably figure out how to correct it.

It's maybe file size 50 mb to 10 gb and contain 1 file or 100. In every case its work not properly. It's starts 20-30 Mb/s, and after a while slow down to 2-5 Mb/s. It's happen when I only do copy to second disc from device (usb HardDisk, or another HardDisk). Thank you.

---

### Post by Giblet5 on 2009-11-14
I have tried to reproduce this and cannot.

Same disk copies, disk to disk copies, USB disk to internal disk...they all complete without causing any noticeable problems.

My slowest transfers were same disk through the ethernet port copies, where I tached 33MB/s, and that was with scp (so it's being read/encrypted/decrypted/written - I expect slow).

I got nuthin'... Sorry.

---

### Post by olegto on 2009-11-15
Anyway thanks everyone for fast response and help.

---


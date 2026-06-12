---
title: "Copying files is really slow, is there anything I can do to speed it up?"
date: 2011-10-29
forum: General Help
---

### Post by mendhak on 2011-10-29
Recently, I purchased and installed Ubuntu on a [WesternDigital 1TB  mechanical hard drive]("http://www.storagereview.com/western_digital_caviar_blue_1tb_review_wd10ealx"). 

I've noticed that the file transfer (copy-paste) speeds are very slow compared to those in Windows 7.  

Creating a 1GB file:

```

$ dd if=/dev/urandom of=file.junk bs=1048576 count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 109.908 s, 9.5 MB/s

```

9.5 MB/s.

Then I tried timing file copies using [this bash script]("http://linuxconfig.org/bash-script-to-test-hard-drive-transfer-speed").


It came out to 92 MB/s.  I also tried it manually, about the same result.

[img]http://i.imgur.com/wcOpr.png[/img]



I tried copied a folder with many files in it.

[IMG]http://i.imgur.com/6lBSv.png[/IMG]


Yet this seems to contradict the disk utility benchmark.  Maybe the disk utility benchmark tests are too low level?  

[img]http://i.imgur.com/95TvQ.png[/img]



So after this, I had a look at Windows 7 and did a few tests there. 

Copying a large file

[img]http://i.imgur.com/SZG85.png[/img]


Creating a large file

[img]http://i.imgur.com/7Mea2.png[/img]



So I did some searching.  I was told to look at hdparm and set DMA to 1.    

```


$ sudo hdparm /dev/sda

/dev/sda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 121601/255/63, sectors = 1953525168, start = 0

```

Nothing about DMA in there.  I tried this command anyway:

```


$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

Then I tried hdparm with the -I switch and I think it is being treated as SATA 2 rather than SATA 3.

```

$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD10EALX-229BA1                     
	Serial Number:      WD-WCATR9226341
	Firmware Revision:  17.01H17
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
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
	LBA48  user addressable sectors: 1953525168
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:      953869 MBytes
	device size with M = 1000*1000:     1000204 MBytes (1000 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
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
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	   *	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	176min for SECURITY ERASE UNIT. 176min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee2b108315e
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 2b108315e
Checksum: correct


```


Any links, reading to do, anything will be appreciated, as my knowledge in regards to how Ubuntu deals with hard drives is non-existent.


Hardware info:  I am using an Asus P67 Sabertooth, and the hard drive is plugged in to the Intel SATA 3 controller port.  The CPU is an Intel i7 2600 K, stock speed.  I'm running Ubuntu 11.04 and Windows 7 x64.

---

### Post by TeoBigusGeekus on 2011-10-29
I'm guessing it's an ntfs hd.
Ntfs writing is fairly new to the linux world. Therefore the writing utilities that exist perform it very conservatively. If you do the same experiment with a fat system you'd get totally different results.

---

### Post by mendhak on 2011-10-29
Hi, the Windows 7 partition is indeed NTFS, but the Ubuntu partition is EXT4.  I am dual booting rather than running a VM if that's what you meant.

---

### Post by dcstar on 2011-10-30
Set up **cgroups** and see if things improve:

[http://www.serverwatch.com/tutorials/article.php/3921001/Setting-Up-Linux-Cgroups.htm](http://www.serverwatch.com/tutorials/article.php/3921001/Setting-Up-Linux-Cgroups.htm)

---


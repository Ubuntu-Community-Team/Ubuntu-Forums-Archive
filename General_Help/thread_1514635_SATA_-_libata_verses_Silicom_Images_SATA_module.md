---
title: "SATA - libata verses Silicom Images SATA module"
date: 2010-06-21
forum: General Help
---

### Post by zong1 on 2010-06-21
hi all,

  I installed Ubuntu 10.04, and happened to have an Silicom Images PCXpress card plugged in, and it kindly added the sil_sata module.  This is fine for this chip set.

I think that my earlier installation of Ubuntu 9.04 used Libata, which does support NCQ and also has good legacy support for the Intel Intel ICH7 chipset I have inside my Sony Vaio SZ notebook.  Also, libata also support Silicon Image chipsets as far as I can tell from 
[https://ata.wiki.kernel.org/index.php/Libata_Feature_Table](https://ata.wiki.kernel.org/index.php/Libata_Feature_Table)

I wish to remove the Silicom Images SATA modules and replace this with libata and then test the performance between the two device drivers.  

Q1:  I know that I can blacklist the Silicom Images module, but would Ubuntu then automatically insmod libata?

Q2:  What would happen to the local disc and the LVM paritions on it?  LVM should pick up the partitions from the UUID as far as I understand; Would changing the modules change the UUIDs?  I expect not.

Q3:  Libata causes each SATA port to appear as a new SCSI buse, and it may be  presented differently to the way the current Silicon Images drivers does it. (Apologies, but I have forgotten the actual module name. It may be sil_sata or sil32sata or lib_sata.)  Will the presentation cause LVM to be confused, or even worse, grub to be confused :  The internal disc is encrypted with dmcrypt.  I certainly won't want an unbootable system.

Any ideas?

Regards, z.

---

### Post by Xianath on 2010-06-21
I'm running 10.04 with 3 Silicon Image controllers (6 drives) and an AMD SB750 controller (6 more drives). I see the sata_sil24 module being loaded as well as atiixp, and all of my drives run with NCQ enabled. Have you checked whether your drives actually initialize with NCQ? See [this link]("https://ata.wiki.kernel.org/index.php/Libata_FAQ#Enabling.2C_disabling_and_checking_NCQ") for details. You may be worrying over nothing (fingers crossed :) )

---

### Post by zong1 on 2010-06-21
Looks like it is with a 32 depth, which surprised me.  I thought 32 depths could result in a reset, which is why libata limits to 31.

[    0.556386] ata3.00: ATA-8: ST9500420ASG, 0002SDM1, max UDMA/133
[    0.556391] ata3.00: 976773168 sectors, multi 16: LBA48 **NCQ (depth 0/32)**
[    0.573463] ata3.00: configured for UDMA/133

** It has been forced to disabled and use DMA**, because the actual value is set to 1 even though it is supported as per NCQ (depth 0/32).


# cat /sys/block/sda/device/queue_depth
**1**
# echo 31 > /sys/block/sda/device/queue_depth
bash: /sys/block/sda/device/queue_depth:** Permission denied**

sata_sil24 is loaded.
# lsmod |grep ata
sata_sil24             10949  0 

[I][U]
I would like to change to libata and see what I set with this driver instead of sata_sil24.  Anyone know how I could do this? [/U][/I] I do not know whether it has a bearing, but the disc is encrypted and has LVM.


Just ran hdparm on the disc in case its of interest.  Off topic, I notice that one cannot do a secure erase on the disc [ frozen] :(

```

# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       ST9500420ASG                            
	Serial Number:      5VJ0XXXX
	Firmware Revision:  0002SDM1
	Transport:          Serial
Standards:
	Used: unknown (minor revision code 0x0029) 
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
	cache/buffer size  = 16384 KBytes
	Nominal Media Rotation Rate: 7200
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 254
	Recommended acoustic management value: 208, current value: 208
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
	   *	Advanced Power Management feature set
	   *	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	WRITE_DMA_QUEUED_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Free-fall Control feature set
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	106min for SECURITY ERASE UNIT. 106min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c50018214d30
	NAA		: 5
	IEEE OUI	: 000c50
	Unique ID	: 018214d30
Checksum: correct

```

---

### Post by zong1 on 2010-06-22
Shameless bump.

Does anyone know how one can enable the NCQ on the disc?  Perhaps libata can do this?

---

### Post by zong1 on 2010-06-22
**Had a thought. ** 
Perhaps I could blacklist the sil24_sata module, and then reboot with the command option in grub   **insmod=libata**
Would this work, or cause any unfortunate results?

**Alternative vector:**
Which is the better driver for a motherboard with an Intel ICH7M SATA controller on it?  
e.g sata_sil24 (PC hasa PC-X Sil3132 controller also in it), libata or ata_piix (ICH  No TCQ/NCQ so no point).

Bear in mind that ACHI is disabled in the BIOS, and the customised BIOS was butchered by Sony Corp on the notebook, thus unable to enable ACHI.  [caveat emptor - Don't buy Sony Vaio : even if these do look sexy]

---

### Post by zong1 on 2010-06-22
I have just noticed that libata does not come with Ubuntu 10.04 by default.
Ahh.

# lsmod | grep ata
sata_sil24             10949  0 

# insmod libata
insmod: can't read 'libata': No such file or directory

I can see these packages for something similar, but don't know whether this is what I really want to install. Any ideas?

# apt-cache search libata
libatasmart-dev - ATA S.M.A.R.T. reading and parsing library - development files
libatasmart4 - ATA S.M.A.R.T. reading and parsing library
libatasmart-bin - ATA S.M.A.R.T. reading and parsing library - utilities

---


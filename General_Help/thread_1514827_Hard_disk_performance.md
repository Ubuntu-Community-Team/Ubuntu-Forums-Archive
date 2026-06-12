---
title: "Hard disk performance"
date: 2010-06-21
forum: General Help
---

### Post by ReyBrujo on 2010-06-21
Hey all,

I used to use Ubuntu 10.04 (32 bits) with an old computer (P4 2.8Ghz, 1.5Gb RAM, and two IDE hard disks, one 120Gb and 300Gb) until it broke. So, I built a new computer and installed one SATA disk, 1Tb with 64Mb cache, with Ubuntu 10.04 (64 bits). This computer, at least regarding copying information, is at least 5x times slower than my previous computer with IDE disks. To concatenate 12 files of 300MB each into a single one, it requires over 75 minutes. To concatenate 24 files of 300MB each, over two hours. With the IDE disks, it used to be done in 15-20 minutes.

Benchmark is as follows:

```
# hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   16912 MB in  2.00 seconds = 8464.24 MB/sec
 Timing buffered disk reads:  230 MB in  3.00 seconds =  76.54 MB/sec

```

Information:
```
# hdparm -I /dev/sda
/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD10EARS-00Z5B1                     
	Serial Number:      WD-WMAVU3124349
	Firmware Revision:  80.00A80
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
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
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
	274min for SECURITY ERASE UNIT. 274min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee600122edf
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 600122edf
Checksum: correct

```

System/Administration/Disk Utility shows it connected as a PATA instead of as a SATA disk. Readonly benchmark vary a bit but it is around min: 20MB/s, max: 110MB/s, avg: 78MB/s.

```
# lsmod
Module                  Size  Used by
f71882fg               29240  0 
coretemp                5345  0 
udf                    85529  0 
crc_itu_t               1715  1 udf
nls_utf8                1421  0 
isofs                  33399  0 
ses                     6683  0 
enclosure               8585  1 ses
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10802  0 
fat                    55350  1 vfat
usb_storage            49833  1 
xt_limit                2180  8 
xt_tcpudp               2667  13 
ipt_LOG                 5370  8 
ipt_MASQUERADE          1863  0 
xt_DSCP                 2277  0 
ipt_REJECT              2384  1 
nf_conntrack_irc        4429  0 
nf_conntrack_ftp        7126  0 
xt_state                1490  6 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   278890  1 
iptable_nat             5219  0 
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      12980  9 iptable_nat,nf_nat
nf_conntrack           73934  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  0 
iptable_filter          2791  1 
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22429  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_hda_intel          25645  4 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd                    70978  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64608  0 
bitblit                 5811  1 fbcon
soundcore               8052  1 snd
softcursor              1565  1 bitblit
serio_raw               4918  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
nvidia              10832442  28 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
pata_jmicron            2747  0 
ieee1394               94675  1 ohci1394
ahci                   37646  0 
r8169                  39650  0 
mii                     5237  1 r8169

```

Motherboard is a MSI X58 PRO-E, micro is I7 930, system with 2Gb 1333 RAM.

Performance increased somewhat when I added noatime, nodiratime, norelatime to the mounting options, but it is still really far from my old IDE disks. I used to think it was because I had connected some IDE stuff (to transfer information) but now there is nothing connected (I left the IDE cable connected to the port since it is a pain to plug it, in case I need to transfer something else from old disks, but nothing is connected to it).

Any suggestion will be appreciated. If you need more information, I can supply it without problem.

---

### Post by LoneWolfJack on 2010-06-21
there doesn't seem to be anything wrong with your drive.

you were probably reading from one and writing to the other disk with your IDE setup, which is of course MUCH faster.

---

### Post by dabl on 2010-06-21
In BIOS, change the SATA mode from "Legacy IDE" to "AHCI", then run ```
sudo hdparm -tT /dev/sda
``` three times in rapid succession (first time spins the drive up) and see if it is better.

That is a 5400 rpm drive and uses "green" (aka "slow") technology for power savings, FYI.  [http://www.wdc.com/en/products/products.asp?driveid=763](http://www.wdc.com/en/products/products.asp?driveid=763)

---

### Post by ReyBrujo on 2010-06-21
> **LoneWolfJack said:**
> there doesn't seem to be anything wrong with your drive.

you were probably reading from one and writing to the other disk with your IDE setup, which is of course MUCH faster.
Thanks for the quick response!

Could it be that I am using a swap file on this hd instead of using a partition as before? I read the performance should be the same with the 2.6 kernel, so I chose it. Even if I were to add a second hard drive, I believe 75 minutes to build up a 4gb file is terrible. It is less than 1mb/s. That is why I am surprised, as the benchmarks don't look bad, but at runtime it is.

Calculating the md5 for the 4gb file takes 1'11'' only, so I am guessing it has to do with writing and not reading.

---

### Post by cascade9 on 2010-06-21
OK, I know what the problem is-

WDC10EARS. 

I'm sorry to tell you, that is an WD drive that uses 'advanced format'. Which means that it uses 4k sectors, not the typical 512b sectors. 

If the drive isnt 'aligned' then you have exactly that issue- its %##$^ slow. 

I've actually just had one walk into my life, just today, and I've been half thinking about making a thread here about how to format/partition the thing right. I've found a few guides on the net about how to make a single partition aligned, but nothing on making muliuple partitions (which is what the owner of the EARS 1TB driver in my hands needs). 

Its 5AM now, and I'm going to bed, but if you want to make a thread on the issue (or if some kind person finds this and posts here) I'm looking for the information..........I've played with hardware for years, and this is the 1st time that somethign liek this has happened to me. I'm unimpressed :(

---

### Post by ReyBrujo on 2010-06-21
> **dabl said:**
> In BIOS, change the SATA mode from "Legacy IDE" to "AHCI", then run ```
sudo hdparm -tT /dev/sda
``` three times in rapid succession (first time spins the drive up) and see if it is better.

That is a 5400 rpm drive and uses "green" (aka "slow") technology for power savings, FYI.  [http://www.wdc.com/en/products/products.asp?driveid=763](http://www.wdc.com/en/products/products.asp?driveid=763)
Well, I had set AHCI before, but since it didn't display the SATA connections in the BIOS main screen, I thought it would not boot, so I kept RAID at IDE. Now I disabled IDE Busmaster, and changed RAID setting to AHCI. Ubuntu Disk Utility now recognizes the HD as SATA instead of PATA, and is working much faster:

```
# hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   18566 MB in  2.00 seconds = 9293.01 MB/sec
 Timing buffered disk reads:  302 MB in  3.02 seconds = 100.07 MB/sec

```

Catting the 4Gb file together now takes 4 minutes instead of the 75 of old. For the sake of completion, here are the benchmark pictures from before the BIOS modifications:

[img]http://ubuntuforums.org/attachment.php?attachmentid=161132&stc=1&d=1277154766[/img]

and the new one:

[img]http://ubuntuforums.org/attachment.php?attachmentid=161133&stc=1&d=1277154766[/img]

It is much consistent (there were lots of hiccups before, which impacted in the minimum read rate). Thanks again all of you, this is the first machine I had with SATA disks, so I knew something was missing. Thanks again!

---

### Post by albertwt on 2010-11-08
> **cascade9 said:**
> OK, I know what the problem is-

WDC10EARS. 

I'm sorry to tell you, that is an WD drive that uses 'advanced format'. Which means that it uses 4k sectors, not the typical 512b sectors. 

If the drive isnt 'aligned' then you have exactly that issue- its %##$^ slow. 

I've actually just had one walk into my life, just today, and I've been half thinking about making a thread here about how to format/partition the thing right. I've found a few guides on the net about how to make a single partition aligned, but nothing on making muliuple partitions (which is what the owner of the EARS 1TB driver in my hands needs). 

Its 5AM now, and I'm going to bed, but if you want to make a thread on the issue (or if some kind person finds this and posts here) I'm looking for the information..........I've played with hardware for years, and this is the 1st time that somethign liek this has happened to me. I'm unimpressed :(

thanks for the explanation man, I appreciate that I'm also using [http://www.wdc.com/en/products/products.asp?DriveID=866]("http://www.wdc.com/en/products/products.asp?DriveID=866") the same drive for my server 2x 1 TB RAID-1 it has problem/warning like the following > Level of Disk write latency above 65 Millisecond consistently between 6-7 AM in the morning (from the monitoring script).

So can we say that this drive is not for web server usage then ?

---

### Post by mastablasta on 2010-11-08
no, but we can say it should be propperly aligned first and then used. i have it on WinXP and suse as server data storage. WD directed me to 3rd party programme that does that in WinXP. so before i started using the disk i read all manuals and aligned it. i believe it can probably be done in Linux as well, however i don't know how to do it.

---

### Post by albertwt on 2010-11-08
> **mastablasta said:**
> no, but we can say it should be propperly aligned first and then used. i have it on WinXP and suse as server data storage. WD directed me to 3rd party programme that does that in WinXP. so before i started using the disk i read all manuals and aligned it. i believe it can probably be done in Linux as well, however i don't know how to do it.

thanks for the reply man, so we must re-align it first before we introduce this disk into the RAID-1 configuration ?

---


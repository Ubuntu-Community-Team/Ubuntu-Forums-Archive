---
title: "wipper.sh fails, input/output error"
date: 2010-03-19
forum: General Help
---

### Post by monkman on 2010-03-19
```
monkman@pc:~/Downloads/hdparm-9.28$ sudo /sbin/wiper.sh --commit /dev/sda6

wiper.sh: Linux SATA SSD TRIM utility, version 2.6, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda6 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (5926453 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 11852912 sectors from 931 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Aborted.

```

any ideas what goes wrong here? i got the intel x25-v ssd, ubuntu 9.10 64bit, kernel 2.6.32.

thx!

---

### Post by Footer on 2010-05-04
Did you ever get your problem figured out?  I"m having the same issues:

```
footer@kubuntu64:~$ sudo /sbin/wiper.sh /dev/sdc1 --commit

wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sdc1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (24390500 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sdc:
trimming 27099135 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 18554281 sectors from 512 ranges
FAILED: Input/output error

/dev/sdc:
trimming 1999248 sectors from 512 ranges
FAILED: Input/output error

/dev/sdc:
trimming 893128 sectors from 512 ranges
FAILED: Input/output error

/dev/sdc:
trimming 235208 sectors from 138 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Done.
footer@kubuntu64:~$
```

It succeeds on the larger sector but fails on the rest.  I've run fsck on my 32GB OCZ-Vertext SSD and it comes back clean.  It was working fine under Kubuntu 9.04, seems it just started under 10.04.  My kernel is 2.6.32-21-generic.

Any thoughts would be appreciated!

---

### Post by monkman on 2010-05-04
i'm afraid not. running windows 7 now and the intel toolbox... for now no linux left here...

---

### Post by Footer on 2010-05-04
Ahh, too bad (or good for you!) depending on how you look at it.  :)

I hope that wasn't the reason you went back to Windows.  Re: the subject problem, I ran wiper.sh many times in a row and the last time, I got this:

```
footer@kubuntu64:~$ sudo /sbin/wiper.sh /dev/sdc1 --commit

wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sdc1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (24390444 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sdc:
trimming 27099135 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 18554281 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 1999248 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 893128 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 235096 sectors from 138 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Done.
footer@kubuntu64:~$ 

```

So I'm not sure what's going on but I'll keep looking.  I assume everything works fine in Windows and your SSD gets trimmed automagically?

---

### Post by habtool on 2010-05-04
I have contacted Mark Lord, the Trim/hdparm developer, and will post back here if I hear back from him. I sent him a message on the projects source-forge page.

I sent him this:

Hi
On Ubuntu Lucid LTS 10.04
Kernel 2.6.32-22-generic
i686
hdparm-9.28
wiper.sh: Linux SATA SSD TRIM utility, version 2.6, by Mark Lord.

Also a post on ubuntu forums where other are having the problem:
[http://ubuntuforums.org/showthread.php?p=9234802](http://ubuntuforums.org/showthread.php?p=9234802)

sudo ./wiper.sh --commit /dev/sdc5

wiper.sh: Linux SATA SSD TRIM utility, version 2.6, by Mark Lord.
Preparing for offline TRIM of free space on /dev/sdc5 (ext4 non-mounted).

This operation could silently destroy your data.  Are you sure (y/N)? y
Syncing disks.. 
Beginning TRIM operations..

/dev/sdc:
trimming 32870688 sectors from 5724 ranges
FAILED: Input/output error
Aborted.

---

### Post by monkman on 2010-05-04
i'd love to use ubuntu as "mainsystem", need windows though for some certain things but only once a month.

got an asus xonar essence st, which doesn't do what i want under linux... should run, but doesn't. and then there is the thing about resampling in alsa...

in my opinion windows sucks. big time. usability is horrible. wtf do i need antivirus software for? just slows down my system and costs me money...

and the nsa backdoors... just doesn't feel right.

ubuntu felt just right...

---

### Post by Footer on 2010-05-04
Ahh, well, I do hope you get back to Ubuntu soon monkman!

And habtool, thanks for your persistence on this issue.  Looking forward to hearing back from the developer.  I had no issues while running under 9.10 (I misstated 9.04 in an earlier post) so I'm thinking it might have to do with the newer kernel?

Thanks.

---

### Post by psusi on 2010-05-04
The x-25 does not support TRIM.

---

### Post by monkman on 2010-05-04
then what does the intel toolbox tool do? it's just called "optimizes"...

thx!

---

### Post by psusi on 2010-05-04
> **monkman said:**
> then what does the intel toolbox tool do? it's just called "optimizes"...

thx!

No idea, but everything I've read says that the Intel SSDs do not support TRIM.

---

### Post by ariel on 2010-05-20
> **psusi said:**
> No idea, but everything I've read says that the Intel SSDs do not support TRIM.


this is incorrect. X-25M generation 2 supports TRIM, as reported by hdparm.

However for some reason wiper.sh fails in lucid, even the intel-patched versions. 

Anyone succeded in getting wiper.sh to work on an x25-M?

---

### Post by spoon_ on 2010-05-22
I'm in the same boat! wiper.sh fails on X25-M G2 80GB on Lucid 64-bit.

Well, at least it doesn't trash my data, I guess.

---

### Post by 98cwitr on 2010-05-26
bump...add me to the failed list. I've contacted Mark Lord about it.

---

### Post by Footer on 2010-06-02
Update on this.  Running:
```

wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
hdparm - get/set hard disk parameters - version v9.28, by Mark Lord.

```
and kernel:
```

Linux kubuntu64 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```
I get the dreaded:
```

FAILED: Input/output error

```
But using the same tools on the same disk with kernel 2.6.31, it succeeds as expected.  So it must be a kernel issue.  Which would make sense because it always worked for me under Kubuntu 9.10 but started failing under 10.04.

Maybe the next kernel update will fix?  Fingers crossed!

:)

---

### Post by ariel on 2010-06-02
> **Footer said:**
> Update on this.  Running:
```

wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
hdparm - get/set hard disk parameters - version v9.28, by Mark Lord.

```and kernel:
```

Linux kubuntu64 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```I get the dreaded:
```

FAILED: Input/output error

```But using the same tools on the same disk with kernel 2.6.31, it succeeds as expected.  So it must be a kernel issue.  Which would make sense because it always worked for me under Kubuntu 9.10 but started failing under 10.04.

Maybe the next kernel update will fix?  Fingers crossed!

:)

or an hdparm issue with 2.6.32? I hope the latter is true because if we need to change kernels that would be really risky for the box stability, I'm not sure what would be worst (no wiper.sh or an unstable system).

---

### Post by Footer on 2010-06-04
Just got an update to the 2.6.32 kernel:

```
Linux kubuntu64 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

and now trim is working again:

```
footer@kubuntu64:~$ sudo /sbin/wiper.sh /dev/sdc1 --commit

wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sdc1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (24279259 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sdc:
trimming 25034751 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 20590505 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 2117720 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 815544 sectors from 374 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

```

WHOOHOO!!!  Anyone else?

:)

---

### Post by cmavr8 on 2010-06-05
> **Footer said:**
> Just got an update to the 2.6.32 kernel:

```
Linux kubuntu64 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

and now trim is working again:

```
footer@kubuntu64:~$ sudo /sbin/wiper.sh /dev/sdc1 --commit

wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sdc1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (24279259 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sdc:
trimming 25034751 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 20590505 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 2117720 sectors from 512 ranges
succeeded

/dev/sdc:
trimming 815544 sectors from 374 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

```

WHOOHOO!!!  Anyone else?

:)


Not fixed for me...
Used to work on my previous installation but I haven't tried it after fresh-installing 10.04 and it doesn't work now that I did.

```

$ uname -r
2.6.32-22-generic
```

---

### Post by Footer on 2010-06-05
> **cmavr8 said:**
> Not fixed for me...
Used to work on my previous installation but I haven't tried it after fresh-installing 10.04 and it doesn't work now that I did.

```

$ uname -r
2.6.32-22-generic
```

Hmmmm ... Try uname -a:

```
footer@kubuntu64:~$ uname -a
Linux kubuntu64 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

```

Note the #36 in the line for my kernel?  Before the upgrade yesterday, it was #33.  So I guess this means it was a very minor update?  Nonetheless, #33 kernel: wiper FAIL, #36 kernel: wiper SUCCESS!!!

:)

---

### Post by agmlego on 2010-06-05
Having this issue with an OCZ Vertex Turbo 30GB drive, running firmware version 1.5. hdparm says the drive has TRIM support enabled. Kernel is #36 on the 2.6.32-22 generic on Ubuntu 10.04. hdparm is newest from SourceForce, 9.28.

---

### Post by Footer on 2010-06-05
Dangit!  I've got the OCZ Vertex 30GB:

	Model Number:       OCZ-VERTEX
	Firmware Revision:  1.4

I must just be lucky I guess???

---

### Post by cmavr8 on 2010-06-05
> **Footer said:**
> 
Note the #36 in the line for my kernel?  Before the upgrade yesterday, it was #33.  So I guess this means it was a very minor update?  Nonetheless, #33 kernel: wiper FAIL, #36 kernel: wiper SUCCESS!!!

:)

Thanks!
I also have #36 but no go... I guess you're right... you're just lucky to have an OCZ.

I've got an Intel x-25 g2.

---

### Post by Footer on 2010-06-05
Well, agmlego (post #19) has an OCZ Vertex Turbo 30GB with a newer firmware than mine and his isn't working ...

:(

---

### Post by ariel on 2010-06-05
> **cmavr8 said:**
> Thanks!
I also have #36 but no go... I guess you're right... you're just lucky to have an OCZ.

I've got an Intel x-25 g2.

same here. same ssd, kernel #36, x64, still getting FAILED: input/output errors  :(

---

### Post by Footer on 2010-06-06
Well folks, I'm not completely out of the woods yet ... Ran it this morning:

```
sudo /sbin/wiper.sh /dev/sdc1 --commit
```

and it failed.  Ran it again and it succeeded.  I don't know what's going on but mine's not perfect either it seems ...

:(

---

### Post by spmurphy on 2010-06-06
mine seems to work. run multiple times, no reported failures.

```
~/src/wiper-2.5$ sudo ./wiper-intel.sh /dev/sda1 --commit

wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (68347153 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 31096829 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31260675 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31195133 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31375363 sectors from 512 ranges
succeeded

/dev/sda:
trimming 11766312 sectors from 197 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

```

```
~/src/wiper-2.5$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       INTEL SSDSA2M080G2GC                    
	Serial Number:        
	Firmware Revision:  2CV102HD
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 1 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  156301488
	LBA48  user addressable sectors:  156301488
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	device size with M = 1024*1024:       76319 MBytes
	device size with M = 1000*1000:       80026 MBytes (80 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 1
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
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	Data Set Management TRIM supported
	   *	Deterministic read ZEROs after TRIM
```

```
hdparm_9.27-2ubuntu1_amd64.deb
```

```
2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

---

### Post by cmavr8 on 2010-06-06
I'm using hdparm 9.28 (in contrast to your 9.27) and wiper 2.6 (you're using 2.5).

Tried your version but still no go...

Thanks for sharing, though!

EDIT: your firmware revision is 2CV102HD but mine is 2CV102HA.
Looking for an upgrade...

EDIT: Upgraded to newest FW: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18363](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18363)
No use!

---

### Post by ariel on 2010-06-06
> **spmurphy said:**
> mine seems to work. run multiple times, no reported failures.

```
~/src/wiper-2.5$ sudo ./wiper-intel.sh /dev/sda1 --commit

wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (68347153 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 31096829 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31260675 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31195133 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31375363 sectors from 512 ranges
succeeded

/dev/sda:
trimming 11766312 sectors from 197 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

``````
~/src/wiper-2.5$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       INTEL SSDSA2M080G2GC                    
    Serial Number:        
    Firmware Revision:  2CV102HD
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
    Used: ATA/ATAPI-7 T13 1532D revision 1 
    Supported: 7 6 5 4 
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  156301488
    LBA48  user addressable sectors:  156301488
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:       76319 MBytes
    device size with M = 1000*1000:       80026 MBytes (80 GB)
    cache/buffer size  = unknown
    Nominal Media Rotation Rate: Solid State Device
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 1
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
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
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
            Device-initiated interface power management
       *    Software settings preservation
       *    Data Set Management TRIM supported
       *    Deterministic read ZEROs after TRIM
``````
hdparm_9.27-2ubuntu1_amd64.deb
``````
2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```



Well I have the same intel SSD, same firmware, same hdparm version, same kernel version. And wiper.sh still doesn't work.

Would you mind attaching the wiper-intel.sh script that's working for you?

Thanks!

---

### Post by spmurphy on 2010-06-09
attached.

---

### Post by cmavr8 on 2010-06-09
WORKED!
Thanks so much!

---

### Post by runesvend on 2010-06-09
I have an 80GB Intel X25-M G2, with firmware version 2CV102DH and I'm running the same kernel as you guys:

```
Linux runescomp 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```

But I still get those "Input/output" errors with the script spmurphy attached.

Any ideas? This seems so strange. Sometimes it works and sometimes it doesn't, and some get it working running the script multiple times in a row... (doesn't work for me though, I've tried that too)

---

### Post by ariel on 2010-06-10
> **runesvend said:**
> I have an 80GB Intel X25-M G2, with firmware version 2CV102DH and I'm running the same kernel as you guys:

```
Linux runescomp 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```But I still get those "Input/output" errors with the script spmurphy attached.

Any ideas? This seems so strange. Sometimes it works and sometimes it doesn't, and some get it working running the script multiple times in a row... (doesn't work for me though, I've tried that too)

no joy here either, it just doesn't work.

if anyone figures this one out... please post your findings :|

---

### Post by josephellengar on 2010-06-12
Wow!  The wiper-intel script finally worked for me!  Thanks!

Anyway, this seems to be a crowd of ssd owners, so I might as well ask my question here.  I upgrade to the 2.6.34 kernel but decided to downgrade again because I was worried about not getting security fixes.  Anyway, I left the discard option in my fstab and it seems like the discard option is working on my kernel 2.6.32 version.  Is that possible?

---

### Post by runesvend on 2010-06-12
I'm wondering if we could get people to post their various configurations (SSD brand, model, firmware version and kernel version), and whether the wiper script works for them or not. Also, if it only works intermittently, it would be useful to know this as well.

So the following information would be useful:

[INDENT]**1. SSD manufacturer, model and firmware version**

This can be obtained by executing the following command:

```
sudo hdparm -i /dev/sda | grep "Model"
```

**2. Kernel version** ("uname -a" command)
**3. Does the wiper script work?** (Always? Never? Sometimes?)[/INDENT]

Maybe we'll be able to see a trend and figure out the problem if we get this information from people. It might also be useful in a bug report.


I'll start out with my info:

[INDENT]**1. SSD manufacturer, model and firmware version**:
```
 Model=INTEL SSDSA2M080G2GC, FwRev=2CV102HD, SerialNo=CVPO927601R2080BGN

```

**2. Kernel version**:
```
Linux runescomp 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```

**3. Does the wiper script work?**:
Never works.[/INDENT]

---

### Post by josephellengar on 2010-06-12
1. SSD manufacturer, model and firmware version

Model=INTEL SSDSA2M160G2GC, FwRev=2CV102HD

2. Kernel version ("uname -a" command)

2.6.32-22-generic
I have this discard option enabled on my fs.  Using this on an ext4 fs mounted rw.

3. Does the wiper script work? (Always? Never? Sometimes?)
Using the wiper.sh Intel version.  Claims to work, even though I am using hdparm 9.15, which shouldn't be a high enough version.  Using the non-intel version never works.

---

### Post by cmavr8 on 2010-06-12
Here's mine:

[INDENT]**1. SSD manufacturer, model and firmware version**:
```
Model=INTEL SSDSA2M080G2GC, FwRev=2CV102HD, SerialNo=CVPO002501QS080BGN

```

**2. Kernel version**:
```
Linux **** 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

**3. Does the wiper script work?**:
Always works.[/INDENT]

---

### Post by ariel on 2010-06-12
**1. SSD manufacturer, model and firmware version**:
 	Code:
 	Model=INTEL SSDSA2M080G2GC, FwRev=2CV102HD, SerialNo=CVPO006423QR070BGN 
**2. Kernel version**:
 	Code:
 	Linux ***** 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux 
**3. Does the wiper script work?**:
No, could never get it to work. Tried tons of hdparm versions.

---

### Post by ariel on 2010-06-12
> **rossholley said:**
> Wow!  The wiper-intel script finally worked for me!  Thanks!

Anyway, this seems to be a crowd of ssd owners, so I might as well ask my question here.  I upgrade to the 2.6.34 kernel but decided to downgrade again because I was worried about not getting security fixes.  Anyway, I left the discard option in my fstab and it seems like the discard option is working on my kernel 2.6.32 version.  Is that possible?

which kernel did you get the script to work with? (.34, .32, both?)

---

### Post by josephellengar on 2010-06-12
> **ariel said:**
> which kernel did you get the script to work with? (.34, .32, both?)

The intel-specific script worked on .32.  I did not try it on .34.  I have a G2 160gb.  But the discard option that I was talking about isn't the script.

---

### Post by runesvend on 2010-07-09
OK, this is strange. Now *some* of the trim operations succeed, while others fail...

```
rune@runescomp:~/Programming/scripts$ sudo ./wiper-intel.sh --commit /
wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (2753024 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 2387856 sectors from 512 ranges
succeeded

/dev/sda:
trimming 1200472 sectors from 512 ranges
succeeded

/dev/sda:
trimming 10136 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 138560 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 4096 sectors from 512 ranges
succeeded

/dev/sda:
trimming 4096 sectors from 512 ranges
succeeded

/dev/sda:
trimming 24536 sectors from 512 ranges
succeeded

/dev/sda:
trimming 293480 sectors from 512 ranges
succeeded

/dev/sda:
trimming 777360 sectors from 512 ranges
succeeded

/dev/sda:
trimming 478696 sectors from 512 ranges
succeeded

/dev/sda:
trimming 186760 sectors from 357 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

```

same deal for my /home partition:

```
rune@runescomp:~/Programming/scripts$ sudo ./wiper-intel.sh --commit /home

wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda3 (ext4 mounted read-write at /home).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (57261197 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 30277630 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31358977 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 31309822 sectors from 512 ranges
succeeded

/dev/sda:
trimming 20057907 sectors from 512 ranges
succeeded

/dev/sda:
trimming 1518064 sectors from 234 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Done.

```

This is the following kernel version:

```
rune@runescomp:~/Programming/scripts$ uname -a
Linux runescomp 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```

---

### Post by runesvend on 2010-07-09
I just tried with the new 2.6.35-rc1 kernel. Now everything succeeds:

```
rune@runescomp:~/Programming/scripts$ uname -a
Linux runescomp 2.6.35-020635rc1-generic #020635rc1 SMP Tue Jun 1 18:38:58 UTC 2010 i686 GNU/Linux
rune@runescomp:~/Programming/scripts$ sudo ./wiper-intel.sh --commit /home

wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda3 (ext4 mounted read-write at /home).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (57202137 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 30015488 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31342589 sectors from 512 ranges
succeeded

/dev/sda:
trimming 31293442 sectors from 512 ranges
succeeded

/dev/sda:
trimming 20167289 sectors from 512 ranges
succeeded

/dev/sda:
trimming 1585472 sectors from 256 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.
rune@runescomp:~/Programming/scripts$ sudo ./wiper-intel.sh --commit /

wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (2524504 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 2545272 sectors from 512 ranges
succeeded

/dev/sda:
trimming 1232944 sectors from 512 ranges
succeeded

/dev/sda:
trimming 670976 sectors from 512 ranges
succeeded

/dev/sda:
trimming 329368 sectors from 512 ranges
succeeded

/dev/sda:
trimming 76264 sectors from 512 ranges
succeeded

/dev/sda:
trimming 4096 sectors from 512 ranges
succeeded

/dev/sda:
trimming 4096 sectors from 512 ranges
succeeded

/dev/sda:
trimming 176304 sectors from 512 ranges
succeeded

/dev/sda:
trimming 9688 sectors from 20 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

```

---

### Post by runesvend on 2010-07-10
I think I might have found the solution.

Setting my motherboard's SATA controller to **AHCI** mode, makes the TRIM operations work every time (on kernel 2.6.32-22). Setting my motherboard's SATA controller to **IDE** mode, makes the TRIM operations fail every time (on kernel 2.6.32-22).
As reported in the post above, using kernel 2.6.35-rc1, the TRIM operations succeed even with IDE mode turned on. I suspect the newer kernel's IDE driver might have enabled passing the TRIM command through to the device, while the older kernels don't have this feature (but that's just a guess).

Here's some output when SATA mode is set to **IDE**:
```
rune@runescomp:~/Programming/scripts$ uname -a
Linux runescomp 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
rune@runescomp:~/Programming/scripts$ dmesg | grep ahci
[    1.404683] ahci 0000:03:00.0: version 3.0
[    1.404702] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.421033] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.421036] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.421041] ahci 0000:03:00.0: setting latency timer to 64
[    1.421179] scsi6 : ahci
[    1.421261] scsi7 : ahci
rune@runescomp:~/Programming/scripts$ sudo ./wiper-intel.sh --commit /

wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (2303719 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 2447416 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 79288 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 4096 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 730736 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 4096 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 4096 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 585584 sectors from 512 ranges
FAILED: Input/output error

/dev/sda:
trimming 752128 sectors from 505 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Done.

```

And the same output when SATA mode is set to **AHCI**:
```
rune@runescomp:~/Programming/scripts$ uname -a
Linux runescomp 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
rune@runescomp:~/Programming/scripts$ dmesg | grep ahci
[    0.833818] ahci 0000:00:1f.2: version 3.0
[    0.833829] ahci 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.833864] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    0.833927] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.833929] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ccc ems 
[    0.833933] ahci 0000:00:1f.2: setting latency timer to 64
[    0.883770] scsi2 : ahci
[    0.883857] scsi3 : ahci
[    0.883934] scsi4 : ahci
[    0.884012] scsi5 : ahci
[    0.884093] scsi6 : ahci
[    0.884170] scsi7 : ahci
[    0.884387] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.899639] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.899642] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    0.899649] ahci 0000:03:00.0: setting latency timer to 64
[    0.899799] scsi8 : ahci
[    0.899876] scsi9 : ahci
rune@runescomp:~/Programming/scripts$ sudo ./wiper-intel.sh --commit /
[sudo] password for rune: 

wiper-intel.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (2302313 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 2130576 sectors from 512 ranges
succeeded

/dev/sda:
trimming 4096 sectors from 512 ranges
succeeded

/dev/sda:
trimming 249176 sectors from 512 ranges
succeeded

/dev/sda:
trimming 616536 sectors from 512 ranges
succeeded

/dev/sda:
trimming 4096 sectors from 512 ranges
succeeded

/dev/sda:
trimming 190024 sectors from 512 ranges
succeeded

/dev/sda:
trimming 790536 sectors from 512 ranges
succeeded

/dev/sda:
trimming 531728 sectors from 512 ranges
succeeded

/dev/sda:
trimming 87864 sectors from 90 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

```

Could the folks experiencing failing TRIM operations please try to enable AHCI mode for the SATA controller that their SSD is on, if possible?

***BEWARE!: If you own an Abit IP35 (Pro) motherboard (like me); turning on AHCI mode will make you unable to enter the BIOS if you own a USB keyboard, and booting from a CD/DVD won't work either. To be able to enter the BIOS again (using your USB keyboard), you are forced to clear the CMOS memory (and lose your BIOS settings). It's quick to boot though!***

---

### Post by agmlego on 2010-08-13
1. Model=OCZ VERTEX-TURBO, FwRev=1.5, SerialNo=YGNN97VE0DFFO3E287Y8
2. Linux inanna 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
3. Never works.

Notes: Partition is ext4, mounted rw on /. hdparm is currently 9.29, latest release on Sourceforge. I looked, but my Acer Aspire One does not have a BIOS option to try the AHCI trick.

---

### Post by runesvend on 2010-08-14
Hi agmlego,

Could you try wiping the partition with the script I have attached?
The attached script is the wiper script, version 2.6 with the following patch applied: [http://sourceforge.net/tracker/?func=detail&aid=3002193&group_id=136732&atid=736684](http://sourceforge.net/tracker/?func=detail&aid=3002193&group_id=136732&atid=736684)
This patch enables the user to specify the maximum number of ranges to be trimmed in a single TRIM operation. This is necessary for, at least, the Intel X25-M and OCZ Vertex2. And for these two disks, the script automatically sets the correct maximum number of ranges, which is 512 and 64 for the Intel X25-M and OCZ Vertex2, respectively. Your disk, however, is not in this list, but since it also is an OCZ disk, could you try running the attached wiper script with the *--max-ranges 64* option, to see if this fixes the issue?

In case this doesn't work, could you try running the wiper script using a newer kernel? This page tells you how to install a newer kernel: [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

---

### Post by kanenas on 2010-08-14
It seems that some motherboards still have a problem with the ahci settings.
One of those is the asrock 780g fulldisplayport.

Every wiper.sh version i tried returns i/o error
but the wiper-intel.sh seems to work

Thank you
spmurphy!!!

p.s.
Linux 2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64 GNU/Linux
and intel postville g2 80gb

---

### Post by agmlego on 2010-08-14
runesvend: No dice, still get an error.

```
$ sudo ./wiper.sh / --commit

wiper.sh: Linux SATA SSD TRIM utility, version 2.7, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (6907096 KB)..
Syncing disks..
Beginning TRIM operations..

/dev/sda:
trimming 3260415 sectors from 64 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks..
Aborted.
```

---

### Post by runesvend on 2010-08-15
> **agmlego said:**
> runesvend: No dice, still get an error.

I see. Then the only solution is probably to install a newer kernel then, and use that (at least) when trimming.

Here are instructions, if needed: [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

---

### Post by Footer on 2010-09-15
More randomness to add to this thread:

1. Model Number:  OCZ-VERTEX, Firmware Revision:  1.4
2. Linux kubuntu64 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

My motherboard was set to IDE so per runesvend's post, I set it to AHCI but the trim operation still gave me the dreaded I/O error.

I tried wiper-intel.sh as well but it still failed.  So I rebooted and set it back to IDE and guess what?  Dang thing worked:

```
footer@kubuntu64:~$ sudo /sbin/wiper.sh --commit --verbose /dev/sdc1

wiper.sh: Linux SATA SSD TRIM utility, version 2.6, by Mark Lord.
rootdev=/dev/sdc1
fsmode2: fsmode=read-write
/: fstype=ext4
freesize = 25081748 KB, reserved = 250817 KB
Preparing for online TRIM of free space on /dev/sdc1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (24830931 KB).. 
Syncing disks.. 
Beginning TRIM operations..
get_trimlist=/sbin/hdparm --fibmap WIPER_TMPFILE.3190

/dev/sdc:
trimming 49661864 sectors from 840 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

```

Not sure what's going on but it appears to be quite the random problem at this point.

Thanks!

---

### Post by agmlego on 2010-09-26
Got some more interesting output today when I tried, shortly after upgrading my kernel to latest in repos:

```

$ sudo ./wiper.sh --commit /

wiper.sh: Linux SATA SSD TRIM utility, version 2.7, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (7037190 KB)..
Syncing disks..
Beginning TRIM operations..

/dev/sda:
trimming 3145725 sectors from 64 ranges
[  825.988237] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  825.988540] ata1.00: cmd 06/01:01:00:00:00/00:00:00:00:00/40 tag 0 dma 512 out
[  825.988547]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  825.989090] ata1.00: status: { DRDY }
succeeded
trimming 3653635 sectors from 64 ranges
[  826.328571] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  826.328756] ata1.00: BMDMA stat 0x5
[  826.328872] ata1.00: cmd 06/01:01:00:00:00/00:00:00:00:00/40 tag 0 dma 512 out
[  826.328877]          res 51/10:01:00:00:00/00:00:00:00:00/40 Emask 0x81 (invalid argument)
[  826.329265] ata1.00: status: { DRDY ERR }
[  826.329376] ata1.00: error: { IDNF }
FAILED: Input/output error
Removing temporary file..
Syncing disks..
Aborted.
$ uname -a
Linux inanna 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

```

Process takes upwards of five minutes between the first "trimming ..." line and the ata exception, and the process fails out rapidly thereafter.

---

### Post by gibbylinks on 2010-11-17
Is there any update on this ? See below for my information

Model=OCZ-VERTEX2, FwRev=1.23,

2.6.36-020636-generic #201010210905 SMP Thu Oct 21 09:08:58 UTC 2010 x86_64 GNU/Linux

Fails with input/output error

---

### Post by agmlego on 2010-11-18
No update or progress so far.

---

### Post by dcstar on 2010-11-18
> **monkman said:**
> ```
monkman@pc:~/Downloads/hdparm-9.28$ sudo /sbin/wiper.sh --commit /dev/sda6

wiper.sh: Linux SATA SSD TRIM utility, version 2.6, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda6 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (5926453 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 11852912 sectors from 931 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Aborted.

```

any ideas what goes wrong here? i got the intel x25-v ssd, ubuntu 9.10 64bit, kernel 2.6.32.

thx!

Just out of interest, when I downloaded the hdparm package I had to compile a new version of it which I then copied to /usr/sbin. Then the wiper.sh command worked on my SSD.

It may be worthwhile for people to compile their own versions rather than using a pre-compiled version that may not be 100% compatible with their setup.

---

### Post by gibbylinks on 2010-11-20
> **dcstar said:**
> Just out of interest, when I downloaded the hdparm package I had to compile a new version of it which I then copied to /usr/sbin. Then the wiper.sh command worked on my SSD.

It may be worthwhile for people to compile their own versions rather than using a pre-compiled version that may not be 100% compatible with their setup.

Yes I did this today and got it working on my system.

Just a quick query, how often should you run wiper.sh ?

Thanks

---

### Post by dcstar on 2010-11-20
> **gibbylinks said:**
> Yes I did this today and got it working on my system.

Just a quick query, how often should you run wiper.sh ?


It depends on how much your SSD slows down due to running out of empty blocks when writing (it will still work, but just slower). If you have a busy system where you do lots of writes, then once a week or more frequently.

Remember that you **only** need to use wiper.sh with pre 2.6.33 kernels that do not support TRIM. A TRIM kernel with the **discard** option in the fstab file will automatically do what wiper.sh manually does. 10.10 already uses TRIM kernels, 10.04 LTS is supposed to have one backported (one day.....)

---

### Post by ariel on 2010-11-21
> **gibbylinks said:**
> Yes I did this today and got it working on my system.

Just a quick query, how often should you run wiper.sh ?

Thanks

These days you'd probably be better off running Maverick and activating TRIM


enable automatic TRIM (kernel >= 2.6.33, ubuntu >= 10.10) 

In /etc/fstab, find the line for your SSD (sdXX in the below example) and add the noatime option:

        - /dev/sdXX / ext4 discard,noatime,defaults 

Then you can easily check if TRIM is working:

        - check if automatic TRIM is actually working: [http://forums.gentoo.org/viewtopic-t-812509.html](http://forums.gentoo.org/viewtopic-t-812509.html) 


I did this on my Intel X25-M (G2) and it works just fine.

Incidentally, the attached wiper-intel.sh script appears to be working out of the box in Maverick for me (no more Input/Output errors as in Lucid). Definitely you don't need it these days though.

---

### Post by gibbylinks on 2010-11-21
Ah it would be nice if these little gems were documented somewhere.

I'm running Meerkat with 2.6.36 and "discard" option in fstab so I'm covered. :P

---


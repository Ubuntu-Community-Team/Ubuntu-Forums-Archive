---
title: "Can't create Audio CDs"
date: 2011-09-17
forum: General Help
---

### Post by BobvanderPoel on 2011-09-17
I can no longer create audio CDs on my system. I've got 2 DVD RW drives. Both from LG. One's a few years only, the other a few months. Exact same problems on both.

I've tried k3b and brassaro and command line. Same problems with all three. 

I've tried blank CDs and erasables. Same problem on all. Exactly. 

With everything being the same I'm thinking it's not hardware or the media. And, I'm sure this worked before :)

I've tried slower burn rates. Seems that even speed=4 gets a 16x burn (slowest speed of the drive?).

Current kernel is  2.6.38-11-generic-pae

These are SATA drives. So I can't use hdparm to generate info from them. Is there another program of SATA?

To make debugging somewhat easier, here's a command line session:

cdrecord dev=/dev/cdrom speed=4 -audio *wav
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH22NS50 '
Revision       : 'TN02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 2822 KB/s
Starting to write CD/DVD at speed  16.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Track 01: Total bytes read/written: 43551984/43551984 (18517 sectors).
Track 02: Total bytes read/written: 36408960/36408960 (15480 sectors).
Track 03: Total bytes read/written: 29230656/29230656 (12428 sectors).
Track 04: Total bytes read/written: 39424224/39424224 (16762 sectors).
Track 05: Total bytes read/written: 17870496/17870496 (7598 sectors).
Track 06: Total bytes read/written: 23806944/23806944 (10122 sectors).
Track 07: Total bytes read/written: 32775120/32775120 (13935 sectors).
Track 08: Total bytes read/written: 18616080/18616080 (7915 sectors).
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 D9 54 00 00 15 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 41.296s timeout 40s
write track data: error after 40452048 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.

My guess is something to do with the atapi mode or interrupts. But, I'm out of my depth here.

BTW, if someone needs some coasters ... I've got a stack of nice shiny ones here. Just pay for shipping :)

---

### Post by lensman3 on 2011-09-17
The following is from my howto:

4. Run cdparanoia copying each track into the tmp directory.
       Dumps or converts the files to .wav files as default
      # cdparanoia -B "1-"

5. Remove the source disk and put in a blank disk

6. Run cdrecord.
         speed = the speed of the drive.
         the *.wav part can be individual files.
       # cdrecord dev=/dev/cdrom -speed=12 -eject -pad -audio -v -dao -useinfo -text  *.wav

7. All done.

8a. Loading an iso image and reviewing it->

mount -t iso9660 -o ro,loop=/dev/loop0 cd_image /mnt/cdrom

(The question I have to ask just to be sure is that you are running cdrecord as root.)  I think you are because you are writing the CD but not closing the session.  I think Linux has gotten beyond ATAPI, but since you have two writers, I don't know how it differentiates them apart.  My /dev/cdrom from ls -la /dev/cdrom looks like:

lrwxrwxrwx. 1 root root 3 Sep 12 22:08 /dev/cdrom -> sr0

You might change /dev/cdrom to /dev/sr0 which would be your writer.

Steps 1 through 3 were how to ID the ATAPI device, but that doesn't work for me any more.  My step 3 is:

3. Run cdrecord to get the cd number on the scsi chain.
      Use the three numbers like 0,1,0 for TEAC CD-456S4
      for the device number.
     # cdrecord -scanbus
     # cdrecord -scanbus dev=ATAPI

---

### Post by BobvanderPoel on 2011-09-18
Sorry, I wasn't clear on this point. I'm trying to burn about 20 tracks to the CD. The burn craps out a the end of track 10 each and every time. (opps, just testing a bit more and this time is was track 8 ).

Also, the tracks will fit on the CD. Total is around 650meg. And the crap out point is around 300meg.

Even stranger (to me) is that I can play the CD I just created. Well, the first 9 tracks or so.

The tracks are on my HDD and they play fine. All are in WAV format.

> **lensman3 said:**
> 
(The question I have to ask just to be sure is that you are running cdrecord as root.)  I think you are because you are writing the CD but not closing the session.  I think Linux has gotten beyond ATAPI, but since you have two writers, I don't know how it differentiates them apart.  My /dev/cdrom from ls -la /dev/cdrom looks like:

lrwxrwxrwx. 1 root root 3 Sep 12 22:08 /dev/cdrom -> sr0


Yes, same on my system.

> 

You might change /dev/cdrom to /dev/sr0 which would be your writer.


No point to that. /dev/cdrom is just a link to /dev/sr0. And, the device is being found, etc. After all, I can blank a RW disk and it writes the first 10 tracks. So the device is being found and communicated with.

Some more info. Both drives are LGs. Here's the spec:
/dev/cdrom:

ATAPI CD-ROM, with removable media
	Model Number:       HL-DT-ST DVDRAM GH22NS50                
	Serial Number:      K00998K1011         
	Firmware Revision:  TN02    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns

And for the other drive:

/dev/cdrom1:

ATAPI CD-ROM, with removable media
	Model Number:       HL-DT-ST DVDRAM GH24NS50                
	Serial Number:      K00AB5E3326         
	Firmware Revision:  XP02    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns


Anyone with a solution? Next I'm going to try them with XP :)

---


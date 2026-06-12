---
title: "Hard Drive Scratch Noise"
date: 2011-04-01
forum: General Help
---

### Post by jtcady on 2011-04-01
I am dual booting Windows 7 and Ubuntu 10.10. When I am on Windows 7, I have no noise from the hard drive. When I use Ubuntu, every now and then I hear a short scratch noise from the hard drive. It didn't start doing it until installing Ubuntu when I was setting up the partitions. Any idea of what this is and if normal?

---

### Post by 3Miro on 2011-04-01
Desktop or Laptop. Is the noise the same as what you hear on boot? Note that on boot you have other noises like the system beep, the CD-Rom maybe, some fans are noisier on startup ... 

It could be that Ubuntu is trying to save power by turning the HDD on and off.

---

### Post by lidex on 2011-04-01
You should check your HDD just in case. Go to "Applications>System>Administration>Disk Utility"

---

### Post by jtcady on 2011-04-02
Trust me, that was the first thing I did lol. It says my disk is healthy.

And it is definitely my hard drive and not a system beep or anything.

---

### Post by jtcady on 2011-04-05
No other thoughts? I'm on a laptop and I checked everything else. The disk is healthy and still doing it. I do not remember having this problem before.

---

### Post by lidex on 2011-04-05
Does it sound like this:
[http://www.youtube.com/watch?v=n9obzgmWrlM](http://www.youtube.com/watch?v=n9obzgmWrlM)

---

### Post by jtcady on 2011-04-05
Sort of but it only lasts a quick second each time it does it and usually a few minutes in between each appearance, and mines louder.

---

### Post by jtcady on 2011-04-05
I was able to catch it on my phone. Here is the file.

[http://www.mediafire.com/?5gdq26dv2udh6zg](http://www.mediafire.com/?5gdq26dv2udh6zg)

---

### Post by smithark on 2011-04-06
even i am having the same problem. the sound usually heard while booting up or while taking back-ups. in windows 7 it warned me that my hard disk may fail any moment. but that was 7 months ago. now i am running only ubuntu. no probs upto now.
anyway i would suggest showing your hard disk to a repair guy.

---

### Post by Jouke74 on 2011-04-06
You are usually able to download a tool from the disk manufacturer to check the disk for problems. Unfortunately most of these tools run in Windows, but since you are dual-booting this should not give an issue.

Afterwards please use a check disk program like HDTune and let it scan for bad sectors (not windows check & repair) just scan. Listen to the disk while running the disk check. If it starts rattling, crackling, hicking, go slower or whatever, you might have physical damage on the disk, which is on the Ubuntu part of the disk. 

Both these tools should indicate that.

Ps. Make sure you have a backup of your important data.

---

### Post by jtcady on 2011-04-06
I am running the HDTune error scan right now so I'll let you know the results. Its gonna take awhile for 500GB lol. Then ill do a windows scan and check for a scan from manufacture. I've only had this hard drive and laptop for about a year.

---

### Post by jtcady on 2011-04-06
I ran about 3 different tests with no errors, disk is healthy. So any other ideas? And I have backed up my data just in case.

---

### Post by cokicd on 2011-04-06
Try this:

Install hdparm:** sudo apt-get install hdparm**

Then run: **sudo hdparm -I /dev/sda**

Paste the output here and I'll check it.

---

### Post by jtcady on 2011-04-06
/dev/sda:

ATA device, with non-removable media
    Model Number:       HITACHI HTS725050A9A364                 
    Serial Number:      100506PCE404VLHM8XAD
    Firmware Revision:  PC4ZC70F
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6; Revision: ATA8-AST T13 Project D1697 Revision 0b
Standards:
    Used: unknown (minor revision code 0x0028 ) 
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  976773168
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:      476940 MBytes
    device size with M = 1000*1000:      500107 MBytes (500 GB)
    cache/buffer size  = 15151 KBytes (type=DualPortCache)
    Form Factor: 2.5 inch
    Nominal Media Rotation Rate: 7200
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Vendor, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
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
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    Idle-Unload when NCQ is active
       *    NCQ priority information
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT LBA Segment Access (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    128min for SECURITY ERASE UNIT. 128min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000cca5b5d6dc04
    NAA        : 5
    IEEE OUI    : 000cca
    Unique ID    : 5b5d6dc04
Checksum: correct

---

### Post by cokicd on 2011-04-06
Looks ok to me

---

### Post by jtcady on 2011-04-06
Yea I know the drive is okay but it is quite annoying.

---

### Post by techunit on 2011-04-06
It is likely a problem caused by not defragging the windows partition before you shrunk it. The Ubuntu partition is probably out towards the outer edge of the disk and thus makes noise while accessing the disk rigorously. You might have some luck looking at your computer manufacturer website for patches.

---

### Post by jtcady on 2011-04-06
> **techunit said:**
> It is likely a problem caused by not defragging the windows partition before you shrunk it. The Ubuntu partition is probably out towards the outer edge of the disk and thus makes noise while accessing the disk rigorously. You might have some luck looking at your computer manufacturer website for patches.

You are correct, I totally forgot to do that.  I guess I can handle it for a few more days as I plan to redo my whole laptop once college classes are done with for this semester.  But this will not cause any problems for now correct?

---

### Post by Jouke74 on 2011-04-07
Everything looks ok, so I assume there will be no problems (a backup is always good to have). :)

---


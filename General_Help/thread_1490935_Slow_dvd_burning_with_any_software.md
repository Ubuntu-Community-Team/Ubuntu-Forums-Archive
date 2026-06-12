---
title: "Slow dvd burning with any software"
date: 2010-05-22
forum: General Help
---

### Post by lombar on 2010-05-22
The burner in this machine worked perfectly in windows but is a train wreck with ubuntu 10.04. I've made several coasters and am about to dump this distro entirely and hope the issue doesn't follow me.
ubuntu 10.04 x86_64



hdparm -I /dev/sr0

/dev/sr0:

ATAPI CD-ROM, with removable media
    Model Number:       PHILIPS SPD2413P                        
    Serial Number:      
    Firmware Revision:  GP03    
Standards:
    Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
    Supported: CD-ROM ATAPI-2 
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(cannot be disabled)
    DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    PACKET command feature set
       *    DEVICE_RESET command
       *    Mandatory FLUSH_CACHE
HW reset results:
    CBLID- below Vih
    Device num = 0


sudo hdparm  /dev/sr0

/dev/sr0:
 multcount     =  0 (off)
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


I succeeded in burning 1 out of 7 discs today. They start at no faster than 8x and then the speed crashes to 0.02x. I dont wait the 1 hour + for it to finish.  I really like linux and ubuntu but I need this burner to work properly. I suspect it has something to do with it not running in 32 bit transfer mode.. no idea how to fix it.  I searched this forum a few times but other than a few like problems, I found no solutions.Any help would be appreciated.

---

### Post by lombar on 2010-05-28
Problem persists with fedora 13. I need the machine to work properly so its back to windows.. 

I just don't want to spend the rest of my life trying to figure out why my dvd burner wont work consistently (or hardly at all). And the overwhelming responses have made me really see the value of the so-called community. 

Works flawlessly with windows xp and windows 7. UBUNTU 10.04 LTS has a SERIOUS ISSUE with ata/udma modes with dvd burners. Its probably some kernal stuff but hours of googling has proven fruitless and i give up. Once again, i try to switch and once again linux fails disasterously.   

Windows and Mac will continue to dominate the market unless little stuff like this gets fixed. Little stuff like MY BASIC HARDWARE FUNCTIONING.


Unhappy camper.

---

### Post by RainmanATX on 2010-08-07
Howdy all!  Just giving my 2 cents on the DVD burning slowly issue.  Been poking around the 'internets' trying to figure out the slow HDD and USB transfer problems along with the slow burning.  During this process, found an Ubuntu page on DMA activation/etc.  Used the command, 'dmesg | grep ata', and saw that my DVD drive was shown as running at 33mb/s due to a 40pin cable, but it was capable of 66mb/s.  Swapped out the 40pin cable for an 80pin, blammo, full 16x DVD burning with any software.  Heck, on auto with K3B, it burned at 22x, but with errors, was using 16x media.  Just my 2 cents aye, still looking for a fix for the HDD/USB IO performance issues.  :(

P.S. - Not sure why Windows has no performance hiccups with the 40pin cable though.  ;)

---


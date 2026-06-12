---
title: "bluray backup help..."
date: 2010-10-31
forum: General Help
---

### Post by ghat on 2010-10-31
hi all

got a new bluray burner... to backup my home videos... using maverick...

The burner is connected to my media-server which is running maverick-server
(no X) so I have to stick to command line...

I plan to use [dvdisaster]("http://dvdisaster.net/") and command line tools

A few basic questions, haunting me...

[LIST=1]
[*] how do I query the cdrw to get the details of the media inserted into the drive
[LIST]
[*]e.g. I inserted a bd-r-lth into the drive and I want to know exactly how many bytes I can burn on it
[/LIST]
 
[*] Once I have that number how do I decide/limit on the exact number of bytes I should have on final iso I am to burn
[*] dvdisaster uses 20% for ecc information, so I guess I can store only 20GB of data (ball park), again how do I limit the iso size so that it does not go over...
[*] I have huge media files (m2ts) some of which may be over 4GB, should I use a ISO filesystem or a UDF ? which is more future-proof...
[/LIST]
 
G
> ```

root@server:~# wodim --devices
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'HL-DT-ST' 'BD-RE  WH10LS30'
 1  dev='/dev/scd1'    rwrw-- : 'TSSTcorp' 'CDDVDW SH-S223F'
-------------------------------------------------------------------------

root@server:~# wodim dev=/dev/bd -atip
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'BD-RE  WH10LS30 '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)

root@server:~# wodim dev=/dev/dvd -atip
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW SH-S223F '
Revision       : 'SB00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
root@server:~# 

```
The BD has a verbatim bdr-lth and the dvd has a HP cd-r


---


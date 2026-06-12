---
title: "how to check blank cd-r size in bytes"
date: 2012-09-11
forum: General Help
---

### Post by ghat on 2012-09-11
hi

I just bought some business card CD's and wanted to check the "exact" size available on the disk. How do I do that... 

```

root@desktop:~# wodim --atip
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'CDRW/DVD GCCT20N'
Revision       : 'A108'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
ATIP info from disk:
  Indicated writing power: 6
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11595 (97:27/30)
  ATIP start of lead out: 26850 (06:00/00)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 17
Manufacturer: Pioneer Video Corporation
root@desktop:~# 

```

That information does not say exactly how many "bytes" are available on the disk.

---

### Post by ghat on 2012-09-11
anyone ?

---

### Post by AndyOpie150 on 2012-09-11
When I tried to burn a CD it gave me the exact usable space on it.
I know this is not the best answer, but until someone gives you a better one it's at least one way to find out.

---


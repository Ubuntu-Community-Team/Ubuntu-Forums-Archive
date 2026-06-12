---
title: "SMART(montools) causes disk to become read only"
date: 2010-03-24
forum: General Help
---

### Post by screamz on 2010-03-24
Hi

Can you advise on work-arounds, reporting, ..

Seems like triggering a smartmontool test makes the system go into read only mode.
EDIT: [COLOR="DimGray"] under 2.6.24-27-server on a machine here. I've booted the other kernel available 2.6.24-19-server, but can't reproduce the issue there.[/COLOR]
was able to reproduce the issue under 2.6.24-27 and 2.6.24-19

Looking especially on some help on interpreting what's going wrong

Thanks for your help


Some details:

2.6.24-27-server #1 SMP Fri Mar 12 01:23:09 UTC 2010 x86_64 GNU/Linux Ubuntu 8.04.4 LTS

>  smartctl -i /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3000HLFS-01G6U0
Serial Number:    WD-WXJ508AH0112
Firmware Version: 04.04V01
User Capacity:    300,069,052,416 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Mar 24 10:51:43 2010 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled



smartctl -t short /dev/sda



> 
Mar 24 12:00:28 XXX kernel: [ 4975.164176] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Mar 24 12:00:28 XXX kernel: [ 4975.164230] ata1.00: BMDMA stat 0x25
Mar 24 12:00:28 XXX kernel: [ 4975.164265] ata1.00: cmd 35/00:10:1e:5b:98/00:00:11:00:00/e0 tag 0 dma 8192 out
Mar 24 12:00:28 XXX kernel: [ 4975.164266]          res 51/10:10:1e:5b:98/10:00:11:00:00/e0 Emask 0x81 (invalid argument)
Mar 24 12:00:28 XXX kernel: [ 4975.164317] ata1.00: status: { DRDY ERR }
Mar 24 12:00:28 XXX kernel: [ 4975.164344] ata1.00: error: { IDNF }


---


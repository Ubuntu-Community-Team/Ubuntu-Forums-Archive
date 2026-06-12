---
title: "USB extension cable linked to data corruption"
date: 2010-02-23
forum: General Help
---

### Post by clubsoda on 2010-02-23
Just wondering if others have seen this phenomenon too. USB is supposed to tolerate cables up to 5 metres but I'm seeing write errors with a 3m cable and a particular thumb drive under both Karmic and WinXP.

Cable: E243928 AWM 2725 28AWG/1PR AND 24AWG/2C 80deg 30V CSA 228191 AWM I/II A FT2 JINLIANLI HIGH SPEED REVISION USB 2.0
Packaged by: Lemel Accessories

Flash memory: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive.
Product name: EzCool Pen Drive
Manufacturer & model: YiFang ED686.

**Test procedure:** Make a large pseudo-random file (dd if=/dev/urandom of=test bs=1000 count=34000) and copy it to the memory stick. Synchronize disks (sync) before unmounting and remounting the USB drive, then compare checksums of the original and copy files (openssl md5). If they differ, use xxd and diff to pinpoint the errors.

Typical error report:```
227521c227521
< 0378c00: abc8 ef07 ea7f fb4d ad7f aa99 c631 fa3d  .......M.....1.=
---
> 0378c00: 3200 0080 ea7f fb4d ad7f aa99 c631 fa3d  2......M.....1.=
1162081c1162081
< 11bb600: ab3f 39bf 771a 8179 0838 6f6c e1c7 c7ea  .?9.w..y.8ol....
---
> 11bb600: 3200 0080 771a 8179 0838 6f6c e1c7 c7ea  2...w..y.8ol....
1689985c1689985
< 19c9800: da3d fce2 e5c9 f45f 5614 814d 638c f47f  .=....._V..Mc...
---
> 19c9800: 3200 0080 e5c9 f45f 5614 814d 638c f47f  2......_V..Mc...
1948129c1948129
< 1db9e00: 6bd0 f389 7041 6b57 7371 ef55 75a1 17fc  k...pAkWsq.Uu...
---
> 1db9e00: b200 0080 7041 6b57 7371 ef55 75a1 17fc  ....pAkWsq.Uu...
```The erroneous 4-byte patterns "3200 0080" or "b200 0080" always show up at the start of a 256-byte block. The errors correspond to interruptions in the syncing process at write time, which can be observed when the USB drive activity LED stops blinking for a few seconds even though the file transfer is not yet complete.

The kernel is aware of those failures. Any line like the following in /var/log/syslog is probably a very bad sign!```
usb 1-4: reset high speed USB device using ehci_hcd and address 5
```The alarming aspect is that there's no indication during the file transfer that anything has gone wrong. Plenty can go wrong later though, when the broken file is retrieved from the flash memory. 
:idea: Maybe that kernel message could be made to trigger a pop-up notification. :idea:

[This discussion [XDA developers]](http://forum.xda-developers.com/showthread.php?t=454395) suggests that the principal cause may be radio frequency interference picked up by the cable, to be solved using ferrite beads. 

I'm interested to hear of any similar experiences or any alternate theories as to the cause.

---


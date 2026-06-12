---
title: "How do i add my hdd in hddtemp.db"
date: 2011-08-10
forum: General Help
---

### Post by editheraven on 2011-08-10
I want to use hddtemp with conky but for that i need to add my hdd in the database. 

I'm getting this from hdparam
```
Model=WDC WD2000JS-55NCB1, FwRev=10.02E01, SerialNo=WD-WCANR1188132
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=390721968
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7
```

And second : how do i get my netcat characters for conky config (for example in : 
Hard Drive Temp: ${execi 300 nc localhost 7634 | cut -c29-30 ;}C

---


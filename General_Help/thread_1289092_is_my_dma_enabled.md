---
title: "is my dma enabled ??"
date: 2009-10-12
forum: General Help
---

### Post by starcraftmaster on 2009-10-12
ubuntu seems to be running slowish then it used to be
hes the drive ubuntu is on:

sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=ST320410A                               , FwRev=3.19    , SerialNo=3FG2E1JZ            
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=39102336
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

---

### Post by P4man on 2009-10-12
yep, its running udma4. From your own output "* signifies the current active mode "

---

### Post by starcraftmaster on 2009-10-13
ok thanks p4man

---


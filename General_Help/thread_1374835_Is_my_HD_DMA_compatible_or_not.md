---
title: "Is my HD DMA compatible or not?"
date: 2010-01-07
forum: General Help
---

### Post by oxf on 2010-01-07
My laptop has a WD400 scorpio IDE hard disk. I'm trying to figure out if it's DMA compatible or not. Taking the cover off there's no mention of DMA on the label. I've googled and get confusing results, at least to me. Is there a way I can figure out if it's DMA or not?

Thanks

---

### Post by wkulecz on 2010-01-07
What is the drive's manufacturing date?  If its newer than 1998 its a pretty sure bet it supports DMA.

--wally.

---

### Post by oxf on 2010-01-07
> **wkulecz said:**
> What is the drive's manufacturing date?  If its newer than 1998 its a pretty sure bet it supports DMA.

--wally.

Thanks.
Manufacture date is 2005. I find mention of DMA in the google so it might be just my inexperience ! Reason I ask is that my Linux magazine mentions installing hdparm if you have a DMA compaitible HD.

---

### Post by todak on 2010-01-07
Paste this in a terminal: ```
sudo hdparm -i /dev/**sda**
``` Assuming **sda** is the drive you want to check. Look at the DMA and UDMA lines in the output of the terminal. The value with a ***** beside it is the current mode your drive is using.

---

### Post by oxf on 2010-01-07
> **todak said:**
> Paste this in a terminal: ```
sudo hdparm -i /dev/**sda**
``` Assuming **sda** is the drive you want to check. Look at the DMA and UDMA lines in the output of the terminal. The value with a ***** beside it is the current mode your drive is using.

I guess this means it is then?

>>>>
/dev/sda:

 Model=WDC WD400UE-22HCT0                      , FwRev=09.07D09, SerialNo=     WD-WXE905127915
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78140160
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

---

### Post by todak on 2010-01-07
> **oxf said:**
> I guess this means it is then?

>>>>
/dev/sda:

 Model=WDC WD400UE-22HCT0                      , FwRev=09.07D09, SerialNo=     WD-WXE905127915
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78140160
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

Yes, it is running as UDMA5.

---

### Post by oxf on 2010-01-07
> **todak said:**
> Yes, it is running as UDMA5.
 Thanks!

---


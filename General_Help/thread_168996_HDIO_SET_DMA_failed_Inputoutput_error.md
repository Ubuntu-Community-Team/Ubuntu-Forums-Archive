---
title: "HDIO_SET_DMA failed: Input/output error ?"
date: 2006-05-01
forum: General Help
---

### Post by jms830 on 2006-05-01
when I try to enable DMA on my cd-rom drive using 
"sudo hdparm -d1 /dev/hdc" or "sudo hdparm -d1 /dev/cdrom"

I get this error
```

 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Input/output error
 using_dma    =  0 (off)
```

what should I do? the output of "sudo hdparm -i /dev/hdc" is
```
 Model=SAMSUNG CD-ROM SC-148C, FwRev=B104, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

```

---


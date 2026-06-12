---
title: "UDMA Mode"
date: 2006-03-21
forum: General Help
---

### Post by ngms27 on 2006-03-21
My hda is showing this:

/dev/hda:
 using_dma    =  1 (on)

 Model=ST3160023A, FwRev=8.01, SerialNo=5JS3TCKR
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:

 * signifies the current active mode

How do I turn on udma5 and what other optimisations can I do?

Thanks

---

### Post by colo on 2006-03-21
There's no real gain in forcing UDAM5 over UDMA4, I'd just leave it as it is right now.

You may try enabling multisector transfers, your device supports 16 in parallel, and is set to 0.

```
hdparm -m16 */dev/yourdisc*
```
takes care of this.

---

### Post by dcstar on 2006-03-21
[QUOTE=colo]There's no real gain in forcing UDAM5 over UDMA4, I'd just leave it as it is right now.
......[/QUOTE]
There is a significant difference between UDMA3 (what is being used) and UDMA5, **but** I believe those items listed are what the drive is capable of, and there may be other components which do not allow it.

For instance, if you do not have the correct high-speed IDE cable or your motherboard doesn't support UDMA5 speeds, then you may not be able to get it going (even if the drive does support it).

You can always experiment with the appropriate hdparm command to try and force the faster UDMA mode, at worst you can corrupt your data or maybe just lose access to the disk and be forced to reboot.....         :(

---

### Post by Dr. Cox on 2006-05-06
i happen to have similar problems. i  know that my disk is capable of running with udma5 but whatever i tried or what was tried for me with the kind help of friends refused to work. this is an error message i get:
> [4294684.020000] ide0: Speed warnings UDMA 3/4/5 is not functional

could a bios update help? i never had that problem before, though.

that is what hdparm shows about my harddisk:

> hdparm -i /dev/hda show

/dev/hda:

 Model=TOSHIBA MK6021GAS, FwRev=GA024A, SerialNo=Y3R01207T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=46
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode


---

### Post by gtr225 on 2007-05-28
I've been having a similar issue. My cables are ATA133, my drives and motherboard support ata100, but all I get is ATA66.

---

### Post by mirak63 on 2007-12-29
I have a similar issue too, I have two drives plugged on the same cable and same ide port.

One can support UDMA 6, and is automatically set to this mode, it's an hitachi I think 80GB.
The other is a Seagate 250GB, and it supports up to UDMA5, but for whatever reason it's set to UDMA3 or UDMA4
>  Model=ST3250823A, FwRev=3.01, SerialNo=3ND059T5
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 *udma1 udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

due it's even worse, I am in UDMA 1 now :/

forcing with the command lines works but in hdparm.conf with this lines, it doesn't work as well

> command_line {
        hdparm -d1 -X udma5 -m16 /dev/hda
}

command_line {
        hdparm -d1 -S 60 -m16 /dev/hdb
}


anyway I don't know why one get the max of it's capabilities and not the other one

---


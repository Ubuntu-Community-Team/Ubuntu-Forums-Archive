---
title: "Very slow transfer rate. Takes forever to load apps."
date: 2009-09-12
forum: General Help
---

### Post by Vric on 2009-09-12
Hi,

 I have build an HTPC/NAS computer 
Pentium Dual Core 6300 (2.8Ghz) 
Asus P5N7A-VM
2Gb DDR2
1x 160gb WD 2.5" drive
4x 1Tb WD Green on Areca 1220 Raid Card.
Ubuntu Jaunty

It's been working flawless for the last 2-3 weeks, but since last week, the speed of the file transfer have droper to 1.7Mb/sec - 3Mb/sec max.

UBuntu is very slow (nearly impossible to work with) if I transfer a huge file.


IF I do benchmark test, everything looks fine:

```

vric@htpc:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  184 MB in  3.00 seconds =  61.31 MB/sec

vric@htpc:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:  764 MB in  3.01 seconds = 254.19 MB/sec


```DMA seem active:

```
vric@htpc:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD1600BEVT-75ZCT2                   , FwRev=11.01A11, SerialNo=     WD-WX*********
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```But yet, if I transfer a file from sda1 to anywhere (same hard drive, sdb1 or even network) speed is maxed at 3Mb/sec. (often 1.7Mb/sec)

If I copy a file from sdb1 (raid array) to sda1, speed is about 45Mb/sec. So **problem is only reading** on sda drive.

I tested my ram, it's fine.

I'm new to Linux/Ubuntu, I tried my best to setup everything without asking help, but I'm stuck right now.

Thanks for help!

---

### Post by NoaHall on 2009-09-12
It's not always the HD's fault. The CPU, RAM, and the motherboard/chipsets pay a important part in it too. Try loading using a older kernel and see if the problem is still there. Kernel updates change the way the core system interacts with the hardware.

---

### Post by DeMus on 2009-09-12
Why do you think you have DMA enabled? You give us information about your harddisk and the disk can handle several types of DMA. This does not mean it is enabled.
I did the same and I got this info for my disk:

Model=Hitachi HDT725050VLA380                 , FwRev=V56OA7EA, SerialNo=      VFJ401R4DLT8MK
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7372kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

The only real difference I see is:
BuffType=DualPortCache where yours is: BuffType=unknown

I copied a 2.2GB file from one to another folder on the same disk to test my speed. I started with 41MB/s and ended with 20MB/s. I saw during copying that the whole PC is slowing down. Other programs complain about not getting enough CPU power to continue.
I must say I have no idea what caused the slow file transfer, but it is something more people complain about.

Edit:
sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:  230 MB in  3.00 seconds =  76.55 MB/sec

---

### Post by Vric on 2009-09-16
> **DeMus said:**
> Why do you think you have DMA enabled? You give us information about your harddisk and the disk can handle several types of DMA.


Well: 

```
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5** *udma6**
*** signifies the current active mode**
 
```This is why I assumed that, but just to be sure:

```

dmesg | grep ata
[    0.000000]  BIOS-e820: 000000005ff90000 - 000000005ff9e000 (ACPI data)
[    0.000000]  modified: 000000005ff90000 - 000000005ff9e000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.004000] Memory: 1535068k/1572416k available (4115k kernel code, 36040k reserved, 2199k data, 532k init, 667208k highmem)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.444366] libata version 3.00 loaded.
[    1.350899] ata1: SATA max UDMA/133 abar m8192@0xfad76000 port 0xfad76100 irq 2301
[    1.350901] ata2: SATA max UDMA/133 abar m8192@0xfad76000 port 0xfad76180 irq 2301
[    1.350903] ata3: SATA max UDMA/133 abar m8192@0xfad76000 port 0xfad76200 irq 2301
[    1.350904] ata4: SATA max UDMA/133 abar m8192@0xfad76000 port 0xfad76280 irq 2301
[    1.350906] ata5: SATA max UDMA/133 abar m8192@0xfad76000 port 0xfad76300 irq 2301
[    1.350908] ata6: SATA max UDMA/133 abar m8192@0xfad76000 port 0xfad76380 irq 2301
[    1.832015] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.874739] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.874742] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
**[    1.876046] ata1.00: configured for UDMA/133**
[    2.764014] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.764878] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223B, SB01, max UDMA/100, ATAPI AN
[    2.765855] ata2.00: configured for UDMA/100
[    3.084010] ata3: SATA link down (SStatus 0 SControl 300)
[    3.404010] ata4: SATA link down (SStatus 0 SControl 300)
[    3.724010] ata5: SATA link down (SStatus 0 SControl 300)
[    4.044010] ata6: SATA link down (SStatus 0 SControl 300)
[    4.246711] Write protecting the kernel read-only data: 1528k
[    4.733244] EXT3-fs: mounted filesystem with ordered data mode.
[   15.178870] EXT3-fs: mounted filesystem with ordered data mode.

```My linux knowledge is limited, but looks like DMA is enabled.

I didn't had time to work on this computer since, but I will try with a live cd and see if I still have this problem.. If not, I will reinstall everything I guess.

I have searched a lot and I have found people with the same problem, but no solution was given.

Strangest thing is, it was fine before and my Kernel wasn't updated since the first installation:

```
uname -a
6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GN

```Thanks for your help

---


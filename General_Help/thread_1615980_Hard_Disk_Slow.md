---
title: "Hard Disk Slow"
date: 2010-11-07
forum: General Help
---

### Post by SavageWolf on 2010-11-07
I have a Acer Aspire 8935 Laptop with 4GB RAM and a Quad Core processor, the problem appears to be that the hard disk is slow, the system will occasionally slow down, and most of my CPUs will be at "I/O Wait". I am using a 64bit 10.10.

```
# hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   3224 MB in  2.00 seconds = 1613.21 MB/sec
 Timing buffered disk reads:  218 MB in  3.01 seconds =  72.34 MB/sec
```

```
# hdparm /dev/sda
/dev/sda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0
```


```
# hdparm -i /dev/sda
/dev/sda:

 Model=TOSHIBA MK5055GSX, FwRev=FG001J, SerialNo=494HT0YJT
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode
```

Though the hard disk may not actually be slow, and that I'm just expecting everything to be amazing... Hmm...

---

### Post by SavageWolf on 2010-11-09
Anyone? Help?

---

### Post by SavageWolf on 2010-11-12
So... Alone...

---

### Post by dagamer on 2010-11-12
Check to see if your hard disk is one of the newer western digital drives that have a different sector size. I read on newegg before that Linux has a hard time reading the new format that only western digital uses. it may be possible to format the drive into a different sector size or something similar?

---

### Post by SavageWolf on 2010-11-13
The disk is a "TOSHIBA MK5055GS" apparently, but I have no idea whether that is one of them, and if so what to do...

---

### Post by SavageWolf on 2010-11-20
Anyone? (Again)

---

### Post by dcstar on 2010-11-20
> **SavageWolf said:**
> Anyone? (Again)

Use the Disk Manager to do a full SMART test on the drive, and look for bad blocks in the SMART data.

---

### Post by dtfinch on 2010-11-20
72.34 MB/sec looks very normal, as does the rest of the hdparm output. It's not one of those 4kb sector advanced format drives, so alignment wouldn't be a problem.

What's usually happening when it gets slow? Copying lots of files? Installing updates?

If Firefox is slowing down or pausing a lot when there's disk io in the background, you could try going to about:config and adding a new integer "toolkit.storage.synchronous" with a value of 0, which causes it to stop calling fsync() whenever it writes to disk, like history and such.

---

### Post by SavageWolf on 2010-11-22
The slowdowns are usually random, the system randomly stops and sends the LA into the tens (The CPU monitor says it's because of "I/O Wait")... Also, it seems to be slow at executing programs, Thunderbird takes a long time to start up the first time, and the boot is MUCH longer than my old system, which had worse specs... I ran a smart self-test thing, and it says everything is OK...

---

### Post by SavageWolf on 2010-11-23
It also seems to be slow when accessing swap, the LA went up to 20!

---

### Post by SavageWolf on 2010-11-27
Hmm...

---

### Post by SavageWolf on 2010-11-27
I've been looking up my hard disk, those stats seem to be "normal", anyone have any idea where the random slowdowns are coming from?

---


---
title: "mdadm RAID 0 is slow..."
date: 2010-05-26
forum: General Help
---

### Post by ownaginatious on 2010-05-26
So I made an array of two 1.5 TB drives and originally they were quite fast... but now they feel slow. Copying a 700 MB file takes almost an entire minute.

The RAID only contains ~700 GB at the moment.

Any ideas as to why it's slowing down?

Thanks!

---

### Post by sylvester_0 on 2010-05-26
What's the output of:```
cat /proc/mdstat
```? Also, try running a simple benchmark: ```
hdparm -Tt /dev/mdX
```

P.S. I hope you know that RAID 0 is striping; if one of those drives dies you'll lose all of your data.

---

### Post by ownaginatious on 2010-05-27
Hi, thanks for responding.

The output to cat /proc/mdstat is:

```

Personalities : [raid0]
md1 : active raid0 sda[0] sdb[1]
      2930276992 blocks 64k chunks

md0 : active raid0 sdd[0] sdc[1]
      2930276992 blocks 64k chunks

unused devices: <none>

```

There are actually two RAIDs; one backs up the other at weekly intervals. The one in question is md0.

So don't worry; I've got drive failure covered to a degree ;).

Here are the results of hdparm:

```
 /dev/md0:
 Timing cached reads:   2018 MB in  2.00 seconds = 1009.75 MB/sec
 Timing buffered disk reads:  332 MB in  3.01 seconds = 110.45 MB/sec
```

EDIT:

I started playing with the hdparm command, and found some more information that may be useful to solving my problem. Both the drives in the RAID are identical:

```

 Model=ST31500341AS, FwRev=CC1H, SerialNo=9VS33RHM
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=2930277168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

```

---

### Post by ownaginatious on 2010-05-28
...bump?

---

### Post by ownaginatious on 2010-06-03
...bump again?

---


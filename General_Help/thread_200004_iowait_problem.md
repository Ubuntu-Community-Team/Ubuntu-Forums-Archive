---
title: "iowait problem"
date: 2006-06-19
forum: General Help
---

### Post by SeTAr on 2006-06-19
Sometimes I get A LOT of iowait for no apparent reason, but only today I managed to make it repeatable.
If I doubleclick on [this file]("http://www.studenti.pef.upr.si/~tinem/test1.svg") in nautilus i get:
```
tinem@abak:~$ vmstat -a 2 10
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free  inact active   si   so    bi    bo   in    cs us sy id wa
 4  0 105272  11868 114384 871348   25  515   869   552  530   863 11  3 76 10
 0  3 141736  10392 247200 738600    0 18286 11090 18386  661   806  6 16  0 78
 0  5 174456  10740 334492 651012  122 16666  3606 16826  674   590  2  7  0 90
 1  8 200480  10092 383192 603364  168 13016  3180 13162  611   516  4  4  0 92
 1  6 217208  10832 410940 575328  228 8370  1754  8370  579   518  1  3  0 95
 0  8 260368  10224 437972 547568  188 21582  1756 21582  653   534  4  9  0 86
 0  7 295660  10084 447476 539360   38 17662  1694 17662  632   670  4  8  0 89
 1 10 318576  11496 466768 517572  248 11458  1684 11458  600   439  2  3  0 95
 1  3 343816  10376 475172 511800  266 12700   954 12736  628   736  4  6  0 90
 0  5 397020  10028 493384 493812   48 26856    48 26900  660   598  5  8  0 88

```

```
tinem@abak:~$ iostat 1
Linux 2.6.15-25-386 (abak)      19/06/06

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
hdd             202.00       520.00     43720.00        520      43720

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.92    0.00    5.88   90.20    0.00    0.00

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
hdd             127.45      2000.00     19600.00       2040      19992

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           9.09    0.00    9.09   81.82    0.00    0.00

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
hdd             206.06      2052.53     35886.87       2032      35528

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.96    0.00    8.91   87.13    0.00    0.00

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
hdd             219.80      1948.51     34764.36       1968      35112
```

this might be interesting (from ps aux):
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root       147  0.0  0.0      0     0 ?        D    21:33   0:00 [pdflush]
root       148  0.1  0.0      0     0 ?        D    21:33   0:02 [kswapd0]
root      1953  0.0  0.0      0     0 ?        D<   21:33   0:00 [reiserfs/0]
...
tinem     5877  8.9 84.2 2329776 872508 ?      Sl   22:00   0:03 eog file:///home/tinem/Dokumenti/xpres/test1.svg
root      5906  0.0  0.0      0     0 ?        D    22:00   0:00 [pdflush]
...

```

system becomes VERY unresponsive until i kill eog...

And DMA seems to be working ok:
```

root@abak:/home/tinem# hdparm /dev/hdd

/dev/hdd:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 160086528, start = 0
root@abak:/home/tinem# hdparm -tT /dev/hdd

/dev/hdd:
 Timing cached reads:   2000 MB in  2.00 seconds = 999.94 MB/sec
 Timing buffered disk reads:  168 MB in  3.00 seconds =  56.00 MB/sec
root@abak:/home/tinem#
```

I have a 80GB Maxtor on ABIT NF7-S (nForce2) using reiserfs

Any idea whats going on?

I found a couple of other threads ([here]("http://www.ubuntuforums.org/showthread.php?t=170710") and [here]("http://www.ubuntuforums.org/showthread.php?t=180093")) on this forum about what seems to be the same problem but without solution...

LPT

---

### Post by danbert on 2007-05-15
I have a similar problem, and it seems that no one is willing to respond.  There is no reason my computer should lag this much.  I get almost the same I/O performance running from a LiveCD.  This was not a problem under 6.10.

---


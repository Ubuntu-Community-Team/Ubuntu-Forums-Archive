---
title: "external SATA transfer speeds"
date: 2010-03-26
forum: General Help
---

### Post by jmalone767 on 2010-03-26
I've read a couple of post very similar to this issue but I can't seem to find one unique to my problem. I just bought a 1Tb hdd and reformatted to FAT32 it is connected via eSATA to SATA cable.

At first I transfered music that initially was getting speeds over 100mb/s (according to nautilus) after about a minute it started to dwindle. Now most files will range somewhere between 8-20mb/s although I've only seen a couple go beyond. 

I edited hdparm.conf to enable DMA

Here is the output of hdparm -Tt for both internal(sda) and external(sdb) hardrives.

```

/dev/sda:
 Timing cached reads:   14872 MB in  2.00 seconds = 7444.68 MB/sec
 Timing buffered disk reads:  372 MB in  3.00 seconds = 123.91 MB/sec
john@john-desktop:~$ sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   14728 MB in  2.00 seconds = 7372.19 MB/sec
 Timing buffered disk reads:  318 MB in  3.00 seconds = 105.98 MB/sec

```

What is the issue this output leads me to believe that I should be getting the same speed I once got.

I'm running Intel Core 2 duo at 3.00, ASUS P5Q (enabled AHCI) and 4gb ram 12gb linux swap. Also Karmic 9.10

Any pointers on what to try next?

---

### Post by rnerwein on 2010-03-26
hi
the fastes IO is no IO. the performance goes down when your cache is filled up. have a look at "top"
at buffer and cache. you can see this behavior too if you use: time dd if=/dev/zero of=bla bs=4k count=10000. this is very very fast. but then type: time sync  ( then the data is going to the disk ).
ciao

---


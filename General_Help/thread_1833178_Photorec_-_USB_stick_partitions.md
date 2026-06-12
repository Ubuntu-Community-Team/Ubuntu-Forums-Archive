---
title: "Photorec - USB stick partitions"
date: 2011-08-25
forum: General Help
---

### Post by cryptotheslow on 2011-08-25
Hi,

Just messing around with a 2GB USB stick to see what is and isn't possible with file recovery - just an academic exercise not an actual recovery crisis :)

It had about 1GB of stuff on it which I deleted, then used sfill to do one pass of zeros.

So fire up Photorec and on getting to the partition selection stage I get this:

```

PhotoRec 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdc - 2002 MB / 1910 MiB (RO) -  USB DISK 2.0

     Partition                  Start        End    Size in sectors
     No partition             0   0  1  1017  37 38    3911680 [Whole disk]
 2 * NetWare 3.11+        43883  52 47 547533  14 42 1936028240
 1 * Sys=72               202428  43 11 499387  30 51 1141509631
 3 * Sys=79               486441  36 30 990090  59 39 1936028192
 4 * Sys=0D               750697  30 25 750711  57 33      55499
```There is just one FAT32 partition occupying the whole drive according to GParted....  so :confused::confused:

What on earth is a NetWare 3.11+ partition when it's at home (just means Novell to me!)? Let alone the 3 Sys partitions?

Any clues what Photorec is doing to come up with list?

Cheers

---

### Post by yiannis66 on 2011-08-28
Give the next in terminal
```
sudo photorec /log

```
then folow the output ,you will find out what it is eazily

---


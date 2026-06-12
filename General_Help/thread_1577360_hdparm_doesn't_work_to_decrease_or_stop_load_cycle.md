---
title: "hdparm doesn't work to decrease or stop load cycles of notebook HD"
date: 2010-09-18
forum: General Help
---

### Post by dbednarski on 2010-09-18
Hi,

Firstly, sorry for my English, I'm Brazilian and don't write very well.  But, Ubuntu is destroying my HD! Recently I had missed one disk, and  perceived now that the load/unload cycles occurs about 140 times in 10  minutes, and in few months I will loose other HD! That bug (or not bug  (?)) is noticed in 
[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695).

The command that exhibited me the cycles:

$ sudo smartctl -A /dev/sda | grep Load_Cycle_Count
 225 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       25308
 
 after 10 minutes:
 
$ sudo smartctl -A /dev/sda | grep Load_Cycle_Count
 225 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       25450
 

I tried to resolve it with "sudo hdparm -B 255 /dev/sda", but hdparm looks not work! The counts still remain high...

How can I stop the cycles? Or, decrease to a value that wouldn't be dangerous...
My HD is SATA, and I don't know if hdparm works for this HD type.

Thanks!

---


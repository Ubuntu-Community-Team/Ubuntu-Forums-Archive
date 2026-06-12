---
title: "Karmic - Please assist me to troubleshoot VERY slow RAID-5 array"
date: 2011-01-07
forum: General Help
---

### Post by jeremydt on 2011-01-07
Hi All,

I read this thread of someone else experiencing terrible RAID5 performance:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1643094](http://ohioloco.ubuntuforums.org/showthread.php?t=1643094)

Mine is also terrible but didn't want to hijack the other thread.

Does anyone have any suggestions on what I can do to troubleshoot the issue further?

[LIST]
[*]Software Raid (MDADM)
[*]Performance is terrible locally, not just over the network. Can often > 60seconds to create a folder or to list files in a directory.
[*] 3GB RAM, E6300CPU
[*] 9.10 Karmic
[*] Low CPU utilisation during slow performance
[*] Low Memory utilisation during slow performance
[/LIST]


Disks that make up the RAID5 array:

```

root@server:~# hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   2172 MB in  2.00 seconds = 1086.12 MB/sec
 Timing buffered disk reads:  266 MB in  3.02 seconds =  88.10 MB/sec
root@server:~# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1724 MB in  2.00 seconds = 861.43 MB/sec
 Timing buffered disk reads:   20 MB in  4.02 seconds =   4.98 MB/sec
root@server:~# hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   2536 MB in  2.00 seconds = 1268.59 MB/sec
 Timing buffered disk reads:  280 MB in  3.02 seconds =  92.72 MB/sec
root@server:~# hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   1344 MB in  2.00 seconds = 671.60 MB/sec
 Timing buffered disk reads:   20 MB in  4.21 seconds =   4.76 MB/sec
root@server:~# hdparm -tT /dev/sde

/dev/sde:
 Timing cached reads:   2198 MB in  2.00 seconds = 1099.45 MB/sec
 Timing buffered disk reads:  300 MB in  3.01 seconds =  99.60 MB/sec
root@server:~# hdparm -tT /dev/sdf

/dev/sdf:
 Timing cached reads:   2532 MB in  2.00 seconds = 1266.33 MB/sec
 Timing buffered disk reads:  290 MB in  3.02 seconds =  96.18 MB/sec
root@server:~# hdparm -tT /dev/sdg

```

Stand-alone Disks (system and one other)
```

root@server:~# hdparm -tT /dev/sdg
/dev/sdg:
 Timing cached reads:   2210 MB in  2.00 seconds = 1104.42 MB/sec
 Timing buffered disk reads:  262 MB in  3.01 seconds =  86.91 MB/sec
root@server:~# hdparm -tT /dev/sdh

/dev/sdh:
 Timing cached reads:   2514 MB in  2.00 seconds = 1256.91 MB/sec
 Timing buffered disk reads:  194 MB in  3.00 seconds =  64.64 MB/sec
root@server:~# hdparm -tT /dev/md0
```

The Actual MDADM array
```
/dev/md0:
 Timing cached reads:   2518 MB in  2.00 seconds = 1259.05 MB/sec
 Timing buffered disk reads:   14 MB in  3.84 seconds =   3.64 MB/sec
```

---

### Post by Joshua on 2011-01-26
I compared your results to what I've been getting.  As I noted in [the other thread]("http://ubuntuforums.org/showthread.php?p=10399475#post10399475"), I still haven't made any progress, but it looks to me like your problem could originate from /dev/sdb and /dev/sdd.  Those two disks look REALLY slow.

Are they IDE or SATA?

How are they connected to the system?  PCI slot or directly to the main board?

---


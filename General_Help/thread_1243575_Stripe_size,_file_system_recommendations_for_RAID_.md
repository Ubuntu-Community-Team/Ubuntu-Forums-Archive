---
title: "Stripe size, file system recommendations for RAID 6?"
date: 2009-08-18
forum: General Help
---

### Post by tuckie on 2009-08-18
I have 7 new 1TB hitachi's on their way to be used in a RAID 6, and I want to make sure that I use an optimal configuration.  

I'm currently using 10, 500GB drives in a RAID 6 with a 256K stripe on an Adaptec 51645.
The file system is xfs, configured as shown below:
```
tuckie@nibbler:~$ sudo xfs_info /dev/sdd1
meta-data=/dev/sdd1              isize=256    agcount=4, agsize=243736673 blks
         =                       sectsz=512   attr=2
data     =                       bsize=4096   blocks=974946691, imaxpct=5
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal               bsize=4096   blocks=32768, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=0
realtime =none                   extsz=4096   blocks=0, rtextents=0

```

hdparm -tT currently returns:
```

Timing cached reads:   880 MB in  2.00 seconds = 439.81 MB/sec
 Timing buffered disk reads:   90 MB in  3.02 seconds =  29.80 MB/sec

```

Which is less than stellar. There are some tips [here]("http://linux.adaptec.com/?p=22#comment-156"), but it sounds like it would require a battery unit installed (which I don't have, although I do use a standard UPS on the server).  Note: this may be due to having too large of an array causing a slowdown, as well as using various versions of WD RE2s.

I'm going to be storing primarily DVD backups (to be played over the network via xbmc) and backups of files and documents from other computers on the network. Finally, the questions:  What stripe size would your recommend for the array? Any (linux) file system preferences for large partitions with large files?  What settings (block size, mount options, etc) would be best for that partition?

---


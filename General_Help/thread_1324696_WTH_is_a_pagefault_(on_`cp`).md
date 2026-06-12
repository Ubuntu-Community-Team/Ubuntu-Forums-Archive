---
title: "WTH is a pagefault? (on `cp`)"
date: 2009-11-12
forum: General Help
---

### Post by zackiv31 on 2009-11-12
I'm copying a couple hundred gigs from a nas to a local raid 5... what are these pagefaults (are they copying errors?)

```

me@me:/media/nas/backup$ sudo time cp -r * /media/backup/
4.73user 1193.09system 4:32:54elapsed 7%CPU (0avgtext+0avgdata 0maxresident)k
761556832inputs+760320560outputs (0major+419minor)pagefaults 0swaps

```

---


---
title: "my partition scheme... any input? opinions?"
date: 2006-03-14
forum: General Help
---

### Post by stevemcqueen on 2006-03-14
so here's my new partitioning scheme...

```

/       5 GB            
swap    2 GB                    
/usr    5 GB                    
/var    5 GB, (with a symlink from /var/tmp to /tmp)                  
/tmp    2 GB, noexec,nosuid
/home   all remaining space                    

```

anyone have any thoughts on this particular way of doing things? i read around various forums and wikis and this was the best i could come up with for my needs.. i'm not sure though if i'm being to generous or not generous enough with some of these partitions..

---

### Post by Koybe on 2006-03-14
A partition scheme depends on the usage, there is no good/bad way to partition your drive.

Anyway it looks good.

---

### Post by yanik on 2006-03-14
your swap is a little overkill.   What's wrong with the default partitioning scheme?

---

### Post by KnottyMan on 2006-03-14
I do this personally:

/ 15G
15G blank partition 
1.5G swap
rest as a data partition.


The second blank partition is for another version of Ubuntu so I can just do a clean install there, but be able to roll back if needed.

All Ubuntu in one partition though.  No real need to split up the filesystem like that.  Just makes is possible to fill up a critical part and have problems later.

---


---
title: "Fibre Channel issue"
date: 2011-02-07
forum: General Help
---

### Post by mbates14 on 2011-02-07
Here is my setup:

Dell poweredge 2600 series server
QLA2200 copper fiber channel card
Clariion DAE 10-disk SCSI fiber channel system with DB9 LCC

I have the ubuntu live 10.01 CD..

Disk utility sees all 10 HDDs but it cannot report the capacity and if you try to partition or format it will not. it errors out. 

any ideas?

---

### Post by mbates14 on 2011-02-08
I figured it out. turns out i was hit with the "clariion syndrome"

proprietary drives, proprietary firmware, proprietary formatting. only to ensure that clariion only works with clariion. 

Anyway, i did manage to fix it all up and got the disks working in a JBOD software RAID5 :-)

---

### Post by tredegar on 2011-02-08
> Anyway, i did manage to fix it all up and got the disks working in a JBOD software RAID5
Pleased you managed to solve this, but it would be *really* helpful to others if you posted what you did to fix your problem, with all the gory details.

I am *guessing* that you first posted here because the search engines reported ""

Other people may be searching for a solution to your problem and reached this thread by search-engine keywords. If you have managed to solve it then please let them know what it was that helped you, even if it was "simple".

Thanks and best wishes.

---


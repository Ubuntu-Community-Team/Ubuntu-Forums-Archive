---
title: "the swap onto a dynamic partition!"
date: 2010-09-09
forum: General Help
---

### Post by mamioop on 2010-09-09
Hi Milky Way  experts & experimenters :p!

I just want ask if I can put the swap linux into a dynamic partitions?
Coz, I wanna create a new basic partition in addition to other 4 basic partitions, as u know we are not able to create more than 4 basic partitions, any new partition should be dynamic and that mean that we can't install new OSes in.

Best Regards!
;)

---

### Post by oldfred on 2010-09-09
Dylnamic is a windows only proprietary partition scheme. Windows says once you convert to dynamic you cannot convert back.

Win dynamic disk
[http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)

The MBR/msdos partitions have 4 primary partitions or one of the primary can become an extended partition and hold essentially an unlimited number of logical partitions, some systems allow 16 others even more, space becomes a bigger issue.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---


---
title: "Raid0"
date: 2006-03-16
forum: General Help
---

### Post by jwe on 2006-03-16
Hi,

Am I right by saying that I cannot raid0 my current server without loosing all my data? ie. I have to format the new raid after I creat it?

---

### Post by tyspot on 2006-03-16
Depends JWE,
are you going into a hardware Raid0 or software striping Raid0? 

Hardware = yes, stripe before load or use provided hardware boot disk, application or such to set source and the target for stripe across. This usually requires having at least 45% disk space free. I prefer to make an image of the data sets (complete backup) then format and setup the Raid0 array. Then make the partition sets and dump the data sets to their respective locales. 

Software = no, it will arange the data across the space and manage access allocations at the Process level. this is not as fast as a good ol Hardware chip controller Raid0 but does increase speed over normal partiton access at standard interface control.

I would not recommend using a Software solution as it is frought with dependencies and should you ever lose the ability to boot into your OS your data will be pooched unless you have either an exact duplicate to load the drives partitons into or have a shadowed copy set active (Mirror of Raid0, aka Raid0+1-3 drives). On the cost perspective I have always found it cheaper whether in SCSI, IDE, SATA or SATAII to go with Hardware raid controllers. You will lose a lot less time and functionality which is what you are after when you talk RAIDing.

Hope the reply hits the Spot.

---


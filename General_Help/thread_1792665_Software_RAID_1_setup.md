---
title: "Software RAID 1 setup"
date: 2011-06-28
forum: General Help
---

### Post by txducker on 2011-06-28
Problem: I want to have offsite copies of my /home and media backups. I do not want to use web based solutions (time, money, control). The plan is to back up my data to 1 TB drive and then mirror that drive using RAID 1. The mirror drive could be then stored offsite and brought back weekly for updating. I have a KINGWIN KF-1000-BK 3.5" Internal hot swap rack for removing/inserting my mirror drive.

Questions:

1. What formating of the drives are required before setting up the RAID. I did: format drive - guid; format volume - ext4; format partition - Linux raid partition.
I want to know if using guid will cause problems for RAID 1 (its newer with more features).

I then used the command > mdam to create the RAID. The RAID is syncing the drives which takes a long time so I don't know if this is going to work.

Thanks in advance for you suggestions.

---

### Post by txducker on 2011-06-28
No one has replied, but I will post in case anyone else has similar questions in the future.

Syncing finished and so far everything seems to be working.

---


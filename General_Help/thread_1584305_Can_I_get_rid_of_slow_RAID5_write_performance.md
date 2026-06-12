---
title: "Can I get rid of slow RAID5 write performance?"
date: 2010-09-29
forum: General Help
---

### Post by tarekeldeeb on 2010-09-29
Hello all,

I have a NFS v4 server with 3 disks in a RAID 5 using mdadm. I suffer from slow write performance especially with many small files (similar to DBs access).

I now know that slow writes are due to excess read-calculate-update parity cycles for each write request.
Can I disable the parity? 
or in other words, can I drop down to RAID 0/1 ?

Please advise me

Thanks, 
Tarek

---


---
title: "Looking for guidance on Raid/Nas setup"
date: 2011-08-02
forum: General Help
---

### Post by Randy Flagg on 2011-08-02
Hey all,
   I have a situation where I need to setup some sort of storage solution with Raid 5 redundancy.  I was thinking that Linux would be the way to go but I am not certain what platform would be best.

      I was thinking running two SATA RAID controllers to get me somewhere between 4 - 6 TBs in Raid 5.  I am very comfortable with ubuntu now and would love to use it.  I have also used FreeNas in the past but would love to have a full OS on the machine if at all possible.

Please let me know if you have any suggestions.

---

### Post by tgalati4 on 2011-08-02
RAID5 can suffer failure during the long rebuild required when using large (2TB disks).  Depending on your needs, using JBOD (Just a Bunch of Disks) and a script to mirror the drives every so often may be better.

---

### Post by Randy Flagg on 2011-08-03
> **tgalati4 said:**
> RAID5 can suffer failure during the long rebuild required when using large (2TB disks).  Depending on your needs, using JBOD (Just a Bunch of Disks) and a script to mirror the drives every so often may be better.

I think that may be why we are looking at RAID 6.

---


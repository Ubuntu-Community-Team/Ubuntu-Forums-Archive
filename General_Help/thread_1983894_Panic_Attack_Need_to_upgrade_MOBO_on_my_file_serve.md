---
title: "Panic Attack: Need to upgrade MOBO on my file server"
date: 2012-05-20
forum: General Help
---

### Post by GuiGuy on 2012-05-20
I have a ubuntu (10.4) based file & media server. It boots from an IDE 320G HDD and then there's this soft RAID5 4 X 2G setup...

The existing aging mobo is creating a couple of problems so it's best to upgrade. 

But I am worried about the RAID5. It is backed up but I know from bitter experience that if the upgrade fails the backup files will be a dud, no matter how much validation I did.

In any case, I'd like to avoid rebuilding the RAID5 from scratch. Last time I did it it took a week. 

The question is, if I replace the MOBO and plug the drives into the new MOBO as they were on the old, can I reasonably expect the system to boot up and mount the array?

Or is there something else I need to do?

TIA; I appreciate any meaningful advice...

---

### Post by dcstar on 2012-05-21
> **GuiGuy said:**
> I have a ubuntu (10.4) based file & media server. It boots from an IDE 320G HDD and then there's this soft RAID5 4 X 2G setup...

The existing aging mobo is creating a couple of problems so it's best to upgrade. 

But I am worried about the RAID5. It is backed up but I know from bitter experience that if the upgrade fails the backup files will be a dud, no matter how much validation I did.

In any case, I'd like to avoid rebuilding the RAID5 from scratch. Last time I did it it took a week. 

The question is, if I replace the MOBO and plug the drives into the new MOBO as they were on the old, can I reasonably expect the system to boot up and mount the array?

Or is there something else I need to do?

TIA; I appreciate any meaningful advice...

If it is a Linux LVM array then it should work, if it uses "Fake Raid" motherboard resources then probably not.

---

### Post by GuiGuy on 2012-05-21
> **dcstar said:**
> If it is a Linux LVM array then it should work, if it uses "Fake Raid" motherboard resources then probably not.

Sorry, should have mentioned I'm using mdadm for  software RAID management.

---


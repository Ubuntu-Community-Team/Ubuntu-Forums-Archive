---
title: "Expand Partition to the Left &quot;Quickly?&quot;"
date: 2010-10-17
forum: General Help
---

### Post by pc_michael on 2010-10-17
I would like to expand my root partition to the left.  I already moved my 100MB /boot partition overand that took like 12 hours with Gparted, so no way do I want to use it for my 60GB partition to gain another 2GB.  Is there a faster way?  (Besides wiping the partition, creating the new larger one and reinstalling Ubuntu? :P)

I've heard LVM might be good, but it sounds like I have to do that from scratch as well, and I'd rather not lose all my stuff and start over, I just want to clean up my messy partitioning. :)

Thanks!

---

### Post by srs5694 on 2010-10-18
I'm surprised that it took 12 hours to move 100MB of data. That sounds like a serious bug (or at least a flaw) in GParted's partition-moving code.

How much free space do you have? If it's enough to hold all the data on your 60 GB partition, you could create a new partition there, copy the data in some other way (tar or perhaps even dd), reconfigure the system to boot from the new partition, reboot to test it, delete the old partition, and then resize the new one to the right to fill the available space. A similar approach would work to convert to LVM.

---


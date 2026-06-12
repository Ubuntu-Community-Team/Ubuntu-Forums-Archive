---
title: "Wubi install, upgrade to 10.10?"
date: 2010-11-06
forum: General Help
---

### Post by dakukuu on 2010-11-06
I installed through Wubi and in update manager 10.10 has appeared, i have two questions

1) Will this install in the Wubi directory? (c://ubuntu) or do i have to partition it first? If i do, please tell me a link how because the one i followed on the wiki said it didn't support 10.04 wubi. I would prefer to upgrade the Wubi install though :)
2) Will upgrading remove any of my user files? I installed themes i want to keep, and i wouldn't want to loose them.


Thank you :D

---

### Post by bcbc on 2010-11-06
> **dakukuu said:**
> I installed through Wubi and in update manager 10.10 has appeared, i have two questions

1) Will this install in the Wubi directory? (c://ubuntu) or do i have to partition it first? If i do, please tell me a link how because the one i followed on the wiki said it didn't support 10.04 wubi. I would prefer to upgrade the Wubi install though :)
2) Will upgrading remove any of my user files? I installed themes i want to keep, and i wouldn't want to loose them.


Thank you :D
I don't think there's a major benefit to upgrading to 10.10 from 10.04.1. So you might want to consider your reasons for upgrading.

Second, although there is a workaround to the wubi upgrade problem, I don't think it's a permanent fix - so you are taking a risk.

Regarding the upgrade, it just updates the virtual disk (c:\ubuntu\disks\root.disk), it won't remove any of your files. You won't see any change in the c:\ubuntu directory.

If you want to migrate to a partition, then this howto supports the latest version of ubuntu: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---


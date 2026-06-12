---
title: "Removing Jaunty in a dual boot in XP"
date: 2010-02-02
forum: General Help
---

### Post by chrioni on 2010-02-02
How do I remove Ubuntu (Jaunty 9.10) from a dual boot setup, using XP?
 
Much appreciate some assistance.

---

### Post by amsterdamharu on 2010-02-02
Boot up from xp cd and choose repair, this will repair the bootsector and overwrite mbr. The menu you are seeing is from grub, the bootloader for ubuntu.

In xp choose run -> mmc -> file -> add remove snap in -> disk manager (not sure about the exact menu's but you'll figure it out).

In the disk manager you can reclaim the space used by ubuntu if it was on it's own partition.

---

### Post by chrioni on 2010-02-03
Thanks I'll try that out...cheers!

---

### Post by howefield on 2010-02-04
> **amsterdamharu said:**
> Boot up from xp cd and choose repair, this will repair the bootsector and overwrite mbr. The menu you are seeing is from grub, the bootloader for ubuntu.

In xp choose run -> mmc -> file -> add remove snap in -> disk manager (not sure about the exact menu's but you'll figure it out).

In the disk manager you can reclaim the space used by ubuntu if it was on it's own partition.

Hopefully it is a "real" dual boot, and not a Wubi install.

---


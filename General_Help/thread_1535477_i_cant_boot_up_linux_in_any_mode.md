---
title: "i cant boot up linux in any mode"
date: 2010-07-20
forum: General Help
---

### Post by korok2 on 2010-07-20
this string of commands pops up when i try to boot up linux in any mode.
 
fsck from util-linux-ng 2.16
/dev/sda5: clean, 207703/1966080 files, 1500210/7859793 blocks (check in 2 mounts)
 
i have no idea about computer stuff so if anyone who answers can keep it simple that would be good. thanks.
 
 
Quote:
I belive in karma. Therefore I can do horrible things to people all day long and believe they diserve it.

---

### Post by alphacrucis2 on 2010-07-20
> **korok2 said:**
> this string of commands pops up when i try to boot up linux in any mode.
 
fsck from util-linux-ng 2.16
/dev/sda5: clean, 207703/1966080 files, 1500210/7859793 blocks (check in 2 mounts)
 
i have no idea about computer stuff so if anyone who answers can keep it simple that would be good. thanks.
 
 
Quote:
I belive in karma. Therefore I can do horrible things to people all day long and believe they diserve it.

fsck is the file system check. Similar to chkdsk in Windows. With Ubuntu, it gets run automatically every so many boots. You should let it run to completion and the boot up should then proceed normally. If the boot isn't completing then maybe fsck has found something wrong that it can't fix. Can you give more detail.

---


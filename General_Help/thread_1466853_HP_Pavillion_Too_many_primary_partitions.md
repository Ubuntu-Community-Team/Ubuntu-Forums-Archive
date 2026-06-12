---
title: "HP Pavillion: Too many primary partitions"
date: 2010-04-30
forum: General Help
---

### Post by kapok on 2010-04-30
I just got an Hp Pavillion laptop, and I'm trying to install Ubuntu. I resized the Windows 7 partition, and tried to install, but was unable because you can have no more than 4 primary partitions. Is there any way around this?

The current partitions are:
Windows 7 ntfs file system
BOOT
RECOVERY
HP_TOOLS

---

### Post by aceracer24 on 2010-04-30
> **kapok said:**
> I just got an Hp Pavillion laptop, and I'm trying to install Ubuntu. I resized the Windows 7 partition, and tried to install, but was unable because you can have no more than 4 primary partitions. Is there any way around this?

The current partitions are:
Windows 7 ntfs file system
BOOT
RECOVERY
HP_TOOLS


You can only have 4 primary partitions but I don't believe there is a limit on logical partitions. So just keep one as a primary and make the rest logical. Or some configuration of that.

---


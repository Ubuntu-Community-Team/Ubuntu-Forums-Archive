---
title: "grub not detecting my paritions correctly"
date: 2010-07-18
forum: General Help
---

### Post by dallnsn on 2010-07-18
Hi all, 

I'm having a problem with multibooting. 

I've been running ubuntu 9.10 until this week without any problems. I've just done an in-place update to 10.04 and now cannot boot my windows XP partition.

looking at grub.cfg it appears to be referring to sdb1 as the XP partition whereas the disk utility says the correct partition is sdb5. 

sdb1 is a data partition formatted ntfs but not bootable.

When I choose XP from the grub menu all I get is a black screen with a flashing cursor at the top, which would suggest it is trying to boot the data partition.

Is there an easy way to fix this? I've tried update-grub and also startupmanager and it makes no difference. I would just try to edit grub.cfg but the next update would presumably wipe out my changes.

Thanks for looking.

---

### Post by dallnsn on 2010-07-21
Ok, solved it myself, eventually.

Removed the disk with ubuntu on it. Did repair install of windows. replaced disk with ubuntu on. Working.

I spent hours trying to get grub to work properly - I assumed it was a linux problem as it was a linux update that broke it.

---


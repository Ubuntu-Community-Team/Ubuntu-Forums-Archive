---
title: "Uninstalling"
date: 2010-11-29
forum: General Help
---

### Post by wenfuli on 2010-11-29
For our own reasons, I installed Ubuntu on my wife's XP laptop so we had XP and Ubuntu (Lucid) running on dual-boot. My wife would now like to remove Ubuntu from her laptop (sorry, can't convince her to give up Windows). What is the best -- and easiest and quickest -- way to wipe all traces of Linux (i.e., Ubuntu and Grub) from her machine?

---

### Post by TeoBigusGeekus on 2010-11-29
To wipe out ubuntu, just use the disk management tool of winxp (System Management>Disk Management).
To wipe out grub, boot up with a windows cd, press R for repair and give
```
fixmbr
```
at the command prompt.

---

### Post by wenfuli on 2010-11-29
Thanks for the help. Sounds good, except for two problems.
1) My wife's version of Windows is in Chinese. I can hopefully use my netbook (which also has Ubuntu and WinXP on dual-boot) to figure that part out.
2) We don't have a Windows CD!

Is there any other way to get rid of Grub?

---


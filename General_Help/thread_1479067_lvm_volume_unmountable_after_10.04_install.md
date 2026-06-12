---
title: "lvm volume unmountable after 10.04 install"
date: 2010-05-10
forum: General Help
---

### Post by tkgamble on 2010-05-10
After upgrading to 10.04 I can't remount my LVM logical volumes.  System-config-lvm  shows them but doesn't recognize any filesystem present on the logical volume (was ext4) and mount responds that /dev/vg00/lv00 doesn't exist (can I recreate them without destroying them?).  When installing 10.04 I ignored these volumes, so ubuntu shouldn't have messed with them.

Is there any way to mount them short of reconfiguring and restoring from backup?

---


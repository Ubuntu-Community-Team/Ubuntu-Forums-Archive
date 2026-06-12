---
title: "Mistakenly extended LVM Volume Group"
date: 2012-06-11
forum: General Help
---

### Post by treymok on 2012-06-11
Ok here is my predicament. I had a 2TB hard drive that had a 1.8TB ext4 partition at the beginning of the drive (/dev/sda2) and I had a LVM volume group inside an extended partition on the rest of the drive (/dev/sda5). I made the mistake of vgextend VolGroup /dev/sda5 and have lost access to my 1.8TB partition. I have done nothing else with this PC (not even rebooted). Is there anyway to undo the extension and recover my data or to fully integrate that partition into the volume group?

---

### Post by treymok on 2012-06-11
Ok here is my predicament. I had a 2TB hard drive that had a 1.8TB ext4 partition at the beginning of the drive (/dev/sda2) and I had a LVM volume group inside an extended partition on the rest of the drive (/dev/sda5). I made the mistake of vgextend VolGroup /dev/sda5 and have lost access to my 1.8TB partition. I have done nothing else with this PC (not even rebooted). Is there anyway to undo the extension and recover my data or to fully integrate that partition into the volume group?

Edit: Moderator Note - Threads Merged. Please do not create multiple threads.

---


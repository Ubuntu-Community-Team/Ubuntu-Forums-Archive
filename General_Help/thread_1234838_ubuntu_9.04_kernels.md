---
title: "ubuntu 9.04 kernels"
date: 2009-08-08
forum: General Help
---

### Post by tudor_victor on 2009-08-08
there are two kernels available as options during the boot of 9.04

what is the difference between them?

---

### Post by michy99 on 2009-08-08
Kernals are periodically updated to fix bugs or add features. Ubuntu leaves the previous kernal so you can boot to it if for some reason the new one does not work.

---

### Post by lswb on 2009-08-08
When updates are installed they sometimes include a newer kernel version that corrects bugs or security problems. Older kernel versions are not removed by the update process. Rarely, a kernel update will cause problems, if this happens, you can select the older version and boot with that. It is usually recommended to keep at least one older version available in the grub boot menu. They don't take up much disk space, if you want to remove them you can use synaptic to search for the older version. Include the numbers like "2.6.28-11" in the search, then mark them for removal or purging.

---


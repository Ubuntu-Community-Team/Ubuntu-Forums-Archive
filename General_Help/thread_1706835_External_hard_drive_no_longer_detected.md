---
title: "External hard drive no longer detected"
date: 2011-03-14
forum: General Help
---

### Post by neon401 on 2011-03-14
Hi,

I have a problem with my external hard drive. I've always used to connect it to my Ubuntu Server with the following command:** sudo mount -t ntfs-3g /dev/sdc1 /mnt/woody**
...and it's worked fine, but after a reboot I did a couple of times ago, the hard drive no longer appears.
**sudo fdisk -l** doesn't show the hard drive anymore. Connecting it to a Windows computer works, I even tried the "safely remove harddrive" function, but to no avail.

Thank you.

---

### Post by vanadium on 2011-03-14
That it does not show up in "sudo fdisk -l" may suggest a hardware issue. Check other USB ports, other cables, etc.

---

### Post by neon401 on 2011-03-14
> **vanadium said:**
> That it does not show up in "sudo fdisk -l" may suggest a hardware issue. Check other USB ports, other cables, etc.
The problem was the cable, thank you very much!

---


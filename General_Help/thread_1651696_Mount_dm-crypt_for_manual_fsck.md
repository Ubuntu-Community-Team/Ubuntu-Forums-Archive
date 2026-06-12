---
title: "Mount dm-crypt for manual fsck"
date: 2010-12-23
forum: General Help
---

### Post by Phoenix_Swelter on 2010-12-23
My laptop suffered a dirty shutdown, and when I tried a reboot, the drive needs a fsck exam. The disk is fully encrypted with dm-crypt. I have hooked it up to my desktop computer as an external drive, and I need to mount the container (decrypt it), but I don't want to mount the partition itself so that I can run fsck on it. How can I do that?


edit://
Additional info

Device       Boot       ID            System
/dev/sdb1    *          83            Linux
/dev/sdb2                  5            Extended
/dev/sdb5                83            Linux

I am able to "cryptsetup luksOpen /dev/sdb5 olddisk" and get "key slot 0 unlocked". But I don't know what to do with it then. I have two "partitions" inside the container (root & swap), how do I address the proper one?


Ray

---


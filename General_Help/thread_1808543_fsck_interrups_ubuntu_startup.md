---
title: "fsck interrups ubuntu startup"
date: 2011-07-20
forum: General Help
---

### Post by SeaKing on 2011-07-20
I have a problem booting up ubuntu on my embedded system. (see output in attachment)

It's an ALIX 2D2 borad and the main thing is it does not have a CMOS battery! To fix the problem I've used this command: "sudo tune2fs -i 0 <device> " to kill time based checks on the bootdrive which are the reasons for this interruption, I guess. Is there another possibility to kill/block these checks or to disable the service?

---

### Post by dcstar on 2011-07-21
> **SeaKing said:**
> I have a problem booting up ubuntu on my embedded system. (see output in attachment)

It's an ALIX 2D2 borad and the main thing is it does not have a CMOS battery! To fix the problem I've used this command: "sudo tune2fs -i 0 <device> " to kill time based checks on the bootdrive which are the reasons for this interruption, I guess. Is there another possibility to kill/block these checks or to disable the service?

Edit /etc/fstab and set the boot check flag for the root partition to 0.

---

### Post by SeaKing on 2011-07-23
That's it! (It's the <pass> option)

---


---
title: "Failed to mount filesystem"
date: 2010-07-25
forum: General Help
---

### Post by FinalShot on 2010-07-25
I'm trying to boot into Ubuntu 9.10, but after the logo comes out, I get "Failed to mount filesystem".

This is the second time this has happened to me, last time I had to reinstall Ubuntu.

---

### Post by CharlesA on 2010-07-25
What is the exact error message?

You could try running fsck from a livecd and see if it spits out any errors.

---

### Post by FinalShot on 2010-07-26
No error message, just "Failed to mount file system".

And fsck appears to be fine, it returns "/dev/sda1: 197573/12304384 files (0.2% non-contiguous), 11099544/49195038 blocks".

---

### Post by CharlesA on 2010-07-26
Hrm. Have you made any changes to fstab recently?

---

### Post by FinalShot on 2010-07-26
Nope, I just booted into windows for like 5minutes, then back into Ubuntu. Then this happened.

---

### Post by CharlesA on 2010-07-26
Strange. Are you able to boot Ubuntu into recovery mode?

Hold down shift and select "recovery mode" from the menu.

---

### Post by lokimon on 2010-07-29
> **CharlesA said:**
> Strange. Are you able to boot Ubuntu into recovery mode?

Hold down shift and select "recovery mode" from the menu.

having the same issue.

can't boot from any of the previous kernels or in recovery mode, if i boot to recovery shell the filesystem is mounted read only so i can't edit fstab, if i boot from a live CD and fsck the drive, it passes clean.

managed to mount the drive and edit fstab as in this post:

[http://ubuntuforums.org/showthread.php?p=8156875](http://ubuntuforums.org/showthread.php?p=8156875) but that didn't help.

not sure what else to try.

---


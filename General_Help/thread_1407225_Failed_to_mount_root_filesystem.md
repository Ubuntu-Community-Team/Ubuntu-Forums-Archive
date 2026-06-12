---
title: "Failed to mount root filesystem"
date: 2010-02-15
forum: General Help
---

### Post by NRaghavendra on 2010-02-15
I have a dual booting newly installed 64 bit Ubuntu 9.10 on my machine. It was all fine until today. Now when I boot into Ubuntu, I see the error Failed to mount root filesystem. I cant remember any significant changes during the last session. One thing I remember is I upgraded the system using the update manager which asked me to choose an option for grub boot loader. I opted for its upgradation. After the upgrade, I was able to work with Ubuntu for a few more sessions. Windows XP works very fine.

I checked other threads which suggested running fsck, but it did not help. fsck does not report any errors.

I am new to Ubuntu and does not know much about its configurations. Can some one suggest me how to go about nailing down and fix this problem? Can it be a Boot loader issue?

---

### Post by ironclaw on 2010-02-16
Boot into an Ubuntu live CD and see if you can mount your Ubuntu root file system.

Also, paste here the output of
```
sudo fdisk -l
```
to see your partitions.

---


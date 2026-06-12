---
title: "Is it worth formatting my /home as ext3 for dual boot HDD space sharing?"
date: 2010-07-23
forum: General Help
---

### Post by Starks on 2010-07-23
I've give up hope on ever seeing an extent-enabled ext4 filesystem driver for Windows.

---

### Post by oldfred on 2010-07-23
If you want to shared data with windows, just create a shared NTFS partition.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

When I first installed Ubuntu I created a separate NTFS /shared partition for firefox, thunderbird & photos so I had all the same data in both. I now have most of my data in a /data partition for all the data I only need in Ubuntu.

---

### Post by Starks on 2010-07-23
I'll look into that. Wouldn't ext3 be faster though? I really don't care enough to share Firefox data anyway.

---

### Post by clhsharky on 2010-07-23
I use ext3 on all my data partitions with good transfer speed and usable with Windows or Linux.

Sharky

---


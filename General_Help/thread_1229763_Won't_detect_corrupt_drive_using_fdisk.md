---
title: "Won't detect corrupt drive using fdisk"
date: 2009-08-02
forum: General Help
---

### Post by Koobi on 2009-08-02
Hi,
I'm usually happy experimenting and finding things out but this one is taking a very long time.

I think I have the data corruption on the 2.6.28-11 kernel issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

Once my main drive became inoperable, I installed Jaunty on a spare hard disk and as soon as I installed it, I downgraded the kernel using this as a guide:
[http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29)
no problems so far.


But I need to recover the data from my corrupted hard disk. It's all ext4 based.

When I attach it as a secondary SATA drive (sdb) and boot from my working drive and attempt to go into rescue mode via grub, it takes forever because the system spits out the errors on the corrupted drive.
After about an hour of spitting out errors, I finally get to a root shell in the hopes that I can fsck.
Thereafter, typing "sudo fdisk -l" does not show the corrupted disk even though I get errors like "Buffer I/O error for sdb....."

Any idea how I can at least fsck the corrupt drive?


Thanks.

---

### Post by baliganikhil on 2009-08-06
I think there is a program called TestDisk which should solve this problem. Not sure, just have a look at it.

---


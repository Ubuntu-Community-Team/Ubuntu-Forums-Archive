---
title: "Ubuntu 10.10 cannot find a device, grub rescue"
date: 2010-10-10
forum: General Help
---

### Post by kingtengu on 2010-10-10
I have just installed Ubuntu 10.10 but can't boot into it. I have two hard drives, one with Windows and the other has Ubuntu.

From live CD I tried:

```
sudo update-grub
```

Which displayed the following message:

> /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

This is what my system looks like:

```
sudo fdisk -l
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       20023   160731136    7  HPFS/NTFS

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18663   149903360   83  Linux
/dev/sdb2           18663       19458     6384641    5  Extended
/dev/sdb5           18663       19458     6384640   82  Linux swap / Solaris

I tried using SuperGrub without success. Any help is much appreciated.

Thanks.

---

### Post by Quackers on 2010-10-10
By doing that you are just running sudo update-grub on the live cd. That won't do anything. You need to chroot into your live system then try it.
Here is a link that explains how to chroot in to your live system. When you are in you can then run sudo update-grub. Watch and see what it picks up as it's generating grub.cfg. If it doesn't pick up your OSes try re-installing grub (the info is given in the same thread).
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---


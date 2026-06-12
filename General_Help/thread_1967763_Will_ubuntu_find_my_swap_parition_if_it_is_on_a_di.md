---
title: "Will ubuntu find my swap parition if it is on a different drive?"
date: 2012-04-28
forum: General Help
---

### Post by joham34 on 2012-04-28
Hello everybody. 
I just purchased an SSD and will put my linux partition on it. So far it was on another hard disk, dual boot which of course had a small swap partition. 
I have been told to avoid creating a swap partition on the ssd, to prolong its life. 
Now, I wonder, if I install only the linux partition without creating the swap on it, will grub find the partition on the old drive and use it? Will I have to mount every time the old hard disc? Should I make some manual changes in the grub file? 
My RAM is 4 GB and I will install 12.04.
Thank you in advance

---

### Post by pqwoerituytrueiwoq on 2012-04-28
it will find it during install (just did this yesterday)
even if it did not you could add it into fstab afterwords
will edit with a copy of my fstab in a minute there are things yuo should do other than swap for max ssd life
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8c51d334-d6a0-4eee-8fd5-118e0dc6a8d5 /               ext4    errors=remount-ro,noatime,discard 0       1
# /home was on /dev/sdb6 during installation
UUID=f157f3c4-e9fd-40aa-a1d4-0aa249333db7 /home           ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=60478ac5-d53b-4cba-86d4-14dd1d65dc2d /var            ext4    defaults        0       2
# /mnt/Windows was on /dev/sdb7 during installation
UUID=8d16ecdf-deae-4f68-ac1c-65352f2ae3e1 /mnt/Windows    ext4    defaults        0       2
# /tmp was made a ram disk after installation
tmpfs                                     /tmp            tmpfs  defaults,noatime,mode=1777 0       0
# swap was on /dev/sdb5 during installation
UUID=fc2a810f-a518-404d-b273-cf64cd1926c6 none            swap    sw              0       0
# move /root to /home/root to reduce wear on ssd
/home/root                                /root           bind   defaults,bind    0       0
```/dev/sda is my ssd
/dev/sdb7 is a dedicated partition for a windows xp virtualbox if you are wondering why it's uuid is so long
if you don't have the ram to put /tmp on the ram you may want to put it on your hdd
notice the noatime and discard on /dev/sda1 those are for SSDs

---


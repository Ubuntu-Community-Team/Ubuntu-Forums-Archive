---
title: "GPT Nvidia RAID array in 10.10"
date: 2010-11-04
forum: General Help
---

### Post by Fingal on 2010-11-04
Howdy,

I just installed Ubuntu 10.10 64bit and wanted to get access to my nvidia RAID array.

This array is working, and is NTFS formatted.

But wasn't showing up through normal means in Ubuntu.
(for example the NTFS Configuration Tool didn't display it)

Here's what the system showed.

```
root@hermes:~# ls -l /dev/mapper/
total 0
crw------- 1 root root 10, 59 2010-11-03 22:39 control
lrwxrwxrwx 1 root root      7 2010-11-03 22:42 nvidia_dadijiag -> ../dm-0

```

```
dmraid -ay
/dev/sdc: "pdc" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: "pdc" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_dadijiag" already active

```


```
root@hermes:~# mount -t ntfs /dev/mapper/nvidia_dadijiag /mnt              
NTFS signature is missing.
Failed to mount '/dev/dm-0': Invalid argument
The device '/dev/dm-0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

After messing around for a few hours I finally got lucky and found the following thread:
[http://www.linuxquestions.org/questions/linux-hardware-18/mounting-an-ntfs-raid-0-stripe-in-ubuntu-9-04-64-bit-769017/page2.html](http://www.linuxquestions.org/questions/linux-hardware-18/mounting-an-ntfs-raid-0-stripe-in-ubuntu-9-04-64-bit-769017/page2.html)

I followed the instructions there installed kpartx and ran it, and now i do have access to my disk.

However, I have 2 concerns.

First, that link points to an old bug report for redhat and seems like it was fixed back in 2009. So i wanted to make sure that it wasn't in fact fixed by some other means in ubuntu (i.e., did I do the right thing)

Second, I now have 3 devices:
```
root@hermes:~# ls -l /dev/mapper/
total 0
crw------- 1 root root 10, 59 2010-11-03 22:39 control
lrwxrwxrwx 1 root root      7 2010-11-03 22:47 nvidia_dadijiag -> ../dm-0
lrwxrwxrwx 1 root root      7 2010-11-03 22:51 nvidia_dadijiag1 -> ../dm-1
lrwxrwxrwx 1 root root      7 2010-11-03 22:51 nvidia_dadijiag2 -> ../dm-2
```

I mounted nvidia_dadijiag2

Is my mirror still in effect, or did i just mount one of the specific drives from the mirror?

Thanks

---

### Post by Fingal on 2010-11-04
Also - how do i persist this between reboots?

---


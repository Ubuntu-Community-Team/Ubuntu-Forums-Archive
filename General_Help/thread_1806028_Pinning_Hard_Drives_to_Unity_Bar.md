---
title: "Pinning Hard Drives to Unity Bar?"
date: 2011-07-17
forum: General Help
---

### Post by iRide113 on 2011-07-17
I have 3 hard drives on my computer now, and a total of 6 partitions. My question is can I put a shortcut to one of them on the Unity Bar?

Like the same icon you see when you mount a hard drive and it pops up in the bar.

Any ideas?

---

### Post by wildmanne39 on 2011-07-17
> **iRide113 said:**
> I have 3 hard drives on my computer now, and a total of 6 partitions. My question is can I put a shortcut to one of them on the Unity Bar?

Like the same icon you see when you mount a hard drive and it pops up in the bar.

Any ideas?Hi, I am not sure about doing it that way, but every time you mount the drive it will show up in the launcher, you could make the drive auto mount and it would be there every time you start your system, but I am not the person to tell you how to add it to fstab and create an automount.

---

### Post by iRide113 on 2011-07-17
> **wildmanne39 said:**
> Hi, I am not sure about doing it that way, but every time you mount the drive it will show up in the launcher, you could make the drive auto mount and it would be there every time you start your system, but I am not the person to tell you how to add it to fstab and create an automount.

Yeah but the risks outweigh the advantages with auto mounting. I've heard even a bad shutdown could corrupt your drives... :?

---

### Post by wildmanne39 on 2011-07-17
> **iRide113 said:**
> Yeah but the risks outweigh the advantages with auto mounting. I've heard even a bad shutdown could corrupt your drives... :?Hi, thats true but there are ways to shut down a unresponsive system here is a link on it.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by garvinrick4 on 2011-07-17
> **iRide113 said:**
> I have 3 hard drives on my computer now, and a total of 6 partitions. My question is can I put a shortcut to one of them on the Unity Bar?

Like the same icon you see when you mount a hard drive and it pops up in the bar.

Any ideas? Here is a link below and a bit of an explanation:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Use fstab to mount what ever you want using the UUID's, if they are present at boot they
will mount to desktop. Below is a copy of a fstab. with mounted install /, a ext4 partition and
a ntfs partition mounted at  /media/home and /media/data

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0

---


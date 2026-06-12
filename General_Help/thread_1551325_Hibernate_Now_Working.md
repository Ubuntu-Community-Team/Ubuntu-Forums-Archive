---
title: "Hibernate Now Working"
date: 2010-08-12
forum: General Help
---

### Post by abdusamed on 2010-08-12
My hibernate is not working because it says "Swap error".Initially I did not install swap during installation but installed it later through this method here

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

After searching through threads, I found this but I think the method is a bit old and I don't know if it's safe to use to use it on Lucid. I should tell you have really bad experience with playing with partitioning. I'm just trying to be on the safe side.

Anyway this is the thread I mentioned

[http://ubuntuforums.org/showthread.php?t=273118](http://ubuntuforums.org/showthread.php?t=273118)

This is what my fstab look like 

```

 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=bbfb75ae-bd13-4c89-a300-48d5375a6dcb /               ext4    errors=remount-ro 0       1
/mnt/2048Mb.swap  none  swap  sw  0 0

```

---

### Post by abdusamed on 2010-08-14
i really need to get this working..I reboot my machine often..

---


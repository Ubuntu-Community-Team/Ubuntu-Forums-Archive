---
title: "Current Users mounts USB Device as Read Only, how to fix?"
date: 2010-12-18
forum: General Help
---

### Post by 0949er on 2010-12-18
Hello, how are you doing? As the title suggest, I am trying to add/delete files from my HTC Evo through ubuntu via enabling file sharing on the device. Ubuntu detects the drive, and mounts it up so that I can browse/read files off the device. However, I am not able to do any writing to the device because it is mounted as "read-only". The only wierd thing is that it worked last week, and I have not changed any settings on my system. Any ideas? Where should I start? Is the auto-mount for USB drives located in "/etc/fstab"? because here is the contents of that file, and I dont see anything for usb mounts:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=12b6f667-b8a7-4ad0-a7ea-fe1a5c1570fa /               ext4    errors=remoun$
# swap was on /dev/sdb5 during installation
UUID=cd8813a0-8368-4471-bb9a-e8e302cb2890 none            swap    sw           $
# user allows me to use the drive, exec gives me execution privilages.
/dev/sr0 /media/dvd-rom auto ro,user,exec,noauto,unhide,uid=1000,gid=1000 0 0

```

---

### Post by 0949er on 2010-12-18
anybody?

---


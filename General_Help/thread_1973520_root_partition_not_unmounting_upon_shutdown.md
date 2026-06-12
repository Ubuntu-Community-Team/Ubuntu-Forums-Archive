---
title: "root partition not unmounting upon shutdown"
date: 2012-05-04
forum: General Help
---

### Post by mahmoodkamal on 2012-05-04
[SIZE=2]I upgraded from 11.10 to precise. No problem except that the root partition (sda3) is not unmounting cleanly when i shutdown. hence upon the next usage it always starts checking the disk drive for errors. Here is my fstab:

[COLOR=Blue]proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=2183f8c1-e07f-4181-ae57-61d025a160e1 /             ext2    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation
UUID=53b6f0c1-bebe-4b69-8bb9-06f637f34f5e none          swap    sw              0       0

UUID=b56aa35d-e87e-492f-96ab-75cdcd879a28 /home     ext4 nodev,nosuid 0 2[/COLOR][/SIZE]

:confused:

---

### Post by 2ta8gdfte on 2012-05-05
> **mahmoodkamal said:**
> [SIZE=2]I upgraded from 11.10 to precise. No problem except that the root partition (sda3) is not unmounting cleanly when i shutdown. hence upon the next usage it always starts checking the disk drive for errors. Here is my fstab:

[COLOR=Blue]proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=2183f8c1-e07f-4181-ae57-61d025a160e1 /             ext2    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation
UUID=53b6f0c1-bebe-4b69-8bb9-06f637f34f5e none          swap    sw              0       0

UUID=b56aa35d-e87e-492f-96ab-75cdcd879a28 /home     ext4 nodev,nosuid 0 2[/COLOR][/SIZE]

:confused:

Have you run this command to see the UUID and checked it to be correct in the fstab. 
 
```
sudo blkid
```Here is my fstab if you need a reference, I don't have a separate home though.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=600c00ea-0106-4ea1-a03a-c41bec8e39b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6f2e78d5-fc58-43f5-8253-08b743adaa57 none            swap    sw              0       0
```

---

### Post by mahmoodkamal on 2012-05-05
i do not think UUID was wrong, otherwise root would not have mounted ?

my problem is UNmounting. root is probably not unmounting cleanly. Hence very fast shutdown, and everrytime fsck starts checking sda3 (root partition)

---

### Post by hypeiv on 2012-05-08
I had the same problem... and my searches lead me to this thread:

[http://ubuntuforums.org/showthread.php?t=1964854](http://ubuntuforums.org/showthread.php?t=1964854)

I added the /sbin/killall5 command to my /etc/init.d/umountroot like Terry suggested in the second post and all is well now

---

### Post by mahmoodkamal on 2012-05-13
> **hypeiv said:**
> I had the same problem... and my searches lead me to this thread:

[http://ubuntuforums.org/showthread.php?t=1964854](http://ubuntuforums.org/showthread.php?t=1964854)

I added the /sbin/killall5 command to my /etc/init.d/umountroot like Terry suggested in the second post and all is well now

I added [SIZE=3]killall5 - 15[/SIZE] in [SIZE=3]/etc/init.d/umountroot[/SIZE] as suggested.

however, the problem is still there. :confused:

Just updated and one of the updates solved the problem :)

---


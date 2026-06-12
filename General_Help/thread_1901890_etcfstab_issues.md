---
title: "etc/fstab issues"
date: 2011-12-29
forum: General Help
---

### Post by chazdg24 on 2011-12-29
I previously had this issue last week: [http://ubuntuforums.org/showthread.php?p=11561705#post11561705]("http://ubuntuforums.org/showthread.php?p=11561705#post11561705")

The problem has resurfaced.  I notice I now have a etc/fstab and an etc/fstab001.  When I boot up I got the message:

disk drive for /media/sdc 1 is not ready yet or not present.
Continue to wait; press S to skip mounting; or M for manual recovery

I removed it from etc/fstab and rebooted to only get:

disk drive for /media/sdg 1 is not ready yet or not present.
Continue to wait; press S to skip mounting; or M for manual recovery

I went and took it out when I noticed a second fstab.  I have no idea what is going on.  Any help on how to fix this issue would be greatly appreciated!  By the way, which fstab is running the show?

---

### Post by chazdg24 on 2011-12-29
Here is fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=67e7a8a3-fc6d-408e-be09-9cfbcdb48219  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=851df827-eb3e-43bf-bd46-3468670f6dd5  none         swap  sw                   0  0  
/dev/sdh1                                  /media/sdh1  ntfs  defaults             0  0  
/dev/sdg1                                  /media/sdg1  ntfs  defaults             0  0  


Here is fstab001:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=67e7a8a3-fc6d-408e-be09-9cfbcdb48219  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=851df827-eb3e-43bf-bd46-3468670f6dd5  none         swap  sw                   0  0  
/dev/sdh1                                  /media/sdh1  ntfs  defaults             0  0  
/dev/sdg1                                  /media/sdg1  ntfs  defaults             0  0

---

### Post by chazdg24 on 2011-12-30
Bump...

Anybody know how to deal with this issue?  Thanks

---


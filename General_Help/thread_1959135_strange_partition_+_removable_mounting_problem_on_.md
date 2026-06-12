---
title: "strange partition + removable mounting problem on Lucid"
date: 2012-04-15
forum: General Help
---

### Post by e0ne199 on 2012-04-15
hello everyone, 
i have a mounting problem after upgrading my ubuntu 9.10 become 10.04.4....on my ubuntu 10.04.4,  i can't mount my partitions and my removable devices from nautilus because their icons are not displayed on either "Places" or side pane / computer window..but surprisingly i can mount all of them if i plug my removable devices in first before booting or before logging in .... and if i do that, some strange things occur when i open gparted, all of devices (partition+removable) displayed suddenly disappear...and i have to reboot my computer again with removable disk plugged in to show them up again...

btw i have never get this problem when i was still using 9.10....before that, thx for helping me solve this annoying problem :)

as a reference, here my /etc/fstab and /etc/mtab are :  

fstab :
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda6 during installation
UUID=e7a06c0c-4bc5-416d-86bf-be95b39f1954 / ext3 errors=remount-ro 0 1
# swap was on /dev/sda7 during installation
UUID=9427f937-4048-417a-b9eb-28b367607523 none swap sw 0 0

mtab :
/dev/sda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/usb0 vfat rw,noexec,nodev,sync,noatime,nodiratime 0 0
gvfs-fuse-daemon /home/hyperstation/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=hyperstation 0 0
/dev/sda1 /media/FC284A54284A0DD8 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda7 /media/6368746f-2074-616b-6f65-207575696400 ext3 rw,nosuid,nodev,uhelper=udisks 0 0
/dev/sda8 /media/DATA_ fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

*oh yeah i get this /etc/mtab when i boot my ubuntu with removable device plugged in, so i can mount them all :)*

---


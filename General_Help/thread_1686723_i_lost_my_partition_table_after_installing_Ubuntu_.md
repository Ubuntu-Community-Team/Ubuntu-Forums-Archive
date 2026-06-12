---
title: "i lost my partition table after installing Ubuntu 10.10"
date: 2011-02-12
forum: General Help
---

### Post by hadim on 2011-02-12
I am a computer novice, need help pleas.
I had windows XP , then i install Ubuntu 10.10, during installation i damaged my partition and lost partition table.
when i boot, i can only get Ubuntu and when i ask for windows i get the following messages :

 "the disk contains an unclean file system(0,1)."
 "The file system wasn't safely closed on windows Fixing"

 and then it takes me back to Ubuntu.

 Some info:

hadi@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hadi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hadi)
/dev/sdb1 on /media/D437-EB6F type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

hadi@ubuntu:~$ sudo blkid
[sudo] password for hadi: 
/dev/loop0: UUID="23ff5ce5-8d94-4d4b-a693-0e0cdfd3965e" TYPE="ext4" 
/dev/sda1: UUID="7C1C9EB11C9E65C4" TYPE="ntfs" 
/dev/sdb1: SEC_TYPE="msdos" UUID="D437-EB6F" TYPE="vfat" 
hadi@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       


hadi@ubuntu:~$ sudo su
root@ubuntu:/home/hadi# mkdir /media/mount_point
root@ubuntu:/home/hadi# echo "UUID=7C19EB11C9E65C4 /media/mount_point auto users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 1" >> /etc/fstab
root@ubuntu:/home/hadi# mount /de/sda1
mount: can't find /de/sda1 in /etc/fstab or /etc/mtab
root@ubuntu:/home/hadi# mount /dev/sda1
mount: /dev/sda1 already mounted or /host busy
mount: according to mtab, /dev/sda1 is already mounted on /host
root@ubuntu:/home/hadi# mkdir /media/mount_point

---


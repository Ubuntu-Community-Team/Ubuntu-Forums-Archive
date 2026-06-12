---
title: "Hard Drive no longer mounts on start-up"
date: 2012-09-07
forum: General Help
---

### Post by brosskgm on 2012-09-07
Ubuntu 12.04 x64

For almost a year my extra internal drive sda2 has been auto mounting just fine at system start-up.

There was one 7 item update yesterday and everything was fine until I  re-booted the system and the extra 80gig internal drive no longer  mounts. I can manually mount the drive in terminal but it does not show  up on the task bar as it used to.

When I put a dvd in the drive or plug another external drive it mounts fine and shows on task bar.

I would like to get the drive to auto mount and lock on the task bar as it used to.

Thanks for your help.
Bob

When I run : sudo fdisk - l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   156301311    78047232    7  HPFS/NTFS/exFAT

when I run :  mount -a

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/[my name here]/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=[my name here])

---


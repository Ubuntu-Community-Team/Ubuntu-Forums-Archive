---
title: "why does `mount` not match /etc/fstab?"
date: 2009-08-02
forum: General Help
---

### Post by tlroche on 2009-08-02
I'm currently [debugging a swap problem]("http://ubuntuforums.org/showthread.php?t=1229325"): I can't hibernate because PM can't find my swap partition. While debugging that, I'm noticing the following:

```
$ cat /etc/fstab
> # /etc/fstab: static file system information.
> # <file system>                            <mount point>  <type>   <options>                    <dump>  <pass>
> proc                                       /proc          proc     defaults                        0      0
> UUID=a2aed1eb-0801-4780-bcdf-48fcd8f164b8  /              ext3     defaults,errors=remount-ro      0      1
> #/host/ubuntu/disks/boot                    /boot          none     bind                            0      0
> UUID=2e73b542-1cb7-439a-b6a7-046dc4011372  none           swap     sw                              0      0
> # mounts of original NTFS partitions
> # mount /c read-only in case of windows hibernation?
> UUID=F8FCC29BFCC25412                      /media/Preload ntfs-3g  defaults,locale=en_US.UTF-8,ro  0      0
> UUID=136C9F91B524AE31                      /media/PMagic1 ntfs-3g  defaults,locale=en_US.UTF-8     0      0
> # internal mounts for compatibility with cygwin, modeled after /boot mount above     
> /media/Preload                             /c             none     bind                            0      0
> /media/PMagic1                             /e             none     bind                            0      0
> /media/PMagic1/tlroche/backups/t_drive     /t             none     bind                            0      0

$ cat /proc/mounts 
> rootfs / rootfs rw 0 0
> none /sys sysfs rw,nosuid,nodev,noexec 0 0
> none /proc proc rw,nosuid,nodev,noexec 0 0
> udev /dev tmpfs rw,mode=755 0 0
> /dev/disk/by-uuid/a2aed1eb-0801-4780-bcdf-48fcd8f164b8 / ext3 rw,errors=remount-ro,data=ordered 0 0
> tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
> fusectl /sys/fs/fuse/connections fusectl rw 0 0
> varrun /var/run tmpfs rw,nosuid,mode=755 0 0
> varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
> tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
> devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
> /dev/sda1 /media/Preload fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
> /dev/sda5 /media/PMagic1 fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
> /dev/sda1 /c fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
> /dev/sda5 /e fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
> /dev/sda5 /t fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
> securityfs /sys/kernel/security securityfs rw 0 0

$ mount
> /dev/sda6 on / type ext3 (rw,errors=remount-ro)
> tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
> proc on /proc type proc (rw,noexec,nosuid,nodev)
> sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
> varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
> varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
> udev on /dev type tmpfs (rw,mode=0755)
> tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
> devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
> fusectl on /sys/fs/fuse/connections type fusectl (rw)
> /dev/sda1 on /media/Preload type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
> /dev/sda5 on /media/PMagic1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
> /media/Preload on /c type none (rw,bind)
> /media/PMagic1 on /e type none (rw,bind)
> /media/PMagic1/tlroche/backups/t_drive on /t type none (rw,bind)
```

Looks like `mount` and /proc/mounts have pretty much the same information, so I'm assuming `mount` is just presenting the information in /proc/mounts. (Am I missing something?) But I'm wondering, 

[LIST=1]
[*] why does /proc/mounts show the mount by UUID but not `mount`?
[*] why does neither show the swap partition as mounted?
[/LIST]

TIA, Tom Roche <Tom_Roche@pobox.com>

---


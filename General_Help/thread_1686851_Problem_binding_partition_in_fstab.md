---
title: "Problem binding partition in fstab"
date: 2011-02-13
forum: General Help
---

### Post by mr_luksom on 2011-02-13
I'm trying to bind a couple of LVM partitions to directories in the /export directory for NFS hosting.

I can bind the partitions perfectly manually using:
```

sudo mount --bind /media/Media /export/media

```

However fstab fails to bind when I restart, and trying to use the fstab with a mount command to check it yields:
```

glen@mythsrvgk02:/export$ mount /export/media
mount: according to mtab, /media/Media is mounted on /media/Media
mount failed

```

Any ideas on what I am doing wrong?

my fstab:
```


#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=2dd243ea-c2f6-4bb5-b3e2-f1bc00a7aa24 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=7eb7ffd2-3ec4-473d-b725-9337192e94aa none            swap    sw              0       0

#USB Storage
UUID=da6ab223-077a-4576-819e-9efd9eed6dd2 /media/StrUSB01 xfs nosuid,auto 0 0

#LVM
/dev/myth-vg/Mythtv      /media/mythstr xfs nosuid,auto 0 0
/dev/myth-vg/Media       /media/Media xfs nosuid,auto 0 0
/dev/myth-vg/Music       /media/Music ext4 nosuid,auto 0 0
/dev/myth-vg/Photos      /media/Photos ext4 nosuid,auto 0 0
/dev/myth-vg/Documents   /media/Documents ext4 nosuid,auto 0 0

#NFS Share Binding
/media/Media     /export/media       none bind,rw 0 0
/media/Documents /export/documents   none bind,rw 0 0
/media/Music     /export/music       none bind,rw 0 0
/media/Photos    /export/photos      none bind,rw 0 0

```

my mtab when I bind manually (successfully):
```


/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
/dev/sdd1 /media/StrUSB01 xfs rw,nosuid 0 0
/dev/mapper/myth--vg-Photos /media/Photos ext4 rw,nosuid 0 0
/dev/mapper/myth--vg-Music /media/Music ext4 rw,nosuid 0 0
/dev/mapper/myth--vg-Documents /media/Documents ext4 rw,nosuid 0 0
/dev/mapper/myth--vg-Mythtv /media/mythstr xfs rw,nosuid 0 0
/dev/mapper/myth--vg-Media /media/Media xfs rw,nosuid 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
gvfs-fuse-daemon /home/glen/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=glen 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/media/Media /export/media none rw,bind 0 0

```

---

### Post by dcstar on 2011-02-13
> **mr_luksom said:**
> I'm trying to bind a couple of LVM partitions to directories in the /export directory for NFS hosting.

I can bind the partitions perfectly manually using:
```

sudo mount --bind /media/Media /export/media

```

However fstab fails to bind when I restart.
.........


Use the **_netdev** option.

---

### Post by mr_luksom on 2011-02-16
No luck with _netdev.

If it makes it any clearer, the partitions I'm trying to bind are local, hence there is no need to wait for networking. It's just that the binding is required for the nfs hosting.

I'm thinking maybe there are issues binding lvm logical partitions? I never had this issue with regular partitions.

---


---
title: "amd64_edac probe failed with error -22"
date: 2010-12-01
forum: General Help
---

### Post by r.osmanov on 2010-12-01
Hi!
I've got strange *dmesg* errors:
```
$ dmesg | grep error
[   17.514909] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   18.633820] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro
[   25.693017] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro,commit=0
[   26.712816] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro,commit=0
```sdb3 is /:
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             109G   20G   83G  20% /
none                  1.9G  284K  1.9G   1% /dev
none                  2.0G  2.2M  2.0G   1% /dev/shm
none                  2.0G  228K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda1             224G   79G  134G  37% /media/system32
/dev/sdb1              48G   20G   26G  44% /backup
/dev/sdb5             179M   40M  130M  24% /boot
/dev/sdb6              56G   22G   31G  42% /home
/dev/sdc3             368G  195M  349G   1% /media/5e5b8582-a0da-499a-967a-9ec83c65e7de
/dev/sdc2             370G  202G  150G  58% /media/video
/dev/sdc1             180G  128G   43G  75% /media/music
```What may be wrong in configuration?

Thanks.

**UPDATE:**
*/etc/fstab:*
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=3fbee204-97a2-4f45-bc42-6ee1ca6cdf97 /               ext4    errors=remount-ro 0       1
UUID=a295fbab-1ccc-4481-b57a-4dba58f69d89 /boot           ext2    defaults        0       2
UUID=4fc4d5dd-9a32-4025-a2e6-e83356d3866d /home           ext4    defaults        0       2
UUID=bca25a79-40a8-4230-b41c-b299a8d558c1 none            swap    sw              0       0
UUID=cf4dc448-06c4-4d04-8db5-6557decba591 none            swap    sw              0       0
UUID=6c6f3b08-39ff-4a3a-a882-8006def25763 /media/system32 ext3 defaults 0 0
UUID=00ae0d9f-8818-4edd-9337-82806a092430 /backup ext4 defaults 0 0

```

---


---
title: "Raid array members change names and array contains partitions after a reboot"
date: 2010-08-16
forum: General Help
---

### Post by slackey on 2010-08-16
I am moving my Ubuntu install to lvm over raid 1. I created the arrays with only 1 disk initially, planning to add the second disk later. I got the files moved and the system booted up successfully on the new disk, but the arrays and partitions seemed to have changed names. Initially I partitioned the disk as follows

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          20      153600   fd  Linux raid autodetect
/dev/sda2              20      243202  1953359960   fd  Linux raid autodetect
```

I then created 2 degraded raid arrays, corresponding to these partitions, md0 for /boot and md1 for lvm with everything else on it. After installing grub and booting from the new disk, everything seems to work except that weird things are afoot. /dev/md1 has partitions on it even though I all I did was 'pvcreate /dev/md1'
```

Device Boot      Start         End      Blocks   Id  System
/dev/md1p1   *         257       38656      153600   fd  Linux raid autodetect
/dev/md1p2           38657   488378646  1953359960   fd  Linux raid autodetect
```

Additionally, /proc/mdstat shows (I have already added the second disk)

```
md0 : active raid1 sdc1[1] md1p1[0]
      153536 blocks [2/2] [UU]

md1 : active raid1 sdc2[2] sda[0]
      1953359872 blocks [2/1] [U_]
```

Where did md1p1 come from, and why doesn't /proc/mdstat show sda1 and sdc1, and sda2 and sdc2?

---


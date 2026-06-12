---
title: "after a while, ext4 fails to mount to /home"
date: 2009-11-08
forum: General Help
---

### Post by tarekeldeeb on 2009-11-08
Hello all,

I have a severe problem, I cannot mount /home any more, it has very important data.

I have ubuntu 9.04, with SW raid partitions set.
One of them sums to 760 GB and mounted as home. First I noticed some file/folders disappear. Then I did 
```
e2fsck -f -y /dev/md3
```

it seemed like fixing many errors. When I rebooted, the system stopped at boot and I fell into a manual recovery console. I did the check + fiix again to the ext4. But the system failed to mount the partition.

I opened the 'dmesg | tail' and found those lines:
```
[  855.054874] ext4: No journal on filesystem on md3

```

When I try manually to mount the /dev/md3 on /home, it tells me to specify a FS type. Then when I type:

```
sudo mount -t ext4 /dev/md3 /home
```

it gives 
```
mount: wrong fs type, bad option, bad superblock on /dev/md3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Now .. I'm hopeless with this situation ..

please help ..

---

### Post by tarekeldeeb on 2009-11-08
sorry .. I want to add those outputs ..

```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md4 : active raid0 sdb5[1] sda5[0]
      31262208 blocks 64k chunks
      
md2 : active raid0 sdb6[1] sda6[0]
      97658880 blocks 64k chunks
      
md1 : active raid0 sdb2[1] sda2[0]
      97658880 blocks 64k chunks
      
md3 : active raid0 sdb7[1] sda7[0]
      749608704 blocks 64k chunks
      
md0 : active raid1 sdb1[1] sda1[0]
      289024 blocks [2/2] [UU]
      
unused devices: <none>

```

.. which tells that the SW raid are working fine ..

but ..

```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007895c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          36      289138+  fd  Linux raid autodetect
/dev/sda2              37        6115    48829567+  fd  Linux raid autodetect
/dev/sda3            6116       60801   439265295    5  Extended
/dev/sda5           58856       60801    15631213+  fd  Linux raid autodetect
/dev/sda6            6116       12194    48829504+  fd  Linux raid autodetect
/dev/sda7           12195       58855   374804451   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f88d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          36      289138+  fd  Linux raid autodetect
/dev/sdb2              37        6115    48829567+  fd  Linux raid autodetect
/dev/sdb3            6116       60801   439265295    5  Extended
/dev/sdb5           58856       60801    15631213+  fd  Linux raid autodetect
/dev/sdb6            6116       12194    48829504+  fd  Linux raid autodetect
/dev/sdb7           12195       58855   374804451   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/md0: 295 MB, 295960576 bytes
2 heads, 4 sectors/track, 72256 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md3: 767.5 GB, 767599312896 bytes
2 heads, 4 sectors/track, 187402176 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md1: 100.0 GB, 100002693120 bytes
2 heads, 4 sectors/track, 24414720 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 100.0 GB, 100002693120 bytes
2 heads, 4 sectors/track, 24414720 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md4: 32.0 GB, 32012500992 bytes
2 heads, 4 sectors/track, 7815552 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md4 doesn't contain a valid partition table

```

.. this shows MANY problems in partition table !!

any clue .. please ..

---

### Post by tarekeldeeb on 2009-11-08
Thanks Allah ..

I found the solution:
```
sudo tune2fs -O has_journal /dev/md3
```

This recreated the journal .. now my md3 is mounted!

---


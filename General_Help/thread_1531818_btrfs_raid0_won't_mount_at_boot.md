---
title: "btrfs raid0 won't mount at boot"
date: 2010-07-15
forum: General Help
---

### Post by sherl0k on 2010-07-15
I upgraded my 9.10 installation to 10.04 and decided to try out btrfs on a some spare drives in the system.

sudo mkfs.btrfs -m raid0 /dev/sdb /dev/sdc /dev/sdd

the only way the system sees the btrfs array is by running btrfsctl -a and then mounting /dev/sdc. but that has to be done in userland, not at boot. if i try to mount it via fstab, ubuntu won't load because it can't find the mount point.

/dev/sdc      /Images         btrfs   nodatasum,thread_pool=128,compress,rw,user 0       0

so where am i going wrong? I tried mounting via the UUID also but that didn't seem to work for me either.

---

### Post by xavv on 2010-09-28
Hi, 


I'm currently testing BTRFS under Debian with the 2.6.35-4 kernel and the lastest btrfs-prog compiled.

At this point, I've tried to use btrfs on a raid10 pool with 4 devices.

In order to mount this pool at the boot time thanks Fstab, you have to explicitely specify the other devices : 

exemple : 

```

sudo mkfs.btrfs -m raid0 /dev/sdb /dev/sdc /dev/sdd

# Fstab
/dev/sdb  /mnt/mountPoint btrfs defaults,device=/dev/sdc,device=/dev/sdd 0 1

```

Note : You can give any device of the pool for the main one and indicate the others. 

If you use the 

```
blkid
``` command, you will notice that all your devices have the same UUID and a unique UUID_SUB.

The UUID helps to know they are from the same Pool.


Moreover, don't trust the ```
df
``` output. Use rather ```
btrfs filesystem df /mountPoint
```.

It's a well known bug not fixed yet.


Hoping It will help you.

++
xavv

---


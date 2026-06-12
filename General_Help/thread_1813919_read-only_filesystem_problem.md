---
title: "read-only filesystem problem"
date: 2011-07-28
forum: General Help
---

### Post by ubuntizer on 2011-07-28
Hello,

suddenly my filesystem have gone read-only ( / )
My /etc/fstab is as follows

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0


```

When i try to remount it with read-write permissions, i get following error:
```

root@ubuntu:~# mount -o remount,rw /
mount: cannot remount block device /host/ubuntu/disks/root.disk read-write, is write-protected

```

Okay, so this is the filesystem where the actual OS is installed, right?
What should i do to fix the errors with it and mount it back with read-write permissions.

Thanks.

---

### Post by rattking on 2011-07-28
have you tried fscking the filesystem? a filesystem with errors will be remounted read only as defined here errors=remount-ro
fsck.ext4 /host/ubuntu/disks/root.disk

I see root.disk is a wubi thing.. I have never used it so I apologize if I am missing something obvious.

---

### Post by Mark Phelps on 2011-07-28
Are you trying to manually mount root.disk?

If you're inside your Wubi-installed Ubuntu and trying to do this -- it won't work because it's already mounted.

---

### Post by bcbc on 2011-07-28
Refer to the wubi guide on how to fsck the root.disk [https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)

1. identify the partition the root.disk is on (while in Wubi, running "mount" from a terminal will show the /host partition)
2. boot an Ubuntu CD in live mode (select "Try it" without installing)
3. mount the partition and fsck the root.disk (assuming it's e.g. /dev/sda1)
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```

---

### Post by ubuntizer on 2011-07-31
Yes, its a wubi install. 
Thanks bcbc, it worked.

---


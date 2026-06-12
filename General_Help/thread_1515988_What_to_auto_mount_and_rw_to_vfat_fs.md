---
title: "What to auto mount and rw to vfat fs"
date: 2010-06-23
forum: General Help
---

### Post by coolboarderguy on 2010-06-23
Hi All,

here is my output for fstab and mount for a fat32 partition that I want to be able to write to.

coolboarderguy@coolboarderguy-laptop:~$ cat /etc/fstab | grep sda8
/dev/sda8       /mnt/sharefat   vfat    auto rw,noexec,user  0       0
coolboarderguy@coolboarderguy-laptop:~$ mount | grep sda8
/dev/sda8 on /mnt/sharefat type vfat (rw)

I get the below though. 

coolboarderguy@coolboarderguy-laptop:~$ touch /mnt/sharefat/mount_rw_test_file
touch: cannot touch `/mnt/sharefat/mount_rw_test_file': Permission denied

What have I missed? Thanks.

Mark

---

### Post by mikewhatever on 2010-06-23
Try adding umask=000 or similar.

---

### Post by coolboarderguy on 2010-06-23
> **mikewhatever said:**
> Try adding umask=000 or similar.

That did the trick. Went and brushed up on umask as well. Thanks.

---


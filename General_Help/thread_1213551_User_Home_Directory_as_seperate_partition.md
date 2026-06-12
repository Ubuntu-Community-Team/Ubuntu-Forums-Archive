---
title: "User Home Directory as seperate partition"
date: 2009-07-14
forum: General Help
---

### Post by thejapanesegeek on 2009-07-14
Placing /home on it's own partition is a common and well-documented scenario. However, I only have one user and I would much prefer to mount /home/user as its own partition. I set it to be mounted as such during installation. However, when I went to boot up my system, I got an error about permissions. The /home/user directory was owned by root, like most mounted drive. 
```
 ls -l
drwxrwx--- 14 root plugdev 16384 1969-12-31 19:00 user
```
I attempted a ```
# chown user:user /home/user
``` but I got the following error message:
```
chown: changing ownership of `/home/user': Operation not permitted
```

Any idea how I can fix this, or will I just have to mount /home ? 

Here's my /etc/fstab if it helps.

```

root@ubuntu-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=e489536b-526a-4978-8882-d8233f14bb7e /               ext3    relatime,errors=remount-ro 0       1
# /home/user was on /dev/sda2 during installation
UUID=02AB-CC32  /home/user       vfat    utf8,umask=007,gid=46 0       1
# /media/windows was on /dev/sda1 during installation
UUID=3C74F6F674F6B1AE /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=c6b2273a-5677-4782-92ff-4b741dd63f5a none            swap    sw              0       0
```

---

### Post by michy99 on 2009-07-14
Did you really put /home/user on a vfat partition? That will never work. vfat file systems do not support linux permissions.

---

### Post by thejapanesegeek on 2009-07-14
Wow, I suppose you're right. That makes a lot of sense. Thanks.

---


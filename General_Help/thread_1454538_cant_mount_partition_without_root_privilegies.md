---
title: "cant mount partition without root privilegies"
date: 2010-04-14
forum: General Help
---

### Post by repu1sion on 2010-04-14
part of /etc/fstab:
/dev/sda2       /mnt/lfs        ext4 rw,users,noauto,suid,exec,uid=1002      0       2

$ mount /dev/sda2 /mnt/lfs
mount: only root can do that

whats wrong with it? 'man mount' says that any can mount partition if it contains option 'user' or 'users' in /etc/fstab ?

---

### Post by mk1w86 on 2010-04-14
It doesn't solve your problem but any partitions in fstab get automatically mounted at start up so it should not be necessary to mount it manually.  You could also just use sudo, then again, I don't know what you are trying to achieve overall so I could be wrong. ;)

---

### Post by prodigy_ on 2010-04-14
> **repu1sion said:**
> mount: only root can do that
Did you check the permissions on **/mnt/lfs**?

---

### Post by prodigy_ on 2010-04-14
> **mk1w86 said:**
> any partitions in fstab get automatically mounted at start
Not exactly. Specifically, **noauto** option prevents a partition from being auto-mounted.

---

### Post by mk1w86 on 2010-04-14
> **prodigy_ said:**
> Not exactly. Specifically, **noauto** option prevents a partition from being auto-mounted.

Ahh, I didn't read the original post properly. ](*,)

---

### Post by repu1sion on 2010-04-14
permissions seems to be ok.
/mnt$ ls -la
total 12
drwxr-xr-x  3 root      root 4096 2010-04-15 01:49 .
drwxr-xr-x 24 root      root 4096 2010-04-12 12:29 ..
drwxrwxrwx  2 repu1sion root 4096 2010-04-15 01:17 lfs
/mnt$ ls -la /dev/sda2
brwxrwxrwx 1 root disk 8, 2 2010-04-15 01:17 /dev/sda2
/mnt$ mount /dev/sda2 /mnt/lfs
mount: only root can do that

personally i want to mount partition from script and not from bootup one.

---

### Post by prodigy_ on 2010-04-14
Hmm. AFAIK, "users" option in **/etc/fstab** has literal meaning. So, is your account a member of the group "users"? Use this command to check: ```
cat /etc/group|grep '^users:'
```

The output should look like: ```
users:x:100:... <your_user_name> ...
``` If the last field is empty you'll need to add your account to this group.

---

### Post by repu1sion on 2010-04-15
actually 
mount /dev/sda2 /mnt/lfs 
will not work.
but mount /dev/sda2 is ok
and also mount /mnt/lfs is ok too

---


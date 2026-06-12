---
title: "User cannot access his own directories"
date: 2012-09-23
forum: General Help
---

### Post by SeaKing on 2012-09-23
Hey,

I have a strange problem, my user (only one except root) can not access one specific directory which belongs to them.

History:
I've mounted my raid under /raid 
fstab:
```
/dev/sdb1    /raid        ext4    defaults    0    0
```some day I couldn't enter the* /raid/backup *directory as normal user just as root and ls -la gave me an empty folder, but ls -lsa showed me the right content. I unmounted the raid, ran fsck and remounted it. The result was ls -la showed me the right content of /raid/backup but only as root, if I try *cd /raid/backup* I get a permission denied but the folder has the following rights:
```
drw-rw-rw- 376 seaking seaking    36864 Sep 16 14:20
```

---

### Post by einonm on 2012-09-23
A directory must be executable by the user in order to be accessed.

So, try 'chmod 777 /raid/backup' to add execute permissions. The ls -al output should then look something like:

```
drwxrwxrwx 376 seaking seaking    36864 Sep 16 14:20
```

---


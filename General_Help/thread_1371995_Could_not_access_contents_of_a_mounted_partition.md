---
title: "Could not access contents of a mounted partition"
date: 2010-01-04
forum: General Help
---

### Post by hariks0 on 2010-01-04
I had my hard disk partitioned as below:-

_Size  Label      Mount point File system_
52 GB Multimedia /MM               ntfs
52 GB Backup     /ABackup          ntfs
52 GB Extras     /Extras           ext4
27 GB root       /                 ext4
60 GB home       /home             ext4

The problem is that I cannot access the /MM and contents. I tried Properties > Permissions and changed applied the changes to subfolders and contents too. Now I can access /MM but not the contents. All are marked with a lock logo. There are numerous folders/files. Changing the permissions individually is a hectic work.

Is it possible to do it in a command line/script? And what is the reason for the lock up?

Thanks for any help

---

### Post by hariks0 on 2010-01-04
Bump

---

### Post by mcgrmic2 on 2010-01-04
```
sudo chmod -R 0775 /MM
```
If that doesn't work it may be a ownership problem, try
```
sudo chown -R username:groupname /MM
```

---

### Post by mcgrmic2 on 2010-01-04
Don't know what the lockup is, becuase I am having a very similar problem with permissions.

[http://ubuntuforums.org/showthread.php?t=1371831](http://ubuntuforums.org/showthread.php?t=1371831)

---

### Post by hariks0 on 2010-01-05
> sudo chown -R username:groupname /MMIt worked. Thank you very much.

---


---
title: "disabling the rm command"
date: 2010-11-03
forum: General Help
---

### Post by prabhanjan2906 on 2010-11-03
I have a directory in which the files are stored. the users must be able to only read or add files to the directory. the users must not delete the files under the directory. how can i do this? is it possible to disable the rm command?


Thanks in advance

---

### Post by matt_symes on 2010-11-03
Hi

What is the filing system type for the directory? NTFS or an ext variant or other? Is it a local directory or samba?

Kind regards

---

### Post by a-user on 2010-11-03
as matt_symes asked, it is important what fs you are using.
on linux typical fs like all ext variations you could achieve this with the following steps:
1. directory needs write acces for your user group (to being able to add files)
2. the creation mask for new files must have write access removed for all (but maybe a special user), thus files cannot be deleted or modified.

i don't remember how exactly the commands are for this so a bit google would be needed.

---

### Post by prabhanjan2906 on 2010-11-04
the file system is ext4 file system.

---

### Post by sisco311 on 2010-11-04
If the sticky bit is set on the directory, only the owner of a file or the owner of the directory (and the super-user of course) will be able to delete that file. 

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---


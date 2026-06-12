---
title: "Copy file from Windows Network Share to Linux"
date: 2010-06-23
forum: General Help
---

### Post by twanchic on 2010-06-23
I have some files on a windows shared folder on my local network. I can't seem to figure out how to copy from it to my local machine through bash. I need to be able to do this through bash.

**Location I'm trying to get from:**
smb://ts2/file.dbf

**I'm trying to get it to:**
/home/toddw/datadump

**when i run the command:**
cp smb://ts2/sbt/file.dbf /home/toddw/datadump

**I get:**

cp: cannot stat `smb://ts2/sbt/file.dbf': No such file or directory


What am I missing here?

---

### Post by J V on 2010-06-23
you have to use the samba program to access windows shares... You can choose to mount the windows share and copy from the mount point, or use the smbclient CLI to copy it over...

man samba
man smbclient

---


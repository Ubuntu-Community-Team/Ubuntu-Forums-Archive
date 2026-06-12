---
title: "Problem with permissions with samba share"
date: 2010-10-12
forum: General Help
---

### Post by xzased on 2010-10-12
Hi, we have a samba share in a machine with RedHat 5.3. this is our config for the share:
```
[test]
	comment = test
	path = /test
	read only = no
	force create mode = 0775
	force directory	mode = 0775
	posix locking = No
```
We have one account (admin). We also created a folder called test00 and change its ownership to root such as the ls -al output is:

```
drwxr-xr-x    3 root     root     4096 Oct 12 18:22 test00
```

and created another folder inside test00 called test01 and change its ownership to admin account. However, when mapped via a windows client using admin account, we cannot delete the folder test01, which is supposed to be owned by admin. Is this how it is supposed to work? Shouldnt the admin account have permission to delete the folder it owns?

---


---
title: "removing root restrictions"
date: 2009-12-02
forum: General Help
---

### Post by princeofnam on 2009-12-02
i transferred two folders over from my flash drive with root privileges.  now i can't access them unless i'm in root.  how do i remove such restrictions?

---

### Post by wojox on 2009-12-02
Try:

```
gksudo nautilus
```

---

### Post by Sam on 2009-12-02
Or better, reset the permissions once for all```
sudo chown -R `whoami`:`whoami` /path/to/folder
```

---

### Post by igknighted on 2009-12-02
You can change the permissions on the folder with the command (MAKE SURE YOU CHANGE /path/to/drive to the actual path to your flash drive):
```
sudo chmod a+rwx -R /path/to/drive
```

"sudo" is to give you root powers
"chmod" is a command to change the read/write/execute rights of a file
the "a" is for all users
the "+" means you are adding priveleges
the "rwx" is for read, write and execute (privileges can be changed individually for each)
the "-R" is to make it recursive, ie it acts on every file in the directory
and the "/path/to/drive" is so the command know what folder to act on


EDIT:
The post above is a better solution... my post changes the rights of the drive (while leaving root as the owner), but the previous post actually makes your user the owner.

---


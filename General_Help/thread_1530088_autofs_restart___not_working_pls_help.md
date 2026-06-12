---
title: "autofs restart   not working pls help"
date: 2010-07-13
forum: General Help
---

### Post by molykkutti on 2010-07-13
/etc/init.d/autofs restart


      when i gave this command through command prompt the following error message appeared .. i don't know how to solve this .. pls help
Stopping automounter: done.
Starting automounter: loading autofs4 kernel module,FATAL: Error inserting autofs4 (/lib/modules/2.6.24-16-generic/kernel/fs/autofs4/autofs4.ko): Operation not permitted
mkdir: cannot create directory `/var/run/autofs': Permission denied
/usr/sbin/automount: This program must be run by root.

---

### Post by bilkay on 2010-08-15
The answer is in the last line.


Make it:
```
sudo /etc/init.d/autofs restart

or

sudo service autofs restart
```

---

### Post by supershin on 2010-08-15
Once you see anything saying "Permission denied and must be run by root" it means you gotta use sudo to execute the program/command. To use sudo just type sudo before the command.

Be careful using sudo. See for more info.
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---


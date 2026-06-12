---
title: "Permission problems in Nagios"
date: 2010-06-02
forum: General Help
---

### Post by shai3421 on 2010-06-02
I've installed Nagios and from the "Service Overview" in the web interface I get the following 2 errors relating to localhost:

Disk Space line: DISK CRITICAL - /home/shai/.gvfs is not accessible: Permission denied 
SSH line: Connection refused 

I've started the Nagios service as sudo so I don't know what is causing this.

Any help would be greatly appreciated.

---

### Post by shai3421 on 2010-06-02
When I try to get access to the directory .gvfs, I get this:

root@shai-desktop:~# chown -R $USER .gvfs
chown: cannot access `.gvfs': Permission denied

?

---

### Post by shai3421 on 2010-06-02
Okay I fixed the problem with the .gvfs, now only the problem with the SSH remains,

Anyone?

---

### Post by jordanthompson on 2010-12-18
So how did you fix this problem?

---

### Post by mhgsys on 2011-05-04
[http://ubuntuforums.org/showthread.php?p=10768219#post10768219](http://ubuntuforums.org/showthread.php?p=10768219#post10768219)

---


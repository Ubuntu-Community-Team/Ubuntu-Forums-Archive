---
title: "CIFS VFS: cifs_mount failed"
date: 2009-09-08
forum: General Help
---

### Post by landolini on 2009-09-08
The command used in long stopped working! I can not find the meaning of the return code -22!
Where can I try ..? mount.cifs not in there '...
 Thank you.

 sudo mount -t  cifs //172.16.196.300/Cart_Cond  /mnt/smb 
[526.485384] CIFS VFS: cifs_mount failed w / return code = -22

---

### Post by uncle-c on 2009-09-08
do you have smbfs installed ?

---

### Post by landolini on 2009-09-08
> **uncle-c said:**
> do you have smbfs installed ?

No ...it is deprecated . I have Ubuntu 9.04.

---

### Post by uncle-c on 2009-09-08
Yes, but it still contains some libs/files needed for cifs to work.
I was getting a similar problem, see if this helps :

[http://ubuntuforums.org/showthread.php?t=1139646](http://ubuntuforums.org/showthread.php?t=1139646)

The last two posts may solve the problem.

uc

---

### Post by landolini on 2009-09-08
Installing smbfs the mount command is not recognized...
My problem could be more complex because my Ubu 9.04 is a 
guest virtual machine and Ubu 8-04.1 is the host.
I could have network problems..and   the meaning of return code 22  could help..

---

### Post by landolini on 2009-09-08
Nobody knows where can be found the meaning of the return code -22!

---


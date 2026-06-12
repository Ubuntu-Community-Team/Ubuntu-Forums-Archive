---
title: "unable to change SCSI hard drive permissions"
date: 2010-04-11
forum: General Help
---

### Post by jakerman999 on 2010-04-11
Running a machine with SCSI based drives as a server machine(head attached) and found that I was unable to change permissions for my two internal hard drives.  A little bit of googling told me that was because the owner of the drives was root.  This lead me into changing my fstab file so that the drives had the following option tags:

```
auto,dev,exec,suid,rw,user,async,umask=000,uid=1000,gid=100
```

Before, both drives permissions were 700 and owned by root, unchangeable even with su.  Now, permissions are 755 and 777 on the two separate drives, both owned by me, and neither cannot be changed (even with su).

What confuses me is, why would the permissions be different for each drive when all I did was edit the fstab?  

I would like to be able to change both drive permissions to read 775 if possible.  Thanks in advance.


EDIT:  Updated to Kubuntu 10.04 Beta and problem resolved itself.  This is why I love gnu/linux.

---


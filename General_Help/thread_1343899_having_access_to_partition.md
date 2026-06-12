---
title: "having access to partition"
date: 2009-12-02
forum: General Help
---

### Post by drifter0000 on 2009-12-02
I just switched to 9.10 32 bit and I am loving it.  I have finally done away with my windows partition.
I am sure this seems like a simple problem to all of you but I cannot seem to fine a simple answer on the net.
Before switching from 9.04 I created a second partion (ext3) and copied my home folder over to it so that I could put documents and other things on the new 9.10 partion.
I am finding out that the second partion only has root access and it is very complicated to move files to 9.10 and changing their permissions.
Is there an easy way to get access to this partition like I had with windows so that I can just copy and paste back and forth between 9.10 partition and the second partion where I would like to keep backups?

Thanks for your help and 9.10 is really great!!!

---

### Post by oldos2er on 2009-12-02
```
sudo chown -R user:user /media/drive
``` where user is your user name, and /media/drive is the partition you want to write to.

 Or you can run ```
gksu nautilus
``` find the partition, right-click on it, choose 'Properties', 'Permissions', choose the permissions you want, then click 'Apply Permissions to enclosed files'.

 More info here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---


---
title: "problem with NFS share on mounted harddrive"
date: 2010-05-04
forum: General Help
---

### Post by DeathscytheDK on 2010-05-04
Hi everybody.
 
I'm having a bit of a problem with my setup. 
I'm running Ubuntu 10.4 on my pc. Ubuntu is installed on a 80 GB HDD, and I also installed a 500 GB HDD formated in ext4.
in my home dir I'v created a dir (/home/user/shared) and i that dir I'v created another (/home/user/shared/mount) :o
I'v mounted the sdb1 (the 500 GB HDD) til the mount dir.
Then I'v created a NFS share to the shared folder.

My problem is this, from my PC2 I can access the NFS, and I can see the mount dir, but I can't se the contens of the the mount :confused:

Is this not possible?
 
ohh yes, and my /etc/exports looks like this:
/home/user/shared/mount 192.168.0.100(rw,sync,subtree_check)
and my fstab entry:
/dev/sdb1 /home/user/shared/mount ext4 defaults 0 0

Am I doing it right, or is there something I'm missing?
All I want to do is to create a nfs share on the 500 GB hdd
 
thanks in anvance
Christian

---

### Post by jbrown96 on 2010-05-04
It's probably a permission problem.

on the nfs server, run ```
ls -l /home/user/shared/
``` and ```
ls -l /home/user/shared/mount
``` post the output here. You can fix it with ```
sudo chmod -R o+rw /home/user/shared
```

---

### Post by DeathscytheDK on 2010-05-04
> **jbrown96 said:**
> It's probably a permission problem.
 
on the nfs server, run ```
ls -l /home/user/shared/
``` and ```
ls -l /home/user/shared/mount
``` post the output here. You can fix it with ```
sudo chmod -R o+rw /home/user/shared
```
ls -l /home/user/shared
total 8
drwx------ 3 user user 4096 2010-05-03 22:40 download
drwx------ 5 user user 4096 2010-05-03 23:25 mount
drwxrwxrwx 8 root root 0 2010-05-03 12:06 terastation
 
ls -l /home/user/shared/hdfilm
total 24
drwx------ 2 root root 16384 2010-05-03 22:39 lost+found
drwxrwxrwx 3 user user 4096 2010-05-01 14:24 Transformers 1
drwxrwxrwx 2 user user 4096 2010-05-01 14:03 Transformers 2
 
Is this right?

---

### Post by jbrown96 on 2010-05-04
I'm not exactly sure about what you're trying to share, but I think it's everything in /home/user/shared/. If that's the case, then you need to allow "others" to access it.

Here's how Linux permissions work. There are three sets of permissions: owner, group, others. There are three permissions for each: read, write, execute. So given drwx------, that means the type is d (directory) and the owner (first three letters) has r (read), w (write), and x (execute) permission. Group and others have no permissions. 

For NFS to work, "others" needs to have read (at least) and write (if you want) permissions. Try ```
sudo chmod -R o+rw /home/user/shared/
```

---

### Post by DeathscytheDK on 2010-05-04
All I want to do it access the data on the 500 gb hdd in PC1 from PC2 via nfs

I'll give it a try when I come home
 
thx jbrown96

---


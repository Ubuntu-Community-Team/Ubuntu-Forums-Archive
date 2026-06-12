---
title: "Mount new HDDs"
date: 2009-08-05
forum: General Help
---

### Post by shaker108 on 2009-08-05
Hi,

I recently added two new HDD to my PC (ububtu 9.04). 

I'm going to use the first one for backup and I want the backup script to mount/unmout it. The problem is that this fails "mount /dev/sdc1 /mnt/myBackup" ... it just results in "mount: only root can do that". 

I added this to fstab and rebooted but it does not help "/dev/sdc1 /mnt/myBackup ext3 user,noauto 0 0". 

I want the second HDD to automatically mount at "/home/<user>/Virtualbox". I tried adding "/dev/sdb1 /home/<user>/Virtualbox ext3 defaults 0 0"  but I'm unable to write to it.

What am I doing wrong? Thanks.

---

### Post by michy99 on 2009-08-05
When you mount from the command line, you need to precede the command with sudo to give yourself root permissions.```
sudo mount -t ext3 /dev/sdc1
```

To fix the permissions issue, make sure that the mountpoint is owned by you.```
sudo chown <user> /home/<user>/Virtualbox
```

---

### Post by shaker108 on 2009-08-05
/home/<user>/Virtualbox is owned by me since its my home directory but I'm still unable to write to it.

And isnt it possible to mount without using sudo?

[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab) here it says that the "user" option in fstab permits any user to mount the filesystem.

---

### Post by michy99 on 2009-08-05
Just because something is in your home directory doesn't mean it is owned by you. To find out, right-click on the folder and select Properties and look under the permissions tab.

---


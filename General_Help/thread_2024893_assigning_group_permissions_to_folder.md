---
title: "assigning group permissions to folder"
date: 2012-07-14
forum: General Help
---

### Post by DanH860 on 2012-07-14
Hi all,

I'm sure this has been covered a load of times before but from searching, I can't seem to get this to work:

I've got a partition on my laptop that automatically gets mounted under /media/data

When logged in as the admin user I can access and write to this folder fine but when I create another user, they cannot access this folder. I've added both the admin user and new user to a new group and have tried to assign group permissions to the folder by using the commands:

```
 sudo chgrp -R groupname /media/data 
``````
 sudo chmod -R 770 /media/data 
```However, when logging in as the new user and navigating to the folder, I can't access it. Can anyone point me in the right direction?

Thanks

---

### Post by Morbius1 on 2012-07-14
What is the output of the following command:
```
ls -dl /media/data
```
And is /media/data pointing to an NTFS or FAT32 partition?

---

### Post by DanH860 on 2012-07-14
Hi, the output is:

```
drwxr-x--- 1 nathalie nathalie 16384 Jul  7 15:07 /media/data
```

to me it looks like the drive is readable and executable for the group, but not writeable... The partition is ntfs by the way

Thanks

---

### Post by Morbius1 on 2012-07-14
To me it looks like it accessible only to nathalie unless your other users are menbers of natchalie's group.

Post the output of your fstab:
```
cat /etc/fstab
```You will need to modify the line for that partition to include or modify these options:
gid=groupname and umask=007

A chgrp, chmod, chown, or ch-anything has no affect of an ntfs partition. You need to change these things in fstab.

---

### Post by DanH860 on 2012-07-14
At the moment my fstab entry looks like this:

```
UUID=04D044A94C653910   /media/data   ntfs uid=1000,gid=1000,dmask=027,fmask=137   0   2
```

I'm not sure on the dmask & fmask settings - I had just copied these from another guide to be honest.  Should I delete the uid, dmask and fmask entrys, change the uid entry and then add the umask entry you mentioned?

---

### Post by Morbius1 on 2012-07-14
Change this:
> UUID=04D044A94C653910   /media/data   ntfs uid=1000,gid=1000,dmask=027,fmask=137   0   2To this:
> UUID=04D044A94C653910   /media/data   ntfs uid=1000,[COLOR=Blue]**gid=groupname**[/COLOR],[COLOR=Blue]**dmask=007**[/COLOR],[COLOR=Blue]**fmask=117**[/COLOR]   0 [COLOR=Blue]**0**[/COLOR]Unmount the partition:
```
sudo umount /media/data
```Then remount it with this command which will also check for any typos you might make:
```
sudo mount -a
```

---

### Post by DanH860 on 2012-07-14
Perfect, thanks for the help, it works!

---


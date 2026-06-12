---
title: "permission for mounted drive"
date: 2011-11-10
forum: General Help
---

### Post by fansaty on 2011-11-10
Hi,
I am currently using Ubuntu Server 10.04.3 LTS, i format drive using mkfs.vfat.
I create folder in /home/mount_folder and set permission:
   $ sudo chgrp -R users /home/mount_folder
   $ sudo chmod -R 775 /home/mount_folder
   $ sudo chmod -R +t /home/mount_folder
-> drwxrwxr-t root users
After i mount drive in fstab:
   /dev/sdb1   /home/mount_folder   vfat   defaults   0   0

Reboot and see permission mount_folder: drwxr-xr-x root root. I can not set permission for it by sudo: Operation not permitted. I would like it to look like "drwxrwxr-t root users" but i can not set any permission for it.

Please tell me how i have to do?

Thanks.

---

### Post by blueridgedog on 2011-11-10
To mount a vfat partition, you must specify permission at mount:

/dev/sdb1 /home/mount_folder vfat uid=root,gid=users,utf8 0 0

To fine tune your permissions, you will need a umask, such as:

- umask=0007 allows user and group read, write and execute permission. Others have no permission.
- umask=0227 allows user and group read and execute permission. Others have no permissions.

So:

/dev/sdb1 /home/mount_folder vfat umask=0000,uid=root,gid=users,utf8 0 0

You will need to research umasks to get the permissions you want, they are basically the inverse of chmod permissions.

An alternative would be to format the partition with a permissions aware file system, such as ext3 or ext4.

A great write up on umask can be found here:

[http://electron.mit.edu/~gsteele/linuxfaq/](http://electron.mit.edu/~gsteele/linuxfaq/)

To quote the page:

Now, umask is like the binary NOT of the file permissions you want. For
example:

```
rwxr-xr-x  - desired file permissions
111101101  - binary file permissions
000010010  - umask
0  2  2    - octal umask
```

---

### Post by fansaty on 2011-11-10
Thanks, it worked.
As i don't know where to config the values.
can i add permission with **+t** parameter for folder? Look like 
$ sudo chmod -R **+t** /home/mount_folder
-> drwxrwxr-**t** root users

Because i would like user can not delete or modify other's file and folder.

---


---
title: "ecryptfs-mount-private"
date: 2010-05-07
forum: General Help
---

### Post by morelo2211 on 2010-05-07
Here is my log:

```

root@ubuntu:/media# chd="/media/687058f8-52dd-4095-bcb4-3ca04a664981"
root@ubuntu:/media# mount -o bind /dev/ $chd/dev
root@ubuntu:/media# mount -t proc proc $chd/proc
root@ubuntu:/media# chroot $chd
root@ubuntu:/# login rasto
Password: 
Last login: Wed May  5 19:44:29 CEST 2010 on pts/0
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Fri May  7 17:30:41 CEST 2010

  System load:  1.87   Swap usage: 97%   Users logged in: 0
  Memory usage: 20%    Processes:  141

  => There is 1 zombie process.
  => There were exceptions while processing one or more plugins. See
     /var/log/landscape/sysinfo.log for more information.

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

open: Permission denied
Error locking counterTo run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

rasto@ubuntu:~$ ls
Access-Your-Private-Data.desktop  README.txt
rasto@ubuntu:~$ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [1264626856c8df66] into the user session keyring
open: Permission denied
Error locking counter

```

I cannot start ubuntu, so I do this what you can see in my log. My problem is this error:
```

open: Permission denied
Error locking counter

```

Pls. Can somebody help me with my problem. Thanks

---

### Post by brt62 on 2010-05-13
I had the same problem after reinstalling my windows partition which was automounted.

Found [https://bugs.launchpad.net/ecryptfs/+bug/573518](https://bugs.launchpad.net/ecryptfs/+bug/573518)

                 adding the line below to my fstab and removing the line for the windows partition fixed  the problem.
 tmpfs     /dev/shm     tmpfs     defaults 0 0


hope this will help you

---

### Post by tc0nn on 2012-04-26
> **brt62 said:**
> I had the same problem after reinstalling my windows partition which was automounted.

Found [https://bugs.launchpad.net/ecryptfs/+bug/573518](https://bugs.launchpad.net/ecryptfs/+bug/573518)

                 adding the line below to my fstab and removing the line for the windows partition fixed  the problem.
 tmpfs     /dev/shm     tmpfs     defaults 0 0


hope this will help you

That worked for me... VMware upgrade/move caused mine.

---


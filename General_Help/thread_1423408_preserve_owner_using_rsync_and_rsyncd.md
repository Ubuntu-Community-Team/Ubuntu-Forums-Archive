---
title: "preserve owner using rsync and rsyncd"
date: 2010-03-06
forum: General Help
---

### Post by vascot on 2010-03-06
Hi,
i try to make a backup using rsync. On my other computer i run a rsync deamon.

I want to copy my files while preserving the numerical user id (rsync -a). But, with this setup the deamon is not able to create directories:
rsync: recv_generator: mkdir "/home" (in backup-a) failed: Permission denied (13)

/etc/rsyncd.conf
```

use chroot = yes
numeric ids = yes
log file = /var/log/rsyncd.log
read only=false

[backup-a]
path = /media/backup/a/.
hosts allow = 192.168.1.7

```

But with this all files are owned by root:
/etc/rsyncd.conf
```

uid=root
gid=root
use chroot = yes
numeric ids = yes
log file = /var/log/rsyncd.log
read only=false

[backup-a]
path = /media/backup/a/.
hosts allow = 192.168.1.7

```

How can I configure rsyncd that this is possible?

---

### Post by tom4everitt on 2010-03-06
I think its the first version thats correct. What you need to do is to change the owner of the folder where it should do mkdir.:

sudo chown nameofuser:nameofgroup /media/backup/a

---

### Post by vascot on 2010-03-06
> **tom4everitt said:**
> I think its the first version thats correct. What you need to do is to change the owner of the folder where it should do mkdir.:

sudo chown nameofuser:nameofgroup /media/backup/a

But I run rsync as root, because I also want to backup /etc and all homedirs. So, it should work regardless of the owner of the dir. But even with root:root it doesn't work.

---

### Post by tom4everitt on 2010-03-07
And what about giving the folder full permissions?

sudo chmod 777 /media/backup/a

(or, if you want it to be applied recursively

sudo chmod -R 777 /media/backup/a

)

---

### Post by vascot on 2010-03-07
> And what about giving the folder full permissions?
Then rsync can create files, but everything is owned by nobody:nogroup

---

### Post by tom4everitt on 2010-03-07
But this probably means that it preserved the _numerical_ user and group, but you do not have a user with that number on the computer you're copying to (nor such a group). 

One way to check this is to create a user with the right uid on the machine your copying to, and see whether the files seems to be owned by that user.

---

### Post by vascot on 2010-03-07
> **tom4everitt said:**
> But this probably means that it preserved the _numerical_ user and group, but you do not have a user with that number on the computer you're copying to (nor such a group). 

One way to check this is to create a user with the right uid on the machine your copying to, and see whether the files seems to be owned by that user.

No, i have exactly the same users and groups on the computers. The numerical preserve option should solve your problem: even when users doesn't exist, files should get created with the same uid as the source file.

Even when I try to backup from the local machine to the local machine it doesn't work.

---

### Post by tom4everitt on 2010-03-07
That sounds like a bug. Does cp -p preserve the right owner? and what about scp -p

---

### Post by vascot on 2010-03-07
Very strange. I did create a new ext4 partition. It is mounted using defaults:
/dev/sdb1 on /media/backup type ext4 (rw)

When I copy from /tmp to /tmp using sudo cp -p owners are good. But when I copy to /media/backup, owner is always root. But I can chown files in /media/backup

---

### Post by tom4everitt on 2010-03-08
That sounds strange, yes. I'm out of ideas:confused:

---

### Post by vascot on 2010-03-09
I'll try to reformat the ext4 filesystem

---

### Post by vascot on 2010-03-22
cp -p does work now as expected. rsync not yet :(

---


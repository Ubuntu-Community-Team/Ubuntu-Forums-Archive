---
title: "Problem running sshfs"
date: 2011-09-23
forum: General Help
---

### Post by satimis on 2011-09-23
Hi folks,

Ubuntu 11.04 desktop 64bit


I could access the remote server running;
$ ssh user@ipaddress

But I couldn't mount the remote server running;
$ sshfs user@ipaddress:/path /mnt/remoteserver```

fusermount: failed to open /etc/fuse.conf: Permission denied
fusermount: user has no write access to mountpoint /mnt/remoteserver

```

$ ls -l /bin/fusermount```

-rwsr-xr-x 1 root root 31320 2011-02-11 05:03 /bin/fusermount

```

$ ls -l /etc/fuse.conf```

-rw-r----- 1 root fuse 216 2010-01-27 08:28 /etc/fuse.conf

```

What shall I do with these 2 files?  TIA


B.R.
satimis

---

### Post by kimberlite on 2011-09-23
Hi,
Try to run with sudo, if you have enough rights:

```
sudo sshfs user@ipaddress:/path /mnt/remoteserver
```

My second guess: add yourself to "fuse" group.
Cheers

---

### Post by satimis on 2011-09-23
> **kimberlite said:**
> Hi,
Try to run with sudo, if you have enough rights:

```
sudo sshfs user@ipaddress:/path /mnt/remoteserver
```

My second guess: add yourself to "fuse" group.
Cheers

Hi,

Tks for your advice.  I tried your suggestion before posting.  It mounted the local PC

Tried again
$ sudo sshfs user@ipaddress:/home/user /mnt/remoteserver/ 
It mounts without complaint

$ ls /mnt/remoteserver```

ls: cannot access /mnt/remoteserver: Permission denied

```

$ sudo ls /mnt/remoteserver 
No printout

$ cd /mnt/remoteserver```

bash: cd: /mnt/remoteserver: Permission denied

```

$ sudo cd /mnt/remoteserver```

sudo: cd: command not found

```

$ su root
Password: 
# cd /mnt/remoteserver/

# ls /mnt/remoteserver
no printout
 
# ls /home/
lost+found  user
(remark: same username on both remote server and local PC)

# ls /home/user/
it displays the files of the local PC


$ cat /etc/group | grep fuse```

fuse:x:104:

```

Any advice?  TIA

B.R.
satimis

---

### Post by kimberlite on 2011-09-23
What happens if you try to mount into your home folder i.e. not to a privileged folder. This is my usual practice, and it is working. Sorry, I am not on 64-bit, but the problem at first sight seemed to be trivial :(. Probably we need help from others ... Cheers, Kim

---

### Post by Jack Waugh on 2012-01-12
or you could change the ownership of the mount point to yourself.

---


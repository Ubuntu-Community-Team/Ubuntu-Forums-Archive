---
title: "Mount SFTP server"
date: 2011-05-04
forum: General Help
---

### Post by megabuffen on 2011-05-04
I have two servers, one is a game server and the other a web server. I would like to mount a directory on the web server in a folder on the game server so that I can automatically publish game information on the web.

I have tried using the following command:

```
root@Kalle-Ubuntu:/home/kalle# sshfs -p 10 default@silvertejp.nu:/var/www/default/htdocs /home/kalle/server -d
default@silvertejp.nu's password: 
FUSE library version: 2.8.4
nullpath_ok: 0
unique: 1, opcode: INIT (26), nodeid: 0, insize: 56
INIT: 7.16
flags=0x0000007b
max_readahead=0x00020000
   INIT: 7.12
   flags=0x00000011
   max_readahead=0x00020000
   max_write=0x00010000
   unique: 1, success, outsize: 40

```While sshfs is running, the directory is mounted, but there is a problem with permissions. If I run the ls -l command as root, I can see the permissions:
```
drwxrws--- 1  5002  5003   4096 2011-05-03 20:15 server
```However, when I use my normal user account I can't cd to the folder and ls -l shows this:
```
d????????? ? ?     ?          ?                ? server
```When there is nothing mounted in the folder, the permissions are as I would expect them to be:
```
drwxr-xr-x 2 kalle kalle   4096 2011-05-04 09:28 server
```Why are they changed when I mount? How can I fix this? Is sshfs the right tool or should I use something different?

---

### Post by spikoley on 2011-05-06
Try using the built in sshfs in Nautilus.

Places> Connect to Server.  Put in your settings and check Add Bookmark.

Let us know if you still have the same issue.

---

### Post by jcreigh on 2011-07-26
By default sshfs (well, actually FUSE) doesn't allow any users other than the user that mounted the filesystem to access it, regardless of permissions. You need to use the "allow_other" option when mounting the filesystem. In addition, the user and group IDs are unlikely to sync up between your two systems, so you may need to make use of the uid and gid options to map the mount to whatever local user or group needs to have access to the files.

So your revised "sshfs" run might look like:

```
$ sshfs -p 10 -o allow_other,uid=1234,gid=5678 default@silvertejp.nu:/var/www/default/htdocs /home/kalle/server -d
```

(replacing the actual value for uid and gid as appropriate, of course)

---

### Post by megabuffen on 2011-09-30
I was wondering, when I use the built-in function "connect to server", where is it actually mounted? When i connect to my server using SFTP, it shows up on my desktop just fine, but I can't access it from withing a program. Is there some way to find the real mount point so that I can access it with, for example, sync software?

---

### Post by temporizer on 2011-12-04
> **megabuffen said:**
> I was wondering, when I use the built-in function "connect to server", where is it actually mounted? When i connect to my server using SFTP, it shows up on my desktop just fine, but I can't access it from withing a program. Is there some way to find the real mount point so that I can access it with, for example, sync software?

AFAIK, it is mounted to ~/.gvfs

---

### Post by collisionystm on 2011-12-04
you want to mount it with fstab

if you mount it with a 'bookmark' it will only mount after you select it from nautilus

if you want to the share to mount automatically you need to use fstab

[http://www.youtube.com/watch?v=K7OCC-laRpc](http://www.youtube.com/watch?v=K7OCC-laRpc)

---

### Post by megabuffen on 2012-04-04
I have added the following to a "Custom application launcher".
```
sshfs -p 10 kalle@silvertejp.nu:/ ~/mount/Silvertejp
```
This works.

---


---
title: "sshfs is mounting filesystems as another user Ubuntu 10.04"
date: 2012-04-18
forum: General Help
---

### Post by XxionxX on 2012-04-18
So I am trying to mount a folder from another computer in my  LAN, and I am able to ssh without any issues. But, I am unable to make  any changes when I access the mounted folder.
  This is what I have done so far:
  Install:
```
$sudo apt-get install sshfs $sudo modprobe fuse $sudo adduser <username> fuse 
$sudo chown root:fuse /dev/fuse
$sudo chmod +x /dev/fuse $mkdir ~/remoteser
```And when I access the remote folder via sshfs:
  ```
$sshfs -o idmap=user <username>@<ipaddress>:/home/user ~/remoteserv
```   The output of becomes:
  ```
$~/remoteserv$ ls -l
total 60
drwxr-xr-x 1 <notmyusername> <notmyusername> 4096 2012-04-13 21:54 Desktop
drwxr-xr-x 1 <notmyusername> <notmyusername> 4096 2012-04-10 13:05 Documents
drwxr-xr-x 1 <notmyusername> <notmyusername> 4096 2012-04-17 19:06 Downloads
drwxr-xr-x 1 <notmyusername> <notmyusername> 4096 2012-04-13 21:55 Music
drwxr-xr-x 1 <notmyusername> <notmyusername> 4096 2012-04-03 15:07 Pictures
... more of the same
```   I am unable to access any of the files properly because sshfs is  mounting the files under my wife's username! I have no idea why, and I  feel like I have made a large mistake somewhere. Is there some  configuration file which I need to tweak somewhere? I can't seem to find  anything on the manpage :/
  I even tried an -o allow_other option when I mounted the desired file, but the desired file was still mounted under my wife's username! What is going on?

---

### Post by papibe on 2012-04-19
Hi XxionxX.

Unfortunately I can't test this at the moment, but my first guess would be this: by any chance the remote user's and local user's UID don't match?

You can check it running this on both machines:
```
echo $UID
```
Regards.

---

### Post by hwttdz on 2012-04-19
I think the simple way to address this is feeding sshfs 
-o uid=youruid,gid=yourgid

I think it's slightly preferable to use idmap=user, but that requires the uids to match up between machines.

---

### Post by XxionxX on 2012-04-24
Thanks guys, that did the trick!

So this is what I did:

```

echo $UID

```

output

```

1000

```

So I input

```

sshfs -o uid=1000 <user>@<ipaddress>:/home/user ~/remoteserv

```

And it mounted with the proper permissions!

Although I have a few questions. What is the uid? What is the gid? I did an 'echo $GID' and it returned a blank string, is that bad?

Once again, thanks for the help guys! ):P

---

### Post by hwttdz on 2012-04-25
Sorry for the tardy reply, uid and gid stand for "user id" and "group id", so these are sort of real identifiers of your user.  For instance in file permissions, everything on your hard disk is stored as being owned by your user id, and the user id->username mapping is done by the system.  So if you were to move your hard disk to a different machine where you had a different id and no user had the id of those files the system would not know who the owner is, and in say an ls listing it would just show the numeric id. 

If you're interested in knowing the id of a user just do "id username" and it will tell you, the uid and the gid for all the groups the user belongs to (the gid of the primary group is the users gid).

---


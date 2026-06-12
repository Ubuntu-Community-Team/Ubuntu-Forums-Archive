---
title: "fstab mount hd for all users"
date: 2011-02-07
forum: General Help
---

### Post by ryezs on 2011-02-07
Hi
i have a problem with my hd´s. I have two users on my Ubuntu 10.10 one administrator and on user. I have three hd's that I mount with fstab like this:

/dev/sdb1 /media/hdd1 xfs default,noatime,user 0 2
/dev/sdc1 /media/hdd2 xfs default,noatime,user 0 2
/dev/sdd1 /media/hdd3 xfs default,noatime,user 0 2

that works for one account the hd's gets mounted at boot and can read and writ on them if the hd's is formatted under that account and that account take ownership over them.

if i don't take ownership over the file system on the hd's both accounts will have the hd's mounted at boot but will only have read rights on them.

I need to mount them at boot and both the user and the admin should have read and write rights

---

### Post by vanadium on 2011-02-07
For partitions that use a file system that supports linux permissions, you do not regulate permissions through /etc/fstab. Set appropriate permissions on the files and directories that are on the partition.

What did you want to achieve with the "user" option?

---

### Post by ryezs on 2011-02-07
I had the "user" option to mount the hd's as a normal user but that only works if I don't have auto mount as default I guess, I don't have it there anymore just forgot to remove it. I will try with permissions

---

### Post by ryezs on 2011-02-08
> **vanadium said:**
> you do not regulate permissions through /etc/fstab. Set appropriate permissions on the files and directories that are on the partition.

I have tried to set the permissions but i must be doing something wrong cause the hd's won't mount for any user. I have found that umode and mask can be used in fstab and have tried to add both.

/dev/sdb1 /media/hdd1 xfs default,noatime,mode=777  0 2
/dev/sdc1 /media/hdd2 xfs default,noatime,mode=777  0 2
/dev/sdd1 /media/hdd3 xfs default,noatime,mode=777  0 2
or
/dev/sdb1 /media/hdd1 xfs default,noatime,umask=000 0 2
/dev/sdc1 /media/hdd2 xfs default,noatime,umask=000 0 2
/dev/sdd1 /media/hdd3 xfs default,noatime,umask=000 0 2

but when i have either of them the hd's won't mount for any user. I don't really care about the security on the hd's they can have full read write for all users that not a problem. 

if I'm not wrong about the umask the 000 should give read write and execute to all users right

---

### Post by Hawkoon on 2011-02-08
From what I know the umask option is used with DOS partitions (which dont support file owner and access permission flags). 

Since you have an XFS partition, get rid of umask and mode parameters in fstab. Then follow vanadiums advice, that is you control WHO can access / WHAT kind of access by setting the appropriate ownership flags (with chown) and file mode bits (with chmod).

---

### Post by vanadium on 2011-02-08
Indeed, I repeat;

[quote=Vanadium]
Originally Posted by vanadium View Post
you do not regulate permissions through /etc/fstab. Set appropriate permissions on the files and directories that are on the partition.
[/QUOTE]

To set ownerships/permissions, you can use the terminal (chmod, chown). You can also use nautilus, but it has to run with root privileges: the command "gksudo nautilus" will give you a nautilus window with root permissions.

Before attempting to set permissions, make sure your drives are properly mounted again as before.

---

### Post by ryezs on 2011-02-08
ok now it works thank you very much for the help

---


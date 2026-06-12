---
title: "Can't mount remote shared drive"
date: 2010-07-26
forum: General Help
---

### Post by KLStringer on 2010-07-26
I'm trying to mount an external drive that's in use on another server so I can copy it's contents to it's new home. When I try to mount it with:

```
mount -t smbfs //terrasan/F /media/recordings/mnt -o user=%username%,pass=%password%,domain=%domainname%
```I get

```
mount: wrong fs type, bad option, bad superblock on //terrasan/F,
missing codepage or helper program, or other error 
(for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program)
In some cases useful info is found in syslog - try
dmesg | tail or so

```I add the |demsg | tail and I get a message saying that smbfs is depreciated use cifs, so i look up what that is and how to use it.

Then I try

```
root@webserver:/media/recordings# mount -t cifs -o guest //terrasan/F /media/recordings/mnt |dmesg | tail
```And get

```

[249423.310424] Slow work thread pool: Starting up
[249423.310884] Slow work thread pool: Ready
[249423.315942]  CIFS VFS: cifs_mount failed w/return code = -22
[249567.564549]  CIFS VFS: No username specified
[249567.564797]  CIFS VFS: cifs_mount failed w/return code = -22
mount: wrong fs type, bad option, bad superblock on //terresan/F,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```So I try 

```

mount -t cifs -o username=server_user,password=secret //192.168.1.108/F /media/recordings/mnt |dmesg | tail
```and get

```

[249636.925542]  CIFS VFS: cifs_mount failed w/return code = -22

```I found this page [http://forums.fedoraforum.org/archive/index.php/t-177110.html](http://forums.fedoraforum.org/archive/index.php/t-177110.html) and tried the things they tried, still no joy so I find this page [http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs) and change the command from 

```

mount -t cifs .....

```to

```

mount.cifs
```and I get a message that smbfs isn't install (WTF not install, ok what ever) aptitude install smbfs.....done...try again
```

root@webserver:/media/recordings# mount.cifs //192.168.1.108/F /media/recordings/mnt -o user=%username%,password=%password%,domain=%domain% |dmesg | tail
[249567.564549]  CIFS VFS: No username specified
[249567.564797]  CIFS VFS: cifs_mount failed w/return code = -22
[249636.925293]  CIFS VFS: No username specified
[249636.925542]  CIFS VFS: cifs_mount failed w/return code = -22

```and it worked but I took all the time to write this as I was trying to figure out WTF was wrong so I'm posting it any way in case some else has the same problem.

---

### Post by KLStringer on 2010-07-26
Here's a question from this mounted drive I want to copy over all the files in the Recordings folder and keep the sub directories intact, when I do:

```

cp -R /media/recordings/mnt/Recordings /media/recordings

```It copies everything and keeps the tree intact but its all in /media/recordings/Recordings.

How do I get it to copy everything in the Recordings folder to /media/recordings, keep the sub directories in Recordings intact, but not in a redundant Recordings folder?

---

### Post by KLStringer on 2010-07-26
Answer

```

cp -R /media/recordings/mnt/Recordings/* /media/recordings

```

---


---
title: "Problems mounting Windows share using /etc/fstab"
date: 2010-03-18
forum: General Help
---

### Post by utannheim on 2010-03-18
Using Nautilus I can connect to a Window Share using a URL like the following: 
```
smb://MYDOMAIN;myuser@server.domain.com/shareName/
```

My goal is to be able to mount this same share via the command line as the current user (without sudo) and without the need to enter credentials. So I modify /etc/fstab as follows:
```
//server.domain.com/sharename /mnt/server.domain.com/sharename smbfs noauto,user,rw,credentials=/home/localUser/.smbcredentials,uid=1000,gid=1000
```
I create the local directory /mnt/server.domain.com/shareName and I create the credentials file as follows:
```
username=myuser
password=p4ssw'd

```

For some reason I keep getting "mount error(13): Permission denied." Any time I get further then this, the permissions on the directory 055 instead of 755 as I would normally expect. 

Any idea why nautilus can connect, but via the command line I cannot? What am I doing wrong?

---

### Post by Iowan on 2010-03-18
A couple of How-To's that might be helpful:
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")

---


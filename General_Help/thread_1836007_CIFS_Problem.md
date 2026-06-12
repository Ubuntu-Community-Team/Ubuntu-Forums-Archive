---
title: "CIFS Problem"
date: 2011-08-30
forum: General Help
---

### Post by jrmolinaq on 2011-08-30
Hi, I use ulteo program to edit documents and I have a problem.

I had mounted a webdav in a directory and ulteo mounts this directory in other location with CIFS, and it works fine. Now I need to mount the first but in CIFS.

When I mount this with CIFS, I can open the documents of my directory ("/opt/ulteo/var/lib/ulteo/ovd/slaveserver/fs/Profile/Documents") in console. When ulteo mounts its CIFS in "/opt/ulteo/mnt/ulteo/ovd/" the files mounted have all permissions but when I try to open a document in console I have the error "[Permission Denied]".

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201106&stc=1&d=1314712745[/IMG]


The first "ls -l" command is my CIFS mount. The second "ls -l" is the cifs mount made by ulteo.

The first "vi" opens the document in my mount and the final line produces an "Permission Denied" error.

I use ulteo 3 rc6 in linux 10.10.

My webdav mount was:
```
sudo mount -t davfs -o noauto,nodev,dir_mode=777,noexec,file_mode=777,_netdev,rw,nosuid //server/DirToMount/ /opt/ulteo/var/lib/ulteo/ovd/slaveserver/fs/xxProfilexx/Documents
```


My Cifs mount is:
```
sudo mount -t cifs -o rw,iocharset=utf8,username=MyLogin,password=MyPassword,dir_mode=0777,file_mode=0777,lfs //server/DirToMount/ /opt/ulteo/var/lib/ulteo/ovd/slaveserver/fs/xxProfilexx/Documents
```


And the mount made by ulteo is:
```
mount -t cifs -o username=%s,password=%s,iocharset=utf8,uid=%s,gid=0,umask=077 //%s/%s %s"%(self.profile["login"], self.profile["password"], self.session.user.name, self.profile["server"], self.profile["dir"], self.profile_mount_point)
```


Excuse my bad english. :confused: Can somebody help me? thanks.

---


---
title: "Cutting files in a share folder in Ubuntu from windows"
date: 2006-05-27
forum: General Help
---

### Post by Dearhell on 2006-05-27
I have a shared folder in my ubuntu machine, and I want to cut files in that folder from another machine of my lan with Windows XP

I have set this folder with read/write permissions in smb.conf

I can copy files from my windows machine to my ubuntu shared folder without any problem, but I can't cut the files on that folder from the windows machine.

I have set the permissions of the folder and the files with chmod 777

Any idea?

smb.conf:

```
[Incoming]
comment = Incoming
path = /home/casa/.aMule/Incoming
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
```

Incoming folder permissions:

```
drwxrwxrwt  2 admin admin    4096 2006-05-27 19:50 Incoming
```

---

### Post by Dearhell on 2006-05-27
No one knows about this? :sad:

---


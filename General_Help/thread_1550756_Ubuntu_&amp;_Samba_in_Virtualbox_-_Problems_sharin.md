---
title: "Ubuntu &amp; Samba in Virtualbox - Problems sharing folders w/ Win7"
date: 2010-08-11
forum: General Help
---

### Post by superseby on 2010-08-11
Hi everyone,
I am having a problem and can't seem to find a solution by myself. 

This is my setup:

Win7 x64 host with Virtualbox installed running Ubuntu 32bit guest OS.  I have Samba installed and I am sharing a folder to have read access from Win7. 

The folders I tried to share (here 'folder1-3') have been added in the conf.d in etc/samba/ like this - I used these 3 variants, all showed the same problem:

```

[folder1]
path = /data/mp3
read only = yes
guest ok = yes
admin users = admin

[folder2]
path = /data/testing
read only = no
guest ok = yes
admin users = win7computername\admin
browseable = yes

[folder3]
   path = /data/ogg
   public = yes
   only guest = yes
   writable = yes
   printable = no
   browseable = yes

```

While I can connect to all of these from Windows and map them in Windows Explorer, I am unable to serve those files using my FTP server that is running on Windows.  The folders simply do not show up when I add them as folders to serve in FileZilla.

The problem I am assuming is causing this is the fact that FileZilla is running as a different instance and not on an administrator level.  I cannot however add any users to the permissions list on the Windows side.  The 'security' tab of the mapped folder shows the following Users:

EVERYONE
root (Unix user\root)
root (Unix group\root)

None of these seem to have rights to 'read' or 'list folders', the only permissions listed are 'special permissions'.  

Does anyone know how I can assign the group EVERYONE privileges to read and list files and then be able to serve this shared folder through my Windows-run FTP server?

Sigh, complicated. :popcorn:

Any help is appreciated!

---

### Post by superseby on 2010-08-12
bump :)

---


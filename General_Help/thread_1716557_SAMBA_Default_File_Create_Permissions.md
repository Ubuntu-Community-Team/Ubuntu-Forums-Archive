---
title: "SAMBA Default File Create Permissions"
date: 2011-03-28
forum: General Help
---

### Post by imstarboard on 2011-03-28
Files saved on our ubuntu server via samba server are all being created/saved as read only (-rwxr--r--).  The users are MAC Users who are connecting via finder.

I have taken 2 steps:

First I added the lines "umask 0000" to the .bashrc files in the users' home directories.

Second, I have modified the /etc/samba/smb.conf file such that I set "create mask = 0000" and also "directory mask = 0000" but the files are still being created as "-rwxr--r--".

Thanks!

---

### Post by imstarboard on 2011-04-04
Can anyone assist here?  

I have played with the file masks in smb.conf and can't get any different response.  I have restarted samba, and even the server.  Can anyone help here?

Thanks :D

---


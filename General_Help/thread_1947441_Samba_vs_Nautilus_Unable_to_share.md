---
title: "Samba vs Nautilus Unable to share"
date: 2012-03-26
forum: General Help
---

### Post by tman001 on 2012-03-26
I am running Ubuntu 10.10 as a server, mainly SMB network storage.
 
The system has been running for a year+
 
I had to re-do my raid, where the shares are located. I wanted access to some files while I was re-builting the array. I used nautilus to share the folder, the perm shares were done in smb.conf I could see the new share, but could not access it. I just used a usb key and didn't worry about it. Now that the raid is up and the data has been transfered back I cannot access my perm shares. Nautilus has changed something and I'm not sure what has changed.
 
here is the output from testparam -s
 
[global]
workgroup = HOMEBASE
server string = %h server (Samba, Ubuntu)
map to guest = Bad User
obey pam restrictions = Yes
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
username map = /etc/samba/smbusers
unix password sync = Yes
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
usershare allow guests = Yes
panic action = /usr/share/samba/panic-action %d
 
[Backup]
comment = Backup Share
path = /srv/samba/share/backup
read only = No
create mask = 0755
 
[Server]
comment = Server Share
path = /srv/samba/share/server
read only = No
create mask = 0755
 
net usershare info --long
 
Shows Nothing
 
I have been playing with smb.conf
 
Windows states cannot find //Tishku/Server, when I diagnose windows states the server is there but the shares are not.
 
Any help would be appriciated

---

### Post by Morbius1 on 2012-03-26
Your smb.conf looks factory fresh to me. The shares you created in Nautilus don't impact smb.conf itself since the shares are defined someplace else but it does do one thing that the classic way does not - it automatically changes permissions on the target folder.

So depending on how you configured the nautilus shares it may have automatically done a "chmod 0777" . Of course that would have made things better not worse as far as access.

When you run the following command in the server does it list all the shares or do you get errors:
```
smbtree
```

---

### Post by tman001 on 2012-03-26
Solved
 
smbtree looked fine.
 
Started with clean smb.conf, no change
 
Cleared logs and tried again, was getting an encrypted filesystem error
 
Chk'd permissions, found it was the permissions for /share/ (mount point for the array)
 
Thx for the response

---


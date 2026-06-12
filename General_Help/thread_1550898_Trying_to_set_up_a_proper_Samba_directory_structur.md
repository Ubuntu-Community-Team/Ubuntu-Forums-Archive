---
title: "Trying to set up a proper Samba directory structure"
date: 2010-08-11
forum: General Help
---

### Post by iselfe on 2010-08-11
Hi all, first time poster long time reader.

Here is my set-up:

I'm  running samba version Version 3.0.33.  My smb.conf file looks like this  -- names have been omitted to protect the innocent.  


[global]
        workgroup = workgroup
        netbios name = smbserver
        security = user
        load printers = No
        default service = global
        path = /share
        username map = /etc/samba/smbusers
[share]
        writeable = yes
        admin users = user1 user2
        path = /share/share
        force user = root
        valid users = user1 user2
        public = yes
;       available = yes
[user1]
        writeable = yes
        admin users = user1
        path = /share/users/user1
        force user = root
        valid users = user1
        public = yes
;       available = yes
[user2]
        writeable = yes
        admin users = user2
        path = /share/users/user2
        force user = root
        valid users = user
        public = yes
;       available = yes

The problem is this... When I first log into the smbserver, I see 3 things;  share, user1, user2.  What I **want to**  see is share and users and make that users directory split off into all  my named users.  It's these directories (share/users/user1,  share/users/user2, etc....)  that I want to see in my directory  structure when I log in.  Any help would be greatly appreciated.

---


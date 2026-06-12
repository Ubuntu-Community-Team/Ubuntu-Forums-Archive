---
title: "Unable to access Samba4 shares from Vista"
date: 2010-08-02
forum: General Help
---

### Post by thaddicus on 2010-08-02
Ok, I'm just about at my wits end with configuring samba shares.  Here's a little color on the issue... I've configured Samba 4 on a bare Ubuntu server running lucid lynx.  I've chmodded (777) each share that I want to access, configured smb.conf file to allow access to each share for a local user, and added the username with sudo smbpasswd.  However, each time I try to access the shares from Windows, I'm prompted for credentials.  No matter what I enter I'm not allowed to access.  Below is what smb.conf looks like.  Also note that get a ton of 'unknown parameter encountered' messages when restarting samba.  Any help would be greatly appreciated.

[global]
workgroup = *My Domain Name*
server string = %h server (Samba, Ubuntu)
dns proxy = no
security = share
encrypt passwords = true
map to guest = bad user
guest ok = yes

[share1]
comment = share1
path = /home/xbmc/videos/share1
writable = yes
printable = no
create mask = 0777
directory mask = 0777
valid users = xbmc

[share2]
comment = share1
path = /home/xbmc/videos/share2
writable = yes
printable = no
create mask = 0777
directory mask = 0777
valid users = xbmc

---


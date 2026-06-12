---
title: "Can't Access SMB Server By IP, NetBIOS Only"
date: 2009-12-29
forum: General Help
---

### Post by NaughtyusMaximus on 2009-12-29
I have an Ubuntu 9.10 server, running samba as a domain member.  For some reason, I can access the shares without issue when I use the netbios name (from WinXP clients), but going directly to the ip will just time out.  I've searched around and found people with the opposite problem, but never this way.  Any thoughts?

```
#/etc/samba/smb.conf
[global]


workgroup = MYDOMAIN
realm = MYDOMAIN.LOCAL
netbios name = sl-012
server string = %h server
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = ADS
domain master = no
idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash
template homedir = /mnt/data/%D/%U
winbind enum groups = yes
winbind enum users = yes
winbind use default domain = yes
winbind separator = +
usershare allow guests = yes
```

---


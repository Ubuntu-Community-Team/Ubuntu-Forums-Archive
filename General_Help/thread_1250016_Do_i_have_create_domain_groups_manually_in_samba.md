---
title: "Do i have create domain groups manually in samba??"
date: 2009-08-26
forum: General Help
---

### Post by Avinash.Rao on 2009-08-26
Dear All,

Ubuntu 8.04 Server 64-bit edition
Samba 3.0.28a
All OS updates installed.

I have configured samba as PDC, below is my smb.conf file. I have gone through the samba documentation. My question is when samba is configured as a PDC, its equal to Windows NT 4.0 domain, but the domain groups don't exits? 

root@human:~# wbinfo -g
BUILTIN\administrators
BUILTIN\users

root@human:~# net rpc group list 
Password:
Administrators
Users

I don't see Domain Users/Admins/Guests groups? Do i have to create them manually in samba? 



```
[global]

    workgroup = abc
    server string = Samba for abc
    log level = 1
    interfaces = eth0
    ;bind interfaces only = True

    log file = /var/log/samba/log.%m
    max log size = 1000

    domain logons = yes
    os level = 65
    prefered master = yes
    domain master = yes
    local master = yes

    add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody %u
    dns proxy =No
    hosts allow = 127. 100.100.100.
    wins support = Yes
    passdb backend = tdbsam
    
    winbind uid = 10000-20000
    winbind gid = 10000-20000
    winbind use default domain = yes    
    encrypt passwords = true
    ; winbind separator = \
    idmap uid = 1-20000
    idmap gid = 1-20000
    template shell = /bin/bash
    ;smb passwd file = /etc/samba/smbpasswd
    security = user
    netbios name = human
    username map = /etc/samba/smbusers   

[homes]
    comment = Home Dir
    read only = NO
    browseable = NO
    valid users = %S
    path = %H
    directory mask = 0700
    create mask = 0700

[share]
    comment = Common Share
    path = /export
    create mask = 0765
    read only = NO

```

---


---
title: "Samba share problem, if username is the same as groupname"
date: 2012-06-29
forum: General Help
---

### Post by imochen on 2012-06-29
Hello,

I have a little understanding Problem:

I have a Samba fileserver with LDAP authentication (via windbind) on a Ubuntu 12.04 Server. The LDAP Server runs on a single Server with Ubuntu 12.04 too.
In the LDAP directory users are assigned to groups, which are also permission groups for the shares on the fileserver, e.g. group verwaltung = share verwaltung.

I created a user for a test, which has the same name as the group, so it exists a user called verwaltung like the group, but the user isn't in it!
Later I tried to access the share Verwaltung on the fileserver, but I get the message access denied.
I checked the permissions of the share and tried to set the rights again with chown -R nobody:verwaltung, but I get the message that this group don't exist. So I checked this with getent group, which said the group is there and ls -al at the share shows the right group too.
After I was looking around on the system a bit, I decided to delete the user I have create before and one secound later I can access the share.

Why is there a problem when a user have the same name as a group, because linux work with the UID's and GID's, or I am wrong?

The global part of my smb.conf:
```
[global]
        workgroup = OFFICE
        netbios name = smb01
        server string = smb01 (%h)
        invalid users = root
        time server = no
        map to guest = Bad User
        dns proxy = No
        log level = 0
        log file = /var/log/samba/log.%m
        max log size = 1024
        syslog = 0
        domain master = no
        local master = no
        preferred master = no
        display charset = ISO8859-15
        dos charset = CP850
        unix charset = utf8
        load printer = no

###AUTH###

        security = domain
        encrypt passwords = true

###WINBIND###

        socket options = SO_KEEPALIVE IPTOS_LOWDELAY TCP_NODELAY
        idmap backend = tdb
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        idmap config OFFICE : backend = rid
        idmap config OFFICE : range = 10000 - 20000
        winbind separator = +
        winbind enum users = yes
        winbind enum groups = yes
        winbind cache time = 10
        winbind use default domain = yes
```

My nsswitch.conf:
```
passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```


Thank you und greetz
Sebastian

---

### Post by wyliecoyoteuk on 2012-06-29
Samba is a windows SMB filesystem, overlaid on top of the Linux filesystem, with separate users, groups, and different rules for permissions, so you have Samba users and Linux users mapped to each other, but separate.
SMB requires unique names for users and groups, I think.

---

### Post by luvshines on 2012-07-07
I have a test setup for Samba with LDAP (no winbind) and it works fine

[root@mytest ~]# getent passwd authuser1
authuser1: x:2220:3000:user one:/bin/bash:/home/authuser1

[root@mytest ~]# getent group authuser1
authuser1:*:3000:authuser1
------
Tested this with CIFS access using (chmod 700, chown authuser:root) and (chmod 070, chown root:authuser1)

---

### Post by wyliecoyoteuk on 2012-07-08
winbind may well be the issue.

---


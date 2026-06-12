---
title: "Unable to delete files from SMB share"
date: 2009-11-16
forum: General Help
---

### Post by Buurman on 2009-11-16
Given a share named "testshare", a user named "testuser" which is in the (default AD) group "domain users" and also in the group "testgroup" and the smb.conf below, 
the user **can not** delete files (but **can** delete directories) from \\testmachine\testshare,
**can not** delete files (but **can** delete directories) from existing directory \\testmachine\testshare\foo, 
but **can** delete files and directories from any directories created by the user.
For example if the user creates the directory \\testmachine\testshare\new, it can create and delete files and directories from \\testmachine\testshare\new.

In the directory structure shown below, the user **can** delete \\testmachine\testshare\New Folder\New Text Document.txt
but **can not** delete any other files.
Why is this? :)

Edit: Ubuntu 9.04 server, samba version 2:3.3.2-1ubuntu3.2, winbind version 2:3.3.2-1ubuntu3.2

smb.conf:

[global]
    # general options
    workgroup = COMPANYNAME
    netbios name = MACHINENAME
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    mangled names = no
    map read only = Permissions
    store dos attributes = no
    dos filemode = no
    acl map full control = True
    preferred master = no

    # winbindd configuration
    winbind separator = +
    winbind use default domain = yes

    # idmap uid and idmap gid are aliases for
    # winbind uid and winbid gid, respectively
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    winbind enum users = yes
    winbind enum groups = yes
    template homedir = /home/%D/%U
    template shell = /bin/bash

    security = ads
    encrypt passwords = yes
    realm = companyname.nl
    # this handles the "ads server = " directive as well -- Enigma
    password server = pdc.companyname.nl
    invalid users = root

    # Log options
    log file = /var/log/samba/log.%m
    syslog = 0
    log level = 1 acls:10 auth:10 vfs:10
    max log size = 1000

[testshare]
    path = /var/local/testshare
    valid users = companyname+testuser @companyname+testgroup
    force user = companyname+testuser
    create mask = 660
    force create mode = 660
    directory mask = 770
    force directory mode = 770
    writable = yes


Directories:
root@testmachine:/var/local/testshare# ls -alkh
total 16K
drwxrwxr-x 7 testuser some_other_group 4.0K 2009-11-16 11:03 .
drwxr-xr-x 6 root     root             4.0K 2009-10-22 16:18 ..
drwxrwx--- 2 testuser domain users     4.0K 2009-11-16 11:03 New Folder
-rw-rw---- 1 testuser domain users        0 2009-11-16 11:00 New Text Document.txt
drwxrwx--- 2 testuser testgroup        4.0K 2009-11-16 10:59 foo


root@testmachine:/var/local/testshare# ls -alkh *
-rw-rw---- 1 testuser domain users     0 2009-11-16 11:00 New Text Document.txt

New Folder:
total 8.0K
drwxrwx--- 2 testuser domain users     4.0K 2009-11-16 11:08 .
drwxrwxr-x 7 testuser some_other_group 4.0K 2009-11-16 11:03 ..
-rw-rw---- 1 testuser domain users        0 2009-11-16 11:08 New Text Document.txt

foo:
total 48K
drwxrwx--- 2 testuser testgroup        4.0K 2009-11-16 10:59 .
drwxrwxr-x 7 testuser some_other_group 4.0K 2009-11-16 11:03 ..
-rw-rw---- 1 testuser testgroup         37K 2009-11-16 08:57 testfile.dat

---


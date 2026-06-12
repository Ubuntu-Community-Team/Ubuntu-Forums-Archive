---
title: "Problem setting up SAMBA client for the /etc/password? Not working :("
date: 2010-01-29
forum: General Help
---

### Post by frenchn00b on 2010-01-29
I have installed winbind, portmap, and samba/smbclient packages on the workstation linux ubuntu , which is intended to be client to samba for /etc/password attached to the server.


At boot nothing changed, and the /etc/password is not attached to samba. So my passwords are stil the local of hte client, and not the server.

This is my config of the client workstation:

cat /etc/nsswitch.conf 
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```


 
 cat /etc/samba/smb.conf
```
[global]
   guest account = nobody
   invalid users = root
   encrypt passwords = yes
   security = ads
   password server = 192.168.1.2
   workgroup = WORKGROUP
   server string = %h server (Samba %v)
   preserve case = yes
   short preserve case = yes
   unix password sync = yes

[homes]
  comment = Home Directories
  read only = No
  create mask = 0700
  directory mask = 0700
  browseable = no





```

---

### Post by frenchn00b on 2010-01-29
```


# cat /etc/samba/smb.conf


[global]
   guest account = nobody
   invalid users = root
   encrypt passwords = yes
   security = server
   password server = 192.168.10.100
   workgroup = WORKGROUP
   server string = %h server (Samba %v)
   preserve case = yes
   short preserve case = yes
   dead time = 0
   wins server = 192.168.10.100
   name resolve order = lmhosts host wins bcast
   dns proxy = yes
   max log size = 1000


```


```

#cat /etc/nsswitch.conf 

passwd:     files winbind
group:      files winbind
hosts:      files dns wins





```

I get the folloowing error:

```
 net rpc join 
cannot join as standalone machine

```

---


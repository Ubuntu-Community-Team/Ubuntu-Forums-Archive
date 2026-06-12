---
title: "Ubuntu 10.04 cant write to samba share"
date: 2010-07-19
forum: General Help
---

### Post by mr42O on 2010-07-19
I have installed ubuntu 10.04 and installed samba but can write to samba share.
 
my config look like this
 
```
# Samba config file created using SWAT
# from UNKNOWN (192.168.1.102)
# Date: 2010/07/19 13:57:02
 
[global]
    workgroup = MSHOME
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    obey pam restrictions = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    panic action = /usr/share/samba/panic-action %d
    invalid users = root
 
[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No
 
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
 
[1TB]
    comment = Seagate 1TB
    path = /mnt/1tb
    read only = No
    create mask = 0700
    guest ok = Yes
```
 
I dont want to use password to connect to samba.

---


---
title: "Samba issue with sharing directories on NTFS/FAT32 (Mounted Drives) ???"
date: 2011-03-12
forum: General Help
---

### Post by chethan123 on 2011-03-12
Hi guys,

I have some strange problems with Samba server. I am using **samba Version 3.5.4 **on **Ubuntu 10.10**. 

I have two windows-xp machines, one on VirtualBox on Ubuntu and another office laptop. Windows machine on VBox has no issues in accessing the shared folders, but the laptop is not able to access all the shared content. 

The issue faced on laptop is => 

Shared folders on Ext3 drives have no issues in accessing, but the contents shared on NTFS and FAT32 drives (mounted ones) are not accessible. When I try to open the shared folder, it asks for user name and password, but doesn't accept when I provide it. (even if I provide admin login details!!!). 

I changed workgroup value to the domain_name in office laptop, but still the problem persists... :(

Here is the smdb.conf I am using... 

> 

[global]
        workgroup = XXX.XXX.ORG    
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        guest ok = Yes

[homes]
        comment = Home Directories

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = No
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Samba server's CD-ROM
        path = /cdrom
        force user = nobody
        force group = nobody
        locking = No


Workgroup Was defined as "HOMENET" before, changed it to domain name on the office laptop thinking it was the problem, but for no avail :(

Thanks in advance :)

Regards

---


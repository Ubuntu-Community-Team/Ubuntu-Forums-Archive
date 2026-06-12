---
title: "Samba - Cannot connect to any shares anymore"
date: 2006-03-06
forum: General Help
---

### Post by alterego125 on 2006-03-06
Hi Everyone,

Today my samba server has stopped accepting connections from my other two machines on my network. I've been running a samba server on breezy for the last few months without any problems.

When I type testparm I get:
> root@user:/home/user# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[user]"
Processing section "[Incomming]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


I hit enter and get:

> # Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[dstahan]
        comment = user's home directory
        path = /home/user
        read only = No
        guest ok = Yes

[Incomming]
        path = /home/user/Incomming
        read only = No
        guest ok = Yes
root@dieters:/home/user# smbclient -L //192.168.15.100 -U user
Password:
Domain=[USER] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        print$          Disk      Printer Drivers
        user         Disk      user's home directory
        Incomming       Disk
        IPC$            IPC       IPC Service (user server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (user server (Samba, Ubuntu))
Domain=[USERS] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            IBM-D13F4691E4F


I haven't touched a singe thing on the system. I've tried restart the samba service as well. I've rebooted the box a couple of times, but now joy. I simply cannot access this from a windows machine.

Anyone have any ideas?

---

### Post by eeclark on 2007-05-30
Hate to do just a me too...but me too.

---


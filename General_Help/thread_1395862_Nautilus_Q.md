---
title: "Nautilus Q?"
date: 2010-02-01
forum: General Help
---

### Post by Tourdog on 2010-02-01
My gksu nautilus brings this up:

"displays nautilus: 2133  Warning ** No marshaller for signature of signal 'upload/download finished."
'
                                              "             2133                 "                        share create error'

Also:   As a result the "Desktop-File Browser" upon clicking its button, "Browse all local & remote disks & folders accessible from this computer.........   yields...

"Could not display "computer" locations."

What is the best/easiest way to get nautilus running smoothly?

I've got to get nautilus running or samba will not ever run fully.

TIA!

---

### Post by Monotoko on 2010-02-01
It seems from:
```
" 2133 " share create error'
```

That is is a problem with Samba, do you have samba installed, and what have you done already with it?

---

### Post by Tourdog on 2010-02-01
Thanks "monotoko" !

Here is what I get:

tourdog@PJK3:~$ dpkg -l | grep samba
ii  samba                                 2:3.4.0-3ubuntu5.4                                      SMB/CIFS file, print, and login server for U
ii  samba-common                          2:3.4.0-3ubuntu5.4                                      common files used by both the Samba server a
ii  samba-common-bin                      2:3.4.0-3ubuntu5.4                                      common files used by both the Samba server a
ii  samba-doc                             2:3.4.0-3ubuntu5.4                                      Samba documentation
ii  system-config-samba                   1.2.63-0ubuntu4                                         GUI for managing samba shares and users
tourdog@PJK3:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[tourdog]"
Processing section "[tourdog-1]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = tourdog
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    guest ok = Yes

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

[Music]
    comment = cpk's music
    path = /home/tourdog/Music
    valid users = tourdog
    read only = No

[tourdog]
    comment = tourdog's docs
    path = /home/tourdog
    valid users = tourdog
    read only = No

[tourdog-1]
    path = /home/tourdog
    valid users = tourdog
    read only = No
    browseable = No
    browsable = No
tourdog@PJK3:~$ 
tourdog@PJK3:~$ 

What do you think?

And, in "samba server menu" should "server settings" Authentication Mode (security) be ""user"" or ""share""  or ...?

---


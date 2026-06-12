---
title: "Join W2K-Domain with AD"
date: 2010-12-14
forum: General Help
---

### Post by Rigoletto on 2010-12-14
Hi,

i have installed 10.10 and Samba. 
If i run Samba with security = user, i can access shares with local created users.

Then i changed security = domain,
and joined successfuly the domain with "net rpc join -Uxxx@yyy".
I checked the AD-Server and see a new entry for the ubuntu-server under ad-computers. I used the normal "Administrator"-account.

Modified nsswitch.conf with:

```
passwd: files winbind
group:  files winbind
hosts:  files dns winbind
```and set "net setauthuser -U xxx%yyy" without error message.
I used the normal "Administrator"-account.

But "wbinfo -u" only lists the local users and not the from the domain,
and i cannot access a samba share.

testparm gives:
```

administrator@ubusrv:/etc/samba$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
        workgroup = EXCHANGE
        server string = %h server (Samba, Ubuntu)
        security = DOMAIN
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *pa                                                                    ssword\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        template shell = /bin/bash

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0775
        browseable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[public]
        comment = Allgemeine Daten
        path = /export/public
        valid users = %S
        read only = No
administrator@ubusrv:/etc/samba$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
        workgroup = EXCHANGE
        server string = %h server (Samba, Ubuntu)
        security = DOMAIN
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
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        template shell = /bin/bash

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0775
        browseable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[public]
        comment = Allgemeine Daten
        path = /export/public
        valid users = %S
        read only = No
administrator@ubusrv:/etc/samba$


```I reboot the ubuntu server but it does not slove the problem.
"net rpc testjoin" says all is ok.

Then i played around and see "sudo wbinfo -u" gives an error "Error looking up domain users".

Last lines from log.winbindd:
```

[2010/12/13 14:20:12,  0] winbindd/winbindd.c:1105(main)
  winbindd version 3.5.4 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2010/12/13 14:20:12.273814,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/12/13 14:20:25.315097,  0] winbindd/winbindd.c:195(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/12/13 14:26:08,  0] winbindd/winbindd.c:1105(main)
  winbindd version 3.5.4 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2010/12/13 14:26:08.992179,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/12/13 14:26:08.994836,  0] winbindd/winbindd_util.c:633(init_domain_list)
  Could not fetch our SID - did we join?
[2010/12/13 14:26:08.994851,  0] winbindd/winbindd.c:1246(main)
  unable to initialize domain list
[2010/12/13 14:33:37,  0] winbindd/winbindd.c:1105(main)
  winbindd version 3.5.4 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2010/12/13 14:33:37.012559,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/12/13 16:26:53.886310,  0] winbindd/winbindd.c:195(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/12/13 16:27:07,  0] winbindd/winbindd.c:1105(main)
  winbindd version 3.5.4 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2010/12/13 16:27:08.011559,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/12/13 16:42:01.630474,  0] winbindd/winbindd.c:195(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/12/14 09:23:54,  0] winbindd/winbindd.c:1105(main)
  winbindd version 3.5.4 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2010/12/14 09:23:54.897328,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2010/12/14 09:35:35.931813,  0] winbindd/winbindd.c:195(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=1)
[2010/12/14 09:46:09,  0] winbindd/winbindd.c:1105(main)
  winbindd version 3.5.4 started.


```
Last lines from log.winbindd-imap

```

[2010/12/14 09:26:48.975644,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/14 09:26:49.032326,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/12/14 09:26:49.032348,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/12/14 09:26:49.032360,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/14 09:35:35.930978,  0] winbindd/winbindd.c:195(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
[2010/12/14 09:57:40.364619,  1] winbindd/idmap.c:438(idmap_init_passdb_domain)
  Could not init passdb idmap domain
[2010/12/14 09:57:40.371348,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/12/14 09:57:40.371364,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/12/14 09:57:40.371373,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/14 10:06:27.517393,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/12/14 10:06:27.517427,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/12/14 10:06:27.517438,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/14 10:06:27.596573,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/12/14 10:06:27.596603,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/12/14 10:06:27.596613,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/14 10:06:27.665185,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/12/14 10:06:27.665214,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/12/14 10:06:27.665224,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/12/14 09:15:57.863421,  0] winbindd/winbindd.c:195(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)


```log.winbindd-dc-connect is empty.

Have no clue anymore what i should do and need a hint.

I got my information from to setup from here, in german: [http://gertranssmb3.berlios.de/output/](http://gertranssmb3.berlios.de/output/)

But i can used one in english to and make a new try if anyone have another actuall info.

greets
Rigoletto

---

### Post by Rigoletto on 2010-12-15
Hi,

after trying severall instructions to get this running i found one that worked for me.
Looks its only a little bit outdated: [URL="http://ubuntuforums.org/showthread.php?t=1253252"]http://ubuntuforums.org/showthread.php?t=1253252
[/URL] 
The only things that didnt run for me was restarting samba and winbind:

> /etc/init.d/winbind stop
/etc/init.d/samba restart
/etc/init.d/winbind start
Just go on with 

```
sh winbind stop
service smbd restart
sh winbind start
```Also i got an error with 
> winbind separator = +testparm says in will maybe stay in conflict with 
> winbind enum groups = yesI just comment the line out.

Hope this helps.

greetz
Rigoletto

---


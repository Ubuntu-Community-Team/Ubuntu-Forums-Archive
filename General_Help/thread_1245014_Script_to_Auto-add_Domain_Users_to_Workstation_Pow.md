---
title: "Script to Auto-add Domain Users to Workstation Power Users Group doesn't work"
date: 2009-08-20
forum: General Help
---

### Post by Avinash.Rao on 2009-08-20
Ubuntu 8.04 Server 64-bit Edition
Samba 3.0.28a configured as PDC
WinXP - SP2 clients

I following the instructions in [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetCommand.html#magicnetlogon](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetCommand.html#magicnetlogon) to add domain users to the winxp clients Power Users group.

```
#!/bin/bash

/usr/bin/net rpc group addmem "Power Users" "DOMAIN_NAME\$1" \
                   -UAdministrator%secret -S $2

exit 0

```

[netlogon]
comment = Netlogon Share
path = /export/samba/logon
root preexec = /etc/samba/scripts/autopoweruser.sh %U %m
read only = Yes
guest ok = Yes


But nothing happens when users login? 

Can anybody help
Avinash

---

### Post by Avinash.Rao on 2009-08-20
:confused:

---

### Post by Avinash.Rao on 2009-08-22
Has anybody done this before?? 
I have entered the correct password for adminsitrator which is on the WinXP machine?

???

---

### Post by Avinash.Rao on 2009-08-26
Has anybody in the world made root preexec = /etc/samba/scripts/autopoweruser.sh %U %m
work???

---

### Post by Avinash.Rao on 2009-08-28
Hi,

Ok, I tried to execute this manually and here's what is happening...

#net rpc group addmem "Administrators" "Domain Users" \ -S WINPCO32
Password:
Usage: 'net rpc group addmem <group> <member>

root@sunbox:~# net rpc group addmem "Power Users" "domain_name\username"
Password:
Could not add domain_name\username to Power Users: NT_STATUS_NO_SUCH_ALIAS

I replaced the domain_name with the name of the domain and username with the appropriate user account.

what does this error mean?

Thanks

---


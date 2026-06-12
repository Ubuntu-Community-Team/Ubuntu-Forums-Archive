---
title: "Samba browsing"
date: 2012-02-19
forum: General Help
---

### Post by bibble235 on 2012-02-19
Hi,

I have a 10.04 server with samba sharing on it. 

I have a laptop running currently 11.10 desktop and has ran 10.04 which using the shares using nautilaus. It does work but I do have to hit refresh several times at the various screens.

E.g. 
Network (Press refresh)
Workgroup (Press refresh)
Machine(Press refresh)
Shares(Press refresh)

It does not happen everytime but can happen more than once at any stage. This is a laptop using wireless but I can stream music from it without issue.

Happy to provide logs or put logging on.

On server 

2:3.4.7~dfsg-1ubuntu3.8

   workgroup = AAAAAA
   server string = %h server (Samba, Ubuntu)
   wins support = no
   dns proxy = no
   name resolve order = wins bcast lmhosts host
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   load printers = yes
   printing = cups
   printcap name = cups
   usershare allow guests = yes
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
   comment = Printer Drivers

---


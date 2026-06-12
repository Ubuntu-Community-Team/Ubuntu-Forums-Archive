---
title: "samba printing"
date: 2012-09-19
forum: General Help
---

### Post by stephan0h on 2012-09-19
Hi,

My wife wants to print from her windows-notebook on our printer attached on my linux pc. the box is running Ubuntu 12.04.1 LTS

Printing already worked, but since a few weeks it doesn't work anymore (I presume some side effect of a system upgrade.) I tried to fix it today, and it sort of partially works now: printing test-pages from windows works, all other documents don't work. Very strange.

I can see the print jobs in /var/spool/samba - files with length 0 bytes. I didn't find anything in the log files - the timestamp of the log files also isn't touched when printing.

This is what I have in smb.conf:

```
[global]
   workgroup = WKG
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
security = user
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
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   public = yes

```

Any ideas?

Thanks,
Stephan

---


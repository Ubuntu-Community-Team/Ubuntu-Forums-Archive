---
title: "Samba Swat help"
date: 2010-11-30
forum: General Help
---

### Post by cap10Ibraim on 2010-11-30
I created the following share "bob" 
```

# Samba config file created using SWAT
# from UNKNOWN (127.0.0.1)
# Date: 2010/11/30 13:51:17

[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
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

[bob]
	comment = ibrahim
	path = /home/ibrahim/ttt
	guest ok = Yes
	hosts allow = 192.168.1.100/255.255.255.0

```
but when i check the status I don't see any active share ?! 
```

version:	3.4.7
smbd:	running
nmbd:	running
winbindd:	not running

```
can I use the wlan0 ? do I need to configure this option ?
plus after activating the share I need to fill a field called 
Share Adress on other machine what would that adress be ?

---

### Post by cap10Ibraim on 2010-11-30
the task is done , now i'm streaming content from my laptop 
wireless interface to the sat receiver to the tv through a router connected to the receiver 
but forget about SWAT i used samba with 
Samba Server Configuration Tool 1.2.63
Copyright 2002 - 2005 (c) Red Hat, Inc. 
Copyright 2002 - 2004 (c) Brent Fox <bfox@redhat.com>
Copyright 2002 - 2004 (c) Tammy Fox <tfox@redhat.com>
Copyright 2004 - 2005 (c) Nils Philippsen <nphilipp@redhat.com>

A graphical interface for configuring SMB shares

---


---
title: "Failed to open samba share"
date: 2010-03-28
forum: General Help
---

### Post by 8301 on 2010-03-28
I have two computers at home both on Ubuntu 9.10.

Iam trying to get samba to work without password authentication. The smb.conf is the same on both machines beside netbios name and shares. 

testparm gives

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Home]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	interfaces = lo, eth0
	bind interfaces only = Yes
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

[Home]
	path = /home/htpc/
	force user = htpc
	read only = No
	guest only = Yes
	guest ok = Yes
	hosts allow = 192.168.0.
```

But I cant access my htpc shares. In nautilus it asks for password not when accessing the laptop with the same smb.conf.

If I change security = user to share my shares disappears from the network.

the only thing that differ between the computers is the output from

findsmb

Htpc's output

```
htpc@htpc:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.114   HTPC          +[	MSHOME        ]

```

laptop's output

```
sebastian@Laptop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.171   LAPTOP         [	MSHOME        ]

```

what is +=LMB? Can I unenable it? Also I have not installed a firewall.

---

### Post by DaveInPhx on 2010-03-28
Last things first, *=DMB and +=LMB are simply a "key" to tell you that if a * or a + appears alongside a machine, it indicates that it is either a Domain Master Browser (DMB) or a Local Master Browser (LMB).  It doesn't mean anything in your context since neither machine is marked.

Hope that clears up part of it for you :)

---

### Post by 8301 on 2010-03-28
Thanx for that bit of information. 

But how can two clean installs of one 64-bit and the other 32-bit of ubuntu 9.10 and with same smb.conf behave so different?

---


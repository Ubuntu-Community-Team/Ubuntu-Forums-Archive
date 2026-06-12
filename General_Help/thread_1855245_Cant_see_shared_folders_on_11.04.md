---
title: "Cant see shared folders on 11.04"
date: 2011-10-05
forum: General Help
---

### Post by sjprice on 2011-10-05
Sharing 3 folders on a mounted drive. Have Samba installed and running:


```
sprice@ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Movies]"
Processing section "[Shows]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
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
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	force user = sprice

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Movies]
	path = /media/shared/Movies
	read only = No
	guest ok = Yes

[Shows]
	path = /media/shared/Shows
	read only = No
	guest ok = Yes

[Music]
	path = /media/shared/Music
	read only = No
	guest ok = Yes
```

Cannot browse the network from another 11.04 box, a Win 7 box or an XP box. Also cannot map a drive from any of the boxes.

My guess is permissions, since it is a mounted NTFS drive:

```
sprice@ubuntu:~$ ls -al /media/shared/Movies
total 28
drwxrwxrwx 1 root root 4096 2011-10-04 10:47 .
drwxrwxrwx 1 root root 4096 2011-10-04 09:59 ..
drwxrwxrwx 1 root root 4096 2011-10-01 18:55 movie names
drwxrwxrwx 1 root root    0 2011-09-02 16:52 movie names
drwxrwxrwx 1 root root    0 2010-02-07 17:23 movie names
drwxrwxrwx 1 root root 4096 2011-10-02 09:31 movie names
drwxrwxrwx 1 root root 4096 2011-10-04 10:00 movie names
drwxrwxrwx 1 root root 4096 2011-10-04 09:59 movie names
drwxrwxrwx 1 root root    0 2010-02-06 17:04 movie names
drwxrwxrwx 1 root root 4096 2009-09-08 12:41 movie names
```

What is my next step?

---

### Post by sjprice on 2011-10-06
I should be more descriptive in the errors.

I can now see the icon in Network for my 11.04 box my shared files are on, but it errors out when clicking on it with:
Unable to mount location
Failed to retrieve share list from server

When using "Connect to server" and Windows share, it errors out with:
Could not display "smb://ubuntu/media/shared/movies"
Error:Failed to mount windows share
Please select another viewer and try again.

(ubuntu is the name of the 11.04 box the shares reside on.)

Edit: Solved by opening the firewall ports on my 11.04 box for Samba. Google for port numbers.

---


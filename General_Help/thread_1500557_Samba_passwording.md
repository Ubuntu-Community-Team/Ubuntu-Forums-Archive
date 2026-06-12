---
title: "Samba passwording"
date: 2010-06-03
forum: General Help
---

### Post by Primefalcon on 2010-06-03
I seem to be having a little issue with samba

I have samba and a windows XP machine here, I have them working fine except for when I want to require a username and password to access a shared folder on Ubuntu....

Guest access works great, however as soon as I go administration-> samba and try to create a folder that is limited to only a certain user login, the windows machine asks for the username and password, then when I enter the account username and password it just keeps saying it's not accessible....

---

### Post by Primefalcon on 2010-06-03
For reference I've tried created a seperate account on ubuntu and user that user and pass (just to be sure) I also create a different password for it using sudo smbpasswd -a username and still no luck....

---

### Post by Morbius1 on 2010-06-03
Why not post the output of the following commands so we can see if there's anything "funny" about your samba setup:

```
net usershare info
testparm -s
```

---

### Post by Primefalcon on 2010-06-03
Okies

> primefalcon@blackbeard:~$  net usershare info
[marshare]
path=/home/primefalcon/Desktop/SharedWithMarlaine
comment=
usershare_acl=Everyone:F,
guest_ok=y


and

> primefalcon@blackbeard:~$  testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
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
	valid users = goldlace, nobody, primefalcon, webdesign
	read only = No
	browseable = No
	browsable = No


---

### Post by Morbius1 on 2010-06-03
Um ... you don't have any of the type of shares you described here:
> however as soon as I go administration-> samba and try to create a  folder that is limited to only a certain user login, the windows machine  asks for the username and password, then when I enter the account  username and password it just keeps saying it's not accessible...

---

### Post by Primefalcon on 2010-06-03
> **Morbius1 said:**
> Um ... you don't have any of the type of shares you described here:
No I neeeded to share the folders so I enabled guest access on path=/home/primefalcon/Desktop/SharedWithMarlaine using the system ->admin

---

### Post by Primefalcon on 2010-06-03
with it set up to actual use a password it looks like this


> primefalcon@blackbeard:~$  testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[folder]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
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
	valid users = goldlace, nobody, primefalcon, webdesign
	read only = No
	browseable = No
	browsable = No

[folder]
	path = /home/primefalcon/Desktop/folder
	valid users = primefalcon
	read only = No
primefalcon@blackbeard:~$  net usershare info
[marshare]
path=/home/primefalcon/Desktop/SharedWithMarlaine
comment=
usershare_acl=Everyone:F,
guest_ok=y

This is the one here

[folder]
	path = /home/primefalcon/Desktop/folder
	valid users = primefalcon
	read only = No

yet it still says auth fales

---

### Post by Morbius1 on 2010-06-03
Assuming you did an **smbpasswd -a primefalcon **somewhere along the way then I suspect the problem is here in /etc/samba/smb.conf:
>      username map = /etc/samba/smbusersThat parameter is normally used to convert a client user to a local server user. So if you have a user named mary then username map can be used to convert mary to john for example. I'm guessing you don't have that situation so I would comment it out so that it looks like this:
```
#username map = /etc/samba/smbusers
```Then restart samba:
```
sudo restart smbd
sudo restart nmbd
```

---

### Post by Primefalcon on 2010-06-09
> **Morbius1 said:**
> Assuming you did an **smbpasswd -a primefalcon **somewhere along the way then I suspect the problem is here in /etc/samba/smb.conf:
That parameter is normally used to convert a client user to a local server user. So if you have a user named mary then username map can be used to convert mary to john for example. I'm guessing you don't have that situation so I would comment it out so that it looks like this:
```
#username map = /etc/samba/smbusers
```Then restart samba:
```
sudo restart smbd
sudo restart nmbd
```

Sorry for the delayed post here, but I haven't had a chance to test this out until now, anyhow that worked perfectly, THANK YOU

---


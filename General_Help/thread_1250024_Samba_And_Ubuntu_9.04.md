---
title: "Samba And Ubuntu 9.04"
date: 2009-08-26
forum: General Help
---

### Post by sawk on 2009-08-26
Hi,

I'm new to linux/ubuntu. I have recently installed ubuntu 9.04, and installed samba (via synaptic) to enable network shares.

Samba seems to work ok, but I get an annoying problem on booting up the PC, It hangs and then I get a message saying 

"Reloading /etc/samba/smb.conf smbd only"  

It hangs here for a few minutes, and continues.

How can I stop getting this bootup problem.

Thanks

Steve

---

### Post by danwood76 on 2009-08-26
Have you modified the smb.conf file?
It might be that you have an error in that file.

To check your smb.conf file can you post the output of the following command from the linux terminal:
```

testparm

```

---

### Post by sawk on 2009-08-26
Hi,

this is the results of testparm


> Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[video]"
Processing section "[PS3]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No
	guest ok = Yes

[video]
	path = /media/video
	read only = No
	guest ok = Yes

[PS3]
	path = /media/spare/PS3
	guest ok = Yes


---

### Post by danwood76 on 2009-08-26
Are "/media/spare" and "/media/video" internal drives/partitions?

---

### Post by doas777 on 2009-08-26
I've had a simmilar issue, when I use the gnome network-manager. the problem is that samba starts at boot, but the network is not present at that time so samba fails (since NM starts the network after login).

I have to run:
```
sudo /etc/init.d/samba restart
``` at each boot 
or just reconfigure my nic to ignore network manager by setting everything in /etc/network/interfaces

---

### Post by sawk on 2009-08-26
Yep

Media/spare and Media/video are internal drive auto mounted in fstab.

---

### Post by sawk on 2009-08-26
Hi doas777,

I've noticed that wicd my network manager loads after the samba error, so may be the same issue that you are having.

Is there a way to change the boot order of these programs ?

---

### Post by sawk on 2009-08-26
went to system - administration - services

I changed folder sharing service (samba) start to s21 on all run level's.

Seems to be working at the moment.

Thanks for all the replies and ideas :)

---

### Post by doas777 on 2009-08-26
> **sawk said:**
> went to system - administration - services

I changed folder sharing service (samba) start to s21 on all run level's.

Seems to be working at the moment.

Thanks for all the replies and ideas :)

Dude! That's a very elegant solution to the problem. thanks for cluein' me in.

---


---
title: "Samba guest shares - win7 and android OK but other Linux fails"
date: 2011-04-18
forum: General Help
---

### Post by castalla on 2011-04-18
I have Samba  guest shares working - win7 and android tablet see the shares.  However, a media player just reports No Folders Found.  The media player can see Win7 and Android samba shares.

Here's the testparm -s

> mint@mint ~/Desktop $ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
	server string = %h server (Samba, LinuxMint)
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
	read only = No
	create mask = 0775
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = Yes
	create mask = 0700
	guest ok = No
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = Yes
	guest ok = No


Any ideas?

---

### Post by Morbius1 on 2011-04-18
You have no shares defined so I'm guessing you used Nautilus to create the Samba share. Please post the output of the following command:
```
net usershare info --long
```

---

### Post by castalla on 2011-04-18
Thanks for the reply - yes I used nautilus shares.

Here's the output:

> mint@mint ~/Desktop $ net usershare info --long
[shared]
path=/home/mint/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

[downloads]
path=/home/mint/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[documents]
path=/home/mint/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y


---

### Post by Morbius1 on 2011-04-18
Please post the output of the following command:
```
ls -al /home/mint
```

---

### Post by castalla on 2011-04-18
as requested ....

> mint@mint ~/Desktop $ ls -al /home/mint
total 852
drwxr-xr-x 39 mint mint   4096 Apr 18  2011 .
drwxr-xr-x  3 root root   4096 Apr 14 13:25 ..
-rw-------  1 mint mint   8060 Apr 18  2011 .ICEauthority
drwx------  3 mint mint   4096 Apr 14 12:27 .adobe
-rw-------  1 mint mint   1226 Apr 18 19:03 .bash_history
-rw-r--r--  1 mint mint    220 Apr 14 13:25 .bash_logout
drwx------  5 mint mint   4096 Apr 18  2011 .cache
drwx------  3 mint mint   4096 Apr 14 12:30 .compiz
drwxr-xr-x 10 mint mint   4096 Apr 17 20:04 .config
drwx------  3 mint mint   4096 Apr 14 13:26 .dbus
-rw-------  1 mint mint     16 Apr 14 13:26 .esd_auth
drwx------  3 mint mint   4096 Apr 14 13:45 .evolution
drwx------  5 mint mint   4096 Apr 18  2011 .gconf
drwx------  2 mint mint   4096 Apr 18 19:03 .gconfd
drwx------  8 mint mint   4096 Apr 18 11:29 .gnome2
drwx------  2 mint mint   4096 Apr 14 13:26 .gnome2_private
drwx------  2 mint mint   4096 Apr 15 10:02 .gnupg
drwxr-xr-x  2 mint mint   4096 Apr 17 18:16 .gstreamer-0.10
-rw-r--r--  1 mint mint    132 Apr 18  2011 .gtk-bookmarks
dr-x------  2 mint mint      0 Apr 18  2011 .gvfs
drwxr--r--  2 mint mint   4096 Apr 14 13:38 .hardinfo
drwxr-xr-x  2 mint mint   4096 Apr 14 12:29 .icons
drwxr-xr-x  5 mint mint   4096 Apr 15 13:04 .linuxmint
drwxr-xr-x  3 mint mint   4096 Apr 14 13:25 .local
drwx------  3 mint mint   4096 Apr 14 12:27 .macromedia
drwx------  3 mint mint   4096 Apr 14 11:42 .mission-control
drwx------  4 mint mint   4096 Apr 14 12:26 .mozilla
drwxr-xr-x  2 mint mint   4096 Apr 17 13:27 .mplayer
drwxr-xr-x  2 mint mint   4096 Apr 14 13:26 .nautilus
-rw-r--r--  1 mint mint    675 Apr 14 13:25 .profile
drwx------  2 mint mint   4096 Apr 18  2011 .pulse
-rw-------  1 mint mint    256 Apr 14 13:26 .pulse-cookie
-rw-------  1 mint mint   6953 Apr 17 23:14 .recently-used.xbel
-rw-r--r--  1 mint mint 623602 Apr 17 23:10 .sinthgunt.log
drwx------  2 mint mint   4096 Apr 15 10:02 .ssh
-rw-r--r--  1 mint mint      0 Apr 14 12:03 .sudo_as_admin_successful
drwxr-xr-x  2 mint mint   4096 Apr 14 12:29 .themes
drwx------  4 mint mint   4096 Apr 17 23:14 .thumbnails
drwxr-xr-x  2 mint mint   4096 Apr 17 19:33 .winff
-rw-------  1 mint mint   4883 Apr 18 18:35 .xsession-errors
-rw-------  1 mint mint   9782 Apr 18 11:29 .xsession-errors.old
drwxr-xr-x  2 mint mint   4096 Apr 18  2011 Desktop
drwxrwxrwx  2 mint mint   4096 Apr 17 16:02 Documents
drwxrwxrwx  2 mint mint   4096 Apr 17 16:02 Downloads
drwxr-xr-x  2 mint mint   4096 Apr 14 13:26 Music
drwxr-xr-x  2 mint mint   4096 Apr 14 13:26 Pictures
drwxr-xr-x  2 mint mint   4096 Apr 14 13:26 Public
drwxrwxrwx  2 mint mint   4096 Apr 17 23:15 Shared
drwxr-xr-x  2 mint mint   4096 Apr 14 13:26 Templates
-rw-r--r--  1 mint mint  23551 Apr 14 12:52 ViaVPN Linux All OpenVPN Config.zip
drwxr-xr-x  2 mint mint   4096 Apr 14 13:26 Videos
drwxr-xr-x  2 mint mint   4096 Nov 25 11:57 config


---

### Post by Morbius1 on 2011-04-18
I hate to tell you this but except for "security = SHARE" ( which in this case doesn't really matter ) everything is textbook correct. The fact that Win7 has no issues points to something about the Media Player.

All the usual suspects on the server end like host name length, linux permissions, firewalls, etc.. would stop the Win7 machine as well so I'm at a loss at the moment.

---

### Post by castalla on 2011-04-18
very strange .... I actually have 2 different media players - one reports the No Folders Found message, the other demands a user and password login.  Somebody else told me they got shares working in the second case by changing directory permissioons to 740  (???).

How would I specify that in samba.conf  ?

---

### Post by Morbius1 on 2011-04-18
Your shares are defined as allowing guest access and the linux permissions on the target directories are 777. Everyone and your Aunt Agnes should have free and unfettered access to those shares.

---

### Post by castalla on 2011-04-18
Well ... I'm well and truly baffled!!!

Thanks for the help .... if you have any afterthoughts ...

---


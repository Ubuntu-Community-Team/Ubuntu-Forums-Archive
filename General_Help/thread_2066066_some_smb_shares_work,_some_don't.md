---
title: "some smb shares work, some don't"
date: 2012-10-03
forum: General Help
---

### Post by qwertyjjj on 2012-10-03
I'm not sure what the issue is here, from the client, I cannot view some of the folders using nautilus yet some I can.
Using smbclient command I get:

```

$ smbclient -L 192.168.0.9 -Uguest
Enter guest's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	xbmc            Disk      
	Media           Disk      
	Films1          Disk      
	TV2             Disk      
	IPC$            IPC       IPC Service (jmediacentre-A880G server (Samba, Ubuntu))
	Films           Disk      
	TVShows         Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	JMEDIACENTRE-A88     jmediacentre-A880G server (Samba, Ubuntu)
	USB                  usb server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            USB
bedroom@bedroom-Inspiron-9300:~$ 

```

In nautilus I can browse Media.
In nautilus I cannot browse Films1.
In xbmc I can add Media.
In xbmc I cannot add Films1 - it keeps asking for a password.

Seems strange as if they weren't accessible by smb then the smbclient command shouldn;t show them

testparm gives:
```

j-media-centre@jmediacentre-A880G:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[xbmc]"
Processing section "[Media]"
Processing section "[Films1]"
Processing section "[TV2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

```

---

### Post by Morbius1 on 2012-10-03
Post the output of this command instead so we can actually see something:
```
testparm -s
```
And like I said before, unless you are actually accessing jmediacentre-A880G by ip address that name will have to go since it’s too long: [http://ubuntuforums.org/showpost.php?p=12271491&postcount=3](http://ubuntuforums.org/showpost.php?p=12271491&postcount=3)

---

### Post by qwertyjjj on 2012-10-03
> **Morbius1 said:**
> Post the output of this command instead so we can actually see something:
```
testparm -s
```
And like I said before, unless you are actually accessing jmediacentre-A880G by ip address that name will have to go since it’s too long: [http://ubuntuforums.org/showpost.php?p=12271491&postcount=3](http://ubuntuforums.org/showpost.php?p=12271491&postcount=3)

```

j-media-centre@jmediacentre-A880G:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[xbmc]"
Processing section "[Media]"
Processing section "[Films1]"
Processing section "[TV2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = MEDIACENTRE
	server string = %h server (Samba, Ubuntu)
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
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[xbmc]
	path = /home/xbmc
	read only = No
	guest ok = Yes

[Media]
	path = /Media
	read only = No
	guest ok = Yes

[Films1]
	path = /home/j-media-centre/Videos/Films
	read only = No
	guest ok = Yes

[TV2]
	path = /home/j-media-centre/Videos/TV\ Shows
	read only = No
	guest ok = Yes
j-media-centre@jmediacentre-A880G:~$ 

```

---

### Post by qwertyjjj on 2012-10-04
> **Morbius1 said:**
> Post the output of this command instead so we can actually see something:
```
testparm -s
```
And like I said before, unless you are actually accessing jmediacentre-A880G by ip address that name will have to go since it’s too long: [http://ubuntuforums.org/showpost.php?p=12271491&postcount=3](http://ubuntuforums.org/showpost.php?p=12271491&postcount=3)

```

j-media-centre@jmediacentre-A880G:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[xbmc]"
Processing section "[Media]"
Processing section "[Films1]"
Processing section "[TV2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = MEDIACENTRE
	server string = %h server (Samba, Ubuntu)
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
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[xbmc]
	path = /home/xbmc
	read only = No
	guest ok = Yes

[Media]
	path = /Media
	read only = No
	guest ok = Yes

[Films1]
	path = /home/j-media-centre/Videos/Films
	read only = No
	guest ok = Yes

[TV2]
	path = /home/j-media-centre/Videos/TV\ Shows
	read only = No
	guest ok = Yes
j-media-centre@jmediacentre-A880G:~$ 

```

---

### Post by Morbius1 on 2012-10-04
What is the output of this command:
```
ls -al /home/j-media-centre/Videos
```

---

### Post by qwertyjjj on 2012-10-04
> **Morbius1 said:**
> What is the output of this command:
```
ls -al /home/j-media-centre/Videos
```

```

$ ls -al /home/j-media-centre/Videos
total 64
drwxr-xr-x  4 j-media-centre j-media-centre 16384 Sep  4 23:20 .
drwxr--r-- 58 j-media-centre j-media-centre 20480 Oct  3 20:05 ..
drwxrwxr-x 81 j-media-centre j-media-centre 20480 Sep 10 20:47 Films
drwxrwxr-x 13 j-media-centre j-media-centre  4096 Sep  8 23:41 TV Shows


```

---

### Post by Morbius1 on 2012-10-04
Your permissions are all messed up. 
> drwxr--r-- 58 j-media-centre j-media-centre 20480 Oct  3 20:05 ..The permissions on /home/j-media-centre are 744. It needs to be 755.
> drwxrwxr-x 81 j-media-centre j-media-centre 20480 Sep 10 20:47 Films
 drwxrwxr-x 13 j-media-centre j-media-centre  4096 Sep  8 23:41 TV ShowsThe permissions on these are 775 but you want write access by guests so it needs to be 777.

Probably the easiest way around this is to use Samba itself. Change your share definitions to this:
> [Films1]
    path = /home/j-media-centre/Videos/Films
    read only = No
    guest ok = Yes
    [COLOR=Blue]**force user = j-media-centre**[/COLOR]

[TV2]
    path = /home/j-media-centre/Videos/TV\ Shows
    read only = No
    guest ok = Yes
    [COLOR=Blue]**force user = j-media-centre**[/COLOR]Then restart samba:
```
sudo service smbd restart
```

---

### Post by qwertyjjj on 2012-10-05
> **Morbius1 said:**
> Your permissions are all messed up. 
The permissions on /home/j-media-centre are 744. It needs to be 755.
The permissions on these are 775 but you want write access by guests so it needs to be 777.

Probably the easiest way around this is to use Samba itself. Change your share definitions to this:
Then restart samba:
```
sudo service smbd restart
```

Sorted.
Thanks

---


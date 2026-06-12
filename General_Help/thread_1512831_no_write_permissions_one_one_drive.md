---
title: "no write permissions one one drive"
date: 2010-06-18
forum: General Help
---

### Post by chrismitt2002 on 2010-06-18
i have sevrel hard drives among 3 pcs all (root of the drive) are shared (except os drive)one pc i use for captureing tv this drive has no write permission from my local pc but all other hard drives have read/write permissions

---

### Post by chrismitt2002 on 2010-06-18
bump

---

### Post by Morbius1 on 2010-06-18
Ya lost me. "shared" as in samba?

---

### Post by chrismitt2002 on 2010-06-18
yes

---

### Post by Morbius1 on 2010-06-18
Post the output of the following commands so we can see how you are configured:

```
net usershare info
```
```
sudo net usershare info
```
```
testparm -s
```

---

### Post by chrismitt2002 on 2010-06-18
owner@intel-quad:~$ net usershare info
owner@intel-quad:~$ sudo net usershare info
owner@intel-quad:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[D-931gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Processing section "[E-931gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Processing section "[F-931gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Processing section "[G-931gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Processing section "[H-698gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Processing section "[I-931gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Processing section "[J-931gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Processing section "[K-931gb]"
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
	server string = 
	null passwords = Yes
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	wins support = Yes

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[D-931gb]
	path = /media/D-931gb/
	force user = owner
	read only = No
	create mask = 0644

[E-931gb]
	path = /media/E-931gb/
	force user = owner
	read only = No
	create mask = 0644

[F-931gb]
	path = /media/F-931gb/
	force user = owner
	read only = No
	create mask = 0644

[G-931gb]
	path = /media/G-931gb/
	force user = owner
	read only = No
	create mask = 0644

[H-698gb]
	path = /media/H-698gb/
	force user = owner
	read only = No
	create mask = 0644

[I-931gb]
	path = /media/I-931gb/
	force user = owner
	read only = No
	create mask = 0644

[J-931gb]
	path = /media/J-931gb/
	force user = owner
	read only = No
	create mask = 0644

[K-931gb]
	path = /media/K-931gb/
	force user = owner
	read only = No
	create mask = 0644
owner@intel-quad:~$

---

### Post by Morbius1 on 2010-06-18
Just so you know, what testparm does is test for errors and interprets the smb.conf file and prints it's interpretation. So all those errors:
```
Unknown parameter encountered: "ready only"
Ignoring unknown parameter "ready only"
```Aren't hurting anything since it's ignoring them but you might want to go in there some day and remove the "ready only" line.

All of that looks OK to me assuming "owner" has write access to the directory in the path. For example can "owner" write to /media/D-931gb/ locally?

You might want to issue the following command and see if "owner" has write access to all those directories:
```
ls -al /media
```

---

### Post by chrismitt2002 on 2010-06-18
the drive that has no write permissions is on windows not linux but is a mapped drive

---

### Post by chrismitt2002 on 2010-06-18
owner@intel-quad:~$ ls -al /media
total 529
drwxrwxrwx 23 root  root    4096 2010-06-18 12:28 .
drwxr-xr-x 23 root  root    4096 2010-06-05 22:25 ..
drwxr-xr-x  1 root  root       0 2010-06-17 22:31 capture
drwxrwxrwx  1 root  root       0 2010-06-11 19:37 D
drwxrwxrwx  2 root  root    4096 2010-06-17 18:34 d-500gb
drwxrwxrwx  1 root  root   32768 2010-06-11 19:37 D-931gb
drwxr-xr-x  2 root  root    4096 2010-06-13 21:21 dtools
drwxrwxrwx  1 root  root       0 2010-06-11 19:37 E
drwxrwxrwx  1 root  root   24576 2010-06-11 19:58 E-931gb
drwxrwxrwx  1 root  root       0 2010-03-14 21:24 F
drwxrwxrwx  1 root  root    8192 2010-06-14 20:53 F-931gb
drwxrwxrwx  1 root  root       0 2010-06-03 13:28 G
drwxrwxrwx  1 root  root   16384 2010-06-15 19:39 G-931gb
drwxrwxrwx  1 root  root       0 2010-06-08 14:07 H
drwxrwxrwx  1 root  root    4096 2010-06-11 19:37 H-698gb
drwxrwxrwx  2 root  root    4096 2010-06-05 22:14 I
drwxrwxrwx  1 root  root    4096 2010-06-04 11:59 I-1.5tb
drwxrwxrwx  2 root  root    4096 2010-06-05 22:14 J
drwx------  1 owner owner 385024 2010-06-15 21:38 J-931gb
drwxrwxrwx  2 root  root    4096 2010-06-05 22:14 K
drwx------  1 owner owner  32768 2010-06-11 19:37 K-931gb
drwx------  9 owner owner   4096 1969-12-31 17:00 PENDRIVE
dr-x------  1 owner owner    564 2006-02-28 05:00 VX2PFPP_EN
owner@intel-quad:~$

---

### Post by Morbius1 on 2010-06-18
Maybe it's because it's the end of the day here for me but I still don't understand. 

> the drive that  has no write permissions is on windows not linux but is a mapped drive Then the problem is either in how you're mapping it or if windows is not allowing a write on it's end.

---

### Post by chrismitt2002 on 2010-06-18
i have mapped all other drives the same way and the shared windows drive has write permissions on windows but not on this pc

---

### Post by chrismitt2002 on 2010-06-18
bump

---

### Post by chrismitt2002 on 2010-06-18
bump

help i dont know what to do

---

### Post by chrismitt2002 on 2010-06-19
bump

---

### Post by chrismitt2002 on 2010-06-22
bump

---


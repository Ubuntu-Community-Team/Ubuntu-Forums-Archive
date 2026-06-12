---
title: "Cant share files over network"
date: 2011-03-10
forum: General Help
---

### Post by WinterMadness on 2011-03-10
Hi, I recently installed Samba, and I know ive been able to do this before by simply using the GUI interface, but now it doesnt work.

I installed Samba, right clicked the folder I wanted to share and clicked share this folder, nautilus updated automatically.

So I go over to my Windows 7 machine to see if I can find my ubuntu machine and I cant. Any help? 

At one time I had this setup, but it was an older version of ubuntu, im using 10.10 now, and it seems samba has been updated a bit since.

---

### Post by WinterMadness on 2011-03-10
I found some info that may be helpful to the person who helps me out

when i type samba into the terminal i get:

```
joe@server:~$ samba
Unknown parameter encountered: "remote announce"
Ignoring unknown parameter "remote announce"
Unknown parameter encountered: "remote browse sync"
Ignoring unknown parameter "remote browse sync"
Unknown parameter encountered: "printcap name"
Ignoring unknown parameter "printcap name"
Unknown parameter encountered: "cups options"
Ignoring unknown parameter "cups options"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "username level"
Ignoring unknown parameter "username level"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "domain master"
Ignoring unknown parameter "domain master"
Unknown parameter encountered: "os level"
Ignoring unknown parameter "os level"
Unknown parameter encountered: "logon drive"
Ignoring unknown parameter "logon drive"
Unknown parameter encountered: "logon home"
Ignoring unknown parameter "logon home"
Unknown parameter encountered: "logon path"
Ignoring unknown parameter "logon path"
Unknown parameter encountered: "logon script"
Ignoring unknown parameter "logon script"
Unknown parameter encountered: "client use spnego"
Ignoring unknown parameter "client use spnego"
Unknown parameter encountered: "client schannel"
Ignoring unknown parameter "client schannel"
Unknown parameter encountered: "server schannel"
Ignoring unknown parameter "server schannel"
Unknown parameter encountered: "allow trusted domains"
Ignoring unknown parameter "allow trusted domains"
Unknown parameter encountered: "follow symlinks"
Ignoring unknown parameter "follow symlinks"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
Unknown parameter encountered: "passwd chat timeout"
Ignoring unknown parameter "passwd chat timeout"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "add user script"
Ignoring unknown parameter "add user script"
Unknown parameter encountered: "add user to group script"
Ignoring unknown parameter "add user to group script"
Unknown parameter encountered: "add group script"
Ignoring unknown parameter "add group script"
Unknown parameter encountered: "delete user script"
Ignoring unknown parameter "delete user script"
Unknown parameter encountered: "delete user from group script"
Ignoring unknown parameter "delete user from group script"
Unknown parameter encountered: "delete group script"
Ignoring unknown parameter "delete group script"
Unknown parameter encountered: "add machine script"
Ignoring unknown parameter "add machine script"
Unknown parameter encountered: "machine password timeout"
Ignoring unknown parameter "machine password timeout"
Unknown parameter encountered: "idmap uid"
Ignoring unknown parameter "idmap uid"
Unknown parameter encountered: "idmap gid"
Ignoring unknown parameter "idmap gid"
Unknown parameter encountered: "winbind use default domain"
Ignoring unknown parameter "winbind use default domain"
Unknown parameter encountered: "winbind cache time"
Ignoring unknown parameter "winbind cache time"
Unknown parameter encountered: "winbind trusted domains only"
Ignoring unknown parameter "winbind trusted domains only"
Unknown parameter encountered: "winbind nested groups"
Ignoring unknown parameter "winbind nested groups"
Unknown parameter encountered: "winbind nss info"
Ignoring unknown parameter "winbind nss info"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "create mode"
Ignoring unknown parameter "create mode"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "use client driver"
Ignoring unknown parameter "use client driver"
Unknown parameter encountered: "printing"
Ignoring unknown parameter "printing"
Unknown parameter encountered: "print command"
Ignoring unknown parameter "print command"
Unknown parameter encountered: "lpq command"
Ignoring unknown parameter "lpq command"
Unknown parameter encountered: "lprm command"
Ignoring unknown parameter "lprm command"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[Thu Mar 10 18:51:50 2011 EST, 0 ../smbd/server.c:374:binary_smbd_main()]
samba version 4.0.0alpha12-GIT-UNKNOWN started.
Copyright Andrew Tridgell and the Samba Team 1992-2010
joe@server:~$ 

```

---

### Post by pricetech on 2011-03-10
Install system-config-samba and configure that way.

---

### Post by WinterMadness on 2011-03-10
I have that, and ive used it a bit to no avail

Also:

```
joe@server:~$ sudo /etc/init.d/samba   restart
[sudo] password for joe: 
sudo: /etc/init.d/samba: command not found

```

Weird...

EDIT:

Tried this

```
joe@server:~$ /etc/init.d/samba4 restart
 * Stopping Samba 4 daemon samba                                                                                                                                                  start-stop-daemon: warning: failed to kill 1915: Operation not permitted
start-stop-daemon: warning: failed to kill 1913: Operation not permitted
start-stop-daemon: warning: failed to kill 1907: Operation not permitted
start-stop-daemon: warning: failed to kill 1906: Operation not permitted
start-stop-daemon: warning: failed to kill 1905: Operation not permitted
start-stop-daemon: warning: failed to kill 1902: Operation not permitted

```

Is it not installed correctly or something? I goto synaptic and everything looks good. Hopefully someone knows

---

### Post by WinterMadness on 2011-03-10
bump

---

### Post by WinterMadness on 2011-03-10
last bump of the night

---

### Post by polki@mac.com on 2011-03-11
You forgot "sudo". Good luck!

---

### Post by Morbius1 on 2011-03-11
It would appear as though you now have what is technically called a discombobulation.
>  I installed Samba, right clicked the folder I wanted to share and clicked share this folder, nautilus updated automatically.The process you described above is creating a Samba Usershare ( a.k.a. nautilus-share).
        > Install system-config-samba and configure that way.     .......
        I have that, and ive used it a bit to no availThe process you just described above is creating a Samba Classic Share.

You are probably creating shares using two different methods on the same target which may or may not work - I try to avoid it myself.

Finally it appears you are using Samba4:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production.Don't know what to tell you about Samb4 - I would remove it but that's me.

If you want to see if Usershare conflicts with Classic Share you can post the output of the following commands so the folks here can see if something is hosed:
```
net usershare info --long
``````
testparm -s
```

---

### Post by WinterMadness on 2011-03-11
I recently deleted everything samba and reinstalled it, but i did those commands, take a look.

**net usershare info --long**
```
joe@server:~$ sudo net usershare info --long
[sudo] password for joe: 
[public]
path=/home/joe/Public
comment=
usershare_acl=Everyone:R,SAMBA24@joe:F,
guest_ok=n

joe@server:~$ 
```
**testparm**
```
joe@server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[Public]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	netbios name = SAMBA24
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	strict locking = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = No
	locking = No
	strict locking = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No
	strict locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	locking = No
	strict locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	guest ok = Yes
	locking = No
	strict locking = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

[Public]
	path = /home/joe/Public
	valid users = joe
	read only = No
joe@server:~$ 

```

---

### Post by Morbius1 on 2011-03-11
I can only speak for myself of course but life is too short to try to troubleshoot the output of gadmin-samba or whatever it was that created that smb.conf.

Your usershare looks OK though as long as you set up samba users.

As far as not being able to actually see the ubuntu shares it could be that smb.conf. It could be a firewall is in the way. Or it could be your network.

Can you access the share by ip address?

---

### Post by WinterMadness on 2011-03-11
> **Morbius1 said:**
> I can only speak for myself of course but life is too short to try to troubleshoot the output of gadmin-samba or whatever it was that created that smb.conf.

Your usershare looks OK though as long as you set up samba users.

As far as not being able to actually see the ubuntu shares it could be that smb.conf. It could be a firewall is in the way. Or it could be your network.

Can you access the share by ip address?

yes, ive actually set up a FTP server as a way to send files to my ubuntu machine by windows, but id really prefer if samba worked because i want to be able to have a print server on that machine

I even have a remote desktop connection right now into it, so something else is going on.

first order of business is getting this fixed though :)

---

### Post by WinterMadness on 2011-03-11
last bump

---


---
title: "Users Can't Use Ubuntu!"
date: 2009-11-19
forum: General Help
---

### Post by pclapham on 2009-11-19
Hi --

I have done a clean install of Karmic on my 64-bit machine and established a large number of users belonging to group "students."

I can log into ubuntu on this server, both directly via ssh and via samba from a windows machine.  However, none of the students can log in.  Looking on the GUI for user privileges didn't provide much info on who can log in and who cannot.  Can you direct me to a place where these privileges are noted?

Thanks.

---

### Post by NoaHall on 2009-11-19
Are you sure that they aren't using capitals? (correct case)

---

### Post by pclapham on 2009-11-19
Absolutely.  I was trying to log in as a student and am well aware of the role of case.  This seems to be a simple instance of a group that does not have logon privileges.  After I posted this query I set up my cat as a user with his own group.  He can log on, but my students can't.  It would appear that the default for a new group is no privileges, but establish a group equal to the user and you have privileges.  Isn't there a config file somewhere that sets privileges for groups?  I would really like to limit the number of groups I'm juggling, with the basic ones able to log on and access their home directories and the directories set up for them.

---

### Post by pclapham on 2009-11-19
Alternatively, is there a preexisting group that does have logon privileges and is there a way to insure that the groups I would set up have automatic membership in that group?

---

### Post by mathfeel on 2009-11-19
Before ssh-ing, you should check if the said student account can login locally. If not, check your local /etc/passwd for hints (paste relevant lines here if that's the case)

If local login works, then perhaps your sshd is set to block certain login. This would usually involve a line like
```

AllowGroup ...
AllowUser ...
DenyGroup ...
DenyUser ...

```

somewhere in /etc/ssh/sshd_config.

---

### Post by pclapham on 2009-11-19
I did try that.  Students can't log in.  Those users with a group name that's the same as their user ID can.  Locally or via ssh or via samba.  It really seems like groups that aren't the same as user IDs can't log in.  There HAS to be a place one can tell the system that a user ID on the system can log in regardless of its group name!  But I can't find it!

---

### Post by blueridgedog on 2009-11-19
How did you add the users?

Can you post the contents of /ect/passwd, editing out anything that you don't want to share:
```

cat /etc/passwd
```

---

### Post by pclapham on 2009-11-23
Thanks to all who have responded.  I actually have a lot more information now than I did when originally posting.  All users can log directly into the server, and they can also access the server by SSH.  The problem is in samba.  Interestingly, a user can access shares, both specific shares and home directories, using the net use command in Windows.  Indeed they can even log onto the server and use its resources if they have a local profile on the Windows machine.  In that case, they get the message that the system can't find the roaming profile and is loading them with the local profile.  What they cannot do is to log into the system if they do not have a local profile on the windows machine.  Given that all of the files they need are on the Ubuntu box, this is a real problem.  I've tried to log myself onto the server from several of my workstations and discovered that even though I have administrative privileges on both the Windows and Ubuntu machines I get the same "domain ERSL is not available" message as the students do.  

I am appending here my smb.conf file.  Perhaps one of you can spot the problem.

# Samba config file created using SWAT
# from UNKNOWN (127.0.0.)
# Date: 2009/11/21 17:16:53

[global]
	workgroup = ERSL
	server string = Environmental Remote Sensing Laboratory
        netbios aliases = earth.sr-02-01.csuohio.edu
	interfaces = eth1
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	logon drive = X:
	domain logons = Yes
	preferred master = Yes
	domain master = Yes
	wins support = Yes
	idmap uid = 10000-20000
	idmap gid = 10000-20000
	template homedir = /home2/%D/%U
	template shell = /bin/bash
	admin users = clapham

[homes]
	comment = Home Directories
	valid users = %S
	read only = No

#[netlogon]
	#comment = Network Logon Service
	#path = /home/samba/netlogon

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	write list = root, @ersladmin

[cdrom]
	comment = Samba server's CD-ROM
	path = /cdrom
	guest ok = Yes
	locking = No
	preexec = /bin/mount /cdrom
	postexec = /bin/umount /cdrom

[ghost]
	comment = GHOST files
	path = /applications/ghost
	valid users = clapham

[hcdn]
	comment = HydroClimatic Data Network
	path = /applications/courseware/hcdn

[hcdn92]
	comment = HydroClimatic Data Network Files
	path = /applications/courseware/hcdn92

[momnpop]
	comment = Mom and Pop Model
	path = /applications/courseware/momnpop

[ETProject]
	comment = Common project files for ET Project
	path = /home1/ETProject
	read only = No

[homes]
	comment = Home Directories
	valid users = %S
	read only = No


Since you've asked for the /etc/passwd file, here are some representative entries:

syslog:x:101:103::/home/syslog:/bin/false
landscape:x:102:105::/var/lib/landscape:/bin/false
sshd:x:103:65534::/var/run/sshd:/usr/sbin/nologin
clapham:x:1000:1000:Pete Clapham,,,,:/home1/clapham:/bin/bash
messagebus:x:104:114::/var/run/dbus:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:106:115:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:107:116:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:108:117:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
haldaemon:x:109:118:Hardware abstraction layer,,,:/var/run/hald:/bin/false
speech-dispatcher:x:110:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:111:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
saned:x:112:119::/home/saned:/bin/false
pulse:x:113:120:PulseAudio daemon,,,:/var/run/pulse:/bin/false
gdm:x:114:122:Gnome Display Manager:/var/lib/gdm:/bin/false
limestone$:x:1028:100::/dev/null:/bin/false
missouri$:x:1032:100::/dev/null:/bin/false
sandusky$:x:1037:100::/dev/null:/bin/false
mosby:x:1050:1003:Mosby,,,:/home/mosby:/bin/bash
polkituser:x:115:123:PolicyKit,,,:/var/run/PolicyKit:/bin/false
judy:x:1027:1030:Beth Judy,,,:/home2/judy:/bin/bash

---

### Post by blueridgedog on 2009-11-25
People need a real shell:

Note that:

```
sandusky$:x:1037:100::/dev/null:/bin/false
```

has "/bin/false" as a shell, and 

```
mosby:x:1050:1003:Mosby,,,:/home/mosby:/bin/bash
```

has "/bin/bash".  mosby should be able to log in, and sandusky should not.

---

### Post by blueridgedog on 2009-11-25
The most common problem with samba is non uniform user accounts.  The name and passowrd must be the same in three locations and the case has the be the same.  The three locations are Windows System, Linux Shell and Samba.  Most people omit the samba user account step.

You have to creat user accounts for the users that match the accounts they use on windows including passwords and you have you use the smbpasswd command on your Ubuntu system to give passwords to those accounts that again match the Linux system password and the windows password that they use. See the link in my signature, especially section 1.1.

---

### Post by pclapham on 2009-12-01
I think this is correct -- mosby is a user; sandusky$ is a machine.  Is it useful/required to do something else?

---

### Post by pclapham on 2009-12-01
I think I did this.  I set up the user accounts using **adduser**, then set up the samba accounts using **pdbedit -a -u**.  The Windows users are authenticated by the PDC (which this machine is), so that there is not a separate local login on the windows machine.  For several years, until Karmic, this approach worked perfectly.  Now it doesn't.  What's really weird is that if a student has used a particular workstation, so that he or she has a local profile on that machine, it is possible for him/her to log into the system normally.  He/she gets the message that the system can't find the roaming profile and is loading the user from the local profile.  That sounds like the authentication is partially complete, but that it doesn't get to the home directory on the server.  The home directory does have to be loaded using the windows **net use** command, but the system is able to find it.  Very confusing!

---

### Post by pclapham on 2009-12-01
An additional piece of information I discovered recently.  While trying to deal with a totally different problem that involved adding a domain-based user to the Windows machine, I got the message that I couldn't do it because the trust relationship between the windows machine and the linux server was broken.  While I don't blame a linux box for not trusting a windows box, I suspect that this is actually the root of my problem.  I did delete the machine user and reestablish it using adduser machinename$ and pdbedit -a -m machinename.  The machinename appears in the pdbedit -Lv output as machinename$, and all would appear to be OK, except that the same results occur.

---


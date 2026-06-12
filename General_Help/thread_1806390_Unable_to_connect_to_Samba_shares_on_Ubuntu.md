---
title: "Unable to connect to Samba shares on Ubuntu"
date: 2011-07-17
forum: General Help
---

### Post by freshtealeaf on 2011-07-17
Hi

I'm trying to use Windows 7 to connect to a Samba server (running Ubuntu 11.04). 

Server is named Mars. Below is my Samba configuration file. I can ping the server, and connect to it via RDP and ssh, so i know its not a network connectivity issue. What else could it be? :KS



```
#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	server string = %h server (Samba, Ubuntu)
	force group = nobody
	guest ok = yes
	workgroup = mshome
	os level = 20
	force user = nobody
	interfaces = lo eth0
	security = share
	bind interfaces only = yes
	


#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
	writeable = yes
	guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

;[Share name]
;writable = yes
;path = /path/to/directory
;public = yes
;guest ok = yes
;guest only = yes
;guest account = nobody
;browsable = yes

[Aeonaeon3]
	path = /media/Aeonaeon3
	writeable = No
	browseable = yes
	valid users = aries
   create mask = 0755
   directory mask = 0755

[MEDIA]
	path = /media/Aeonaeon3/MEDIA
	writeable = No
	browseable = yes
	guest ok = yes
  create mask = 0755
   directory mask = 0755

[IsaacP1]
	path = /media/C60C80570C804481
	writeable = yes
	force user = nobody
	force group = nobody
	browseable = yes
	guest ok = yes
  create mask = 0755
   directory mask = 0755

[Aeonaeon2 233GB]
	path = /media/Aeonaeon2 233GB
	writeable = yes
	browseable = yes
	guest ok = yes
	force user = nobody
	force group = nobody
  create mask = 0755
   directory mask = 0755

[Vault1]
	path = /media/6d170594-4493-4394-a27f-cbd622678906/Vault1
	writeable = yes
	browseable = yes
  create mask = 0755
   directory mask = 0755
	guest ok = yes

[Vault2]
	path = /media/2b2dbfe6-8a64-41d0-81b9-e1e3ebf51220/Vault2
	writeable = yes
	browseable = yes
  create mask = 0755
   directory mask = 0755
	guest ok = yes

[IsaacP2]
	comment = p2
	path = /media/E4100FD2100FAB1E
	writeable = yes
	browseable = yes
	guest ok = yes
  create mask = 0755
   directory mask = 0755

```

---

### Post by gordintoronto on 2011-07-17
What version of Windows 7?

It might help if you describe what you do on the Windows machine, and what result you get.

---

### Post by mikejonesey on 2011-07-17
are you having problems with the login, does you bindows show the machine in the network list? need bit more info as stated in last post..

---

### Post by freshtealeaf on 2011-07-17
No, I cannot see it on the "Network" list at all. I can see the local Windows machines in my house, but not the Samba server. 

At one point I was able to connect to the Samba server, and I was still unable to get access to the directories. 

I'm running Windows 7 Enterprise.

---

### Post by gordintoronto on 2011-07-18
If you download issue 43 of Full Circle Magazine, the solution might be on page 33.
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---


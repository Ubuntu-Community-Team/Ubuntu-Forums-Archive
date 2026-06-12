---
title: "Please post a working smb.conf (on 2.6.15-23-686)"
date: 2006-06-11
forum: General Help
---

### Post by Flyn on 2006-06-11
Every since I switched to Dapper around Flight 3, I couldn't get XP computers to view the Ubuntu samba shares ("The network path was not found"), though it worked the other way round.
I've tried every guide, thread and general site I could find, and believe me, I've spent -way- more hours into this than is reasonable, and while no linux guru, I've been messing with Ubuntu for a long while now. So, as the topic says, someone please post a working smb.conf, because I just don't understand what I've been doing wrong.

Thanks in advance

---

### Post by rbalfour on 2006-06-11
[QUOTE=Flyn]Every since I switched to Dapper around Flight 3, I couldn't get XP computers to view the Ubuntu samba shares ("The network path was not found"), though it worked the other way round.
I've tried every guide, thread and general site I could find, and believe me, I've spent -way- more hours into this than is reasonable, and while no linux guru, I've been messing with Ubuntu for a long while now. So, as the topic says, someone please post a working smb.conf, because I just don't understand what I've been doing wrong.

Thanks in advance[/QUOTE]

May post your current SMB.conf and see what is wrong with it.

---

### Post by Flyn on 2006-06-11
rbalfour, not that I don't appreciate your response, but I'd prefer to do it this way. Couldn't you just post your smb.conf file, its not that big a request, is it?

Again, thanks in advance.

---

### Post by djsroknrol on 2006-06-11
check your System>Administration>Shared folders section...make sure that Samba is checked in there...I've had upgrades that have unchecked this twice...```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Mshome
   netbios name=server

# server string is the equivalent of the NT Description field
   server string = (Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

#   guest account = no
#   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
#   printing = bsd
#   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
#   printing = cups
#   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
#   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

wins support = no
[homes]
   browseable = yes
   path=/home/bob

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

available = yes
public = yes
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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



[Movies]
path = /media/hdb1/Movies
available = yes
browseable = yes
public = yes
writable = yes


[A-K]
path = /media/hdc1/A - K
available = yes
browseable = yes
public = yes
writable = yes

[L-Z]
path = /media/hdc1/L - Z
available = yes
browseable = yes
public = yes
writable = yes

[NewMP3's]
path = /media/hdc1/New MP3's
available = yes
browseable = yes
public = yes
writable = yes

[Transfers]
path = /media/hda1/Network transfers
available = yes
browseable = yes
public = yes
writable = yes


```

Also look at System>Administration>Networking..check your location in your active eth0 or eth1(what ever your case may be).I had problems with that resetting as well...good luck...

---

### Post by rbalfour on 2006-06-11
[QUOTE=Flyn]rbalfour, not that I don't appreciate your response, but I'd prefer to do it this way. Couldn't you just post your smb.conf file, its not that big a request, is it?

Again, thanks in advance.[/QUOTE]

The manly way...with gedit and SAMBA MAN file in hand. BTW, this is for a domain server.

```

[global]
   workgroup = mmsilver
   netbios name = %h
   server string = %h server (Samba %v)

   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Default logon
   logon drive = U:
   logon script = scripts/logon.bat



   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords with linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = no
   unix password sync = no
   
   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = @domain_admins
   valid users = %U
   read only = no

[office]
	comment = All Office Share
	writeable = yes
	valid users = @users
	browsable = yes
	path = /data/office

[accounting]
	comment = Accounting Share
	writeable = yes
	valid users = @mms-accounting
	browsable = yes
	path = /data/accounting

[sales]
	comment = Sales Share
	writeable = yes
	valid users = @mms-sales
	browsable = yes
	path = /data/sales

[backup]
	comment = File Backup
	writeable = yes
	valid users = @users
	browsable = /data/backup


```

---

### Post by Flyn on 2006-06-11
Lots of thanks to both of you, I'll try what you gave me as soon as I can and post.

---


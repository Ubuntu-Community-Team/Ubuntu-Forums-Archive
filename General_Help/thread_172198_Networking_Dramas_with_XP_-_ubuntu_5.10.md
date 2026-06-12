---
title: "Networking Dramas with XP - ubuntu 5.10"
date: 2006-05-08
forum: General Help
---

### Post by electroconvulsive on 2006-05-08
I have followed a few of the threads recently to get my networking with a winxp machine hapening. OK after following a few of the posts I have been able to browse and write to and from my windows shares from my linux ubuntu machine. But shared folders on the ubuntu linux machine still seem to be inacessible. I was a few hours ago able to browse these files and after no settings changes access is now denied. I want to be able to browse and write to and from the shares on the ubuntu machine from the windows machine. I am a little stuck here. 

Here is a copy of my smbconf file if it will help Ive changed a few settings from the default.

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
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

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
;   name resolve order = lmhosts host wins bcast


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
   encrypt passwords = false

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = nobody

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
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


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

wins support = yes
[homes]
   comment = Home Directories
   browseable = yes

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
   guest ok = no
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


[NetworkShare]
path = /root
available = yes
browseable = yes
public = yes
writable = yes

[shared]
path = /home/ric
available = yes
browseable = yes
public = yes
writable = yes


Well anyway I relly need some help on this one and any help would be appreciated.

---

### Post by yota on 2006-05-08
If you want a quick and dirty windows-style share add:

"guest account = root" under authentication section (global settings)

and

"guest ok = yes" to your shares definition.

It should make shares behave as you like, but please be aware of the unsafety of a setup in wich everyone can write in your /root dir.

Hope this helps!

---

### Post by dmizer on 2006-05-09
been there.  FINALLY got it working.

your problem is under share deffinitions:
```
wins support = yes
[homes]
comment = Home Directories
browseable = yes
```
the above is correct, but i need to call it to your attention because of this:
```
[NetworkShare]
path = /root
available = yes
browseable = yes
public = yes
writable = yes

[shared]
path = /home/ric
available = yes
browseable = yes
public = yes
writable = yes
```
linux network share is always homes ... like a mounted network drive in windows is always z:

mine looks like this:
```
[homes]
path = /home/dmizer/shared
available = yes
browseable = yes
public = yes
writable = yes
```

here's my whole samba.conf file:
```
#======================= Global Settings =====================================

[global]



# workgroup = NT-Domain-Name or Workgroup-Name, eg: LINUX2

   workgroup = YOURWORKGROUP



# server string is the equivalent of the NT Description field

   server string = %h server (Samba, Ubuntu)



# Security mode. Defines in which mode Samba will operate. Possible

# values are share, user, server, domain and ads. Most people will want

# user level security. See the HOWTO Collection for details.

   security = share



# This option is important for security. It allows you to restrict

# connections to machines which are on your local network. The

# following example restricts access to two C class networks and

# the "loopback" interface. For more examples of the syntax see

# the smb.conf man page

   hosts allow = 192.168.0. 127.0.


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

;   guest account = nobody
   invalid users = root

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

#============================ Share Definitions ==============================

wins support = no
[homes]

   
   browseable = no
   writable = no


[homes]
path = /home/dmizer/shared
available = yes
browseable = yes
public = yes
writable = yes
```
a few things to watch out for:
make sure you chmod the shared folder to the correct permissions.
make sure samba.conf shows "security = share"
make sure that "hosts allow = 192.168.0. 127.0." <-- should reflect your ip subnet.

---

### Post by chettyk on 2006-05-09
If you want to avoid the problems Yota spoke of, you need to make sure that the Samba on Ubuntu has a user with the same username and password as the user on XP. I couldn't do that without adding a user to my Ubuntu box.

The following are the steps I followed for doing that.

1. Add user to Ubuntu with the same username and password as on XP

2. ```
sudo smbpasswd -a <username>
```
    Keep the same username and password as in Step 1.

I'd also suggest shutting down any firewall on the XP while you are getting Samba working.

---

### Post by electroconvulsive on 2006-05-09
[QUOTE=yota]If you want a quick and dirty windows-style share add:

"guest account = root" under authentication section (global settings)

and

"guest ok = yes" to your shares definition.

It should make shares behave as you like, but please be aware of the unsafety of a setup in wich everyone can write in your /root dir.

Hope this helps![/QUOTE]


Thanx Yota got it working so I can move file seither using windows or ubuntu.

There is only one problem: If I move a file using the windows machine it appears on my ubuntu machine as locked and owned by root. Not a perfect outcome yet but a big help and im well on the way there.

---

### Post by electroconvulsive on 2006-05-09
[QUOTE=chettyk]If you want to avoid the problems Yota spoke of, you need to make sure that the Samba on Ubuntu has a user with the same username and password as the user on XP. I couldn't do that without adding a user to my Ubuntu box.

The following are the steps I followed for doing that.

1. Add user to Ubuntu with the same username and password as on XP

2. ```
sudo smbpasswd -a <username>
```
    Keep the same username and password as in Step 1.

I'd also suggest shutting down any firewall on the XP while you are getting Samba working.[/QUOTE]

Thanks Chettyk; I got it working both ways when I take my windows firewall down except any files transferred using the windows machine browser show up in the directory as being owned by root.

I'll take your advice but because my user on my windows machine has no password and ubuntu does not allow for the creation of users without passwords (same username on both machines). I guess the solution is going to be to add a pasword to the user on the windows machine in step 1

Does this also mean I can change guest to that username instead of root in my smb.conf file under authentication so that files transfered this way are owned by me instead of root.

---

### Post by yota on 2006-05-10
You can change the permissions on created files using:
```

create mask = 0666
directory mask = 7777

```
on your shares definition, so the files are accessible by local users even if they are still owned by root (or anyone else).

On my machine, for similar reasons, I've chosen to create a specific user "share", used it as "guest user" in smb.conf, with the above masks.
Then every local user that I want to have rights on shared files is included in group "share" and share is the gid for every shared file.

---


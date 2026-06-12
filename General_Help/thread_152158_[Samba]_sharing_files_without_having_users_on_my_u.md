---
title: "[Samba] sharing files without having users on my ubuntu machine"
date: 2006-03-29
forum: General Help
---

### Post by MaZZly on 2006-03-29
Hi
i would like to share files on my ubuntu machine without adding users to my ubuntu machine, is that possible?
is there anyway i could "smbpasswd -a greta" without having her as a user on ubuntu?

i would like to set a password for both greta and lanfiler so they'll have to log in on the server to acces the files

see my config file, and u'll maybe know what im trying to do:
> #
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
   workgroup = NYSAND
   netbios name = Flugan

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
   security = user



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

wins support = no

[Filer]
   comment = filer på servern
   browseable = yes
   path = /home/mazzly/filer
   valid users = mazzly lanfiler
   public = yes
   read only = yes
   writeable = no

[greta]
   comment = mammas filer
   browseable = yes
   path = /home/mazzly/greta
   valid users = mazzly greta
   read only = no
   public = yes
   writeable = yes

[admin]
   comment = admin area
   browseable = yes
   path = /home/mazzly/
   valid users = mazzly
   public = no
   read only = no
   writeable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

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
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
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





---

### Post by ispmarin on 2006-03-29
Do you want to share only to windows systems? If not, you can consider nfs to share to other linux machines... just an idea.

---

### Post by MaZZly on 2006-03-29
only to windows, but i only want to make a "network sharing account" not a ubuntu account to "smbpasswd -a lanfiler/greta"

but howto?

---

### Post by John.Michael.Kane on 2006-03-29
[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)
[http://www.skippy.net/linux/2000/smb-howto.html](http://www.skippy.net/linux/2000/smb-howto.html)
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by MaZZly on 2006-03-30
can i add users(like lanfiler or greta) without having them as a actual user on my server?? if im using:
```
security = user
```

---

### Post by Video Toaster on 2006-03-30
[QUOTE=MaZZly]can i add users(like lanfiler or greta) without having them as a actual user on my server?? if im using:
```
security = user
```[/QUOTE]
I don't think so, but you CAN disable the user's UNIX logon afterwards, which does effectively the same thing.

---

### Post by MaZZly on 2006-03-30
what securtiy do i have to put on to do what i want then? (make "not-ubuntu-user-but-still-user-for-acces-to-share")

---

### Post by Video Toaster on 2006-03-30
[QUOTE=MaZZly]what securtiy do i have to put on to do what i want then? (make "not-ubuntu-user-but-still-user-for-acces-to-share")[/QUOTE]
I think disabling the user's Ubuntu logon priviledges after adding the user is the best way to go.  Add the new users in Ubuntu and Samba and leave "security=user".  Then, for any users you do not want to be able to log on locally, type the following in a terminal window:
```
sudo passwd -l *username*
```
This will prevent the user from logging onto Ubuntu, but will still allow the user to log onto Samba.

---

### Post by MaZZly on 2006-03-31
[QUOTE=Video Toaster]I think disabling the user's Ubuntu logon priviledges after adding the user is the best way to go.  Add the new users in Ubuntu and Samba and leave "security=user".  Then, for any users you do not want to be able to log on locally, type the following in a terminal window:
```
sudo passwd -l *username*
```
This will prevent the user from logging onto Ubuntu, but will still allow the user to log onto Samba.[/QUOTE]


k, so i did that and i can log into the ubuntu server with greta, and i see all the shares (filer and greta), but when i try to acces the greta folder it says that it doesnt have permission to the folder. Its the same way if i log lanfiler. If i log on mazzly i can acces all the shares. what could be wrong?

*edit* i started to wonder if it has something to do with the paths of the "greta" and "filer" shares, couse they are in /home/mazzly/
is there any command i have to put for them to acces the share from there?

thnx in regards

---

### Post by MaZZly on 2006-04-01
anyone knows what to do??

---

### Post by Video Toaster on 2006-04-01
[QUOTE=MaZZly]k, so i did that and i can log into the ubuntu server with greta, and i see all the shares (filer and greta), but when i try to acces the greta folder it says that it doesnt have permission to the folder. Its the same way if i log lanfiler. If i log on mazzly i can acces all the shares. what could be wrong?

*edit* i started to wonder if it has something to do with the paths of the "greta" and "filer" shares, couse they are in /home/mazzly/
is there any command i have to put for them to acces the share from there?

thnx in regards[/QUOTE]
Check the file permissions for those two folders in Nautilus.  Right-click them (on the local computer) and check the Permissions tab.

---

### Post by KnottyMan on 2006-04-01
This is how I setup my remote jobsite servers:

I add the user as a system user.  'aduser --system username' 

From 'man adduser'

 A  home  directory  is created by the same rules as for normal users.  The new system user will have the shell /bin/false (unless overridden  with  the  --shell  option),  and  have logins disabled.  Skeletal configuration files are not copied.

So no Desktop folder, .profile, etc.  /bin/false as a shell so no local login.  I add them to the 'users' group and then make a shared folder on the file system for everybody to use.  smbpasswd sets their SMB password.

They get a their home directory as a share and a "shared" share for common stuff.  Works great.

---

### Post by MaZZly on 2006-04-02
[QUOTE=Video Toaster]Check the file permissions for those two folders in Nautilus.  Right-click them (on the local computer) and check the Permissions tab.[/QUOTE]

thank you so much, working like a dream now, only to set up printer sharing from xp machine now :)

---


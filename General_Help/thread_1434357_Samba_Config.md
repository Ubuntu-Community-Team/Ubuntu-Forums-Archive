---
title: "Samba Config"
date: 2010-03-20
forum: General Help
---

### Post by 8301 on 2010-03-20
yellow Iam trying to get samba work with no password on my home network. I want to have Writeble permissions for creating files and folders and sub folders in the shared folder with no password needed.

I have this set up

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
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
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

usershare owner only = False
guest account = nobody


#### Networking ####

interfaces = lo eth0
bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

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
;	read only = yes
;	guest ok = no
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

[Home]
writable = yes
path = /home/seb/
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes

[down]
path = /home/seb/down
writable = yes
path = /home/sebastian/
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
```

The things I have add is

#### global ####
usershare owner only = False
guest account = nobody
#### Networking ####
interfaces = lo eth0
bind interfaces only = yes
####### Authentication #######
security = share


I can access the /home/seb/ directory but cant write in it. And with the same permissions for the down directory I cant even access the folder from the other pc it only says "Could not display "smb://laptop/down".The file is of an unknown type"

And finally how can I clean up the smb.conf so it is readable?

---

### Post by Morbius1 on 2010-03-20
I'm going to pick off the easy question first ;).

>  And finally how can I clean up the smb.conf so it is readable?      If you want to see the smb.conf file without all the comments then :

Open **Terminal**
Type **testparm -s**

There is one interesting addition you made to your smb.conf which may ( repeat - may ) be a problem.:
> The things I have add is
#### global ####
[COLOR=Blue]usershare owner only = False[/COLOR]There are two completely different methods of sharing folders in Ubuntu:

Classic-share = where the share definitions are located in smb.conf and where you seem to have yours.
Nautilus-share = where the share definitions are located at /var/lib/samba/usershares.

Two different methods, two different config files, and two different ways to create them. The "usershare owner only = False" is for Nautilus-share so it appears you are using both methods. It's possible that one method is conflicting with the other method. 

Please post the output of the following commands so that we can determine if you have any nautilus-shares configured:

Open **Terminal**
Type **net usershare info**
Type [B]sudo net usershare info

[/B]If you have no nautilus-shares then my guess is that you are allowing guest access in samba but the linux file permissions on the target won't allow it. Post the output of the following so we can determine the file permissions on the target:

Open[B] Terminal
[/B]Type[B] ls -al /home/seb


[/B]

---

### Post by 8301 on 2010-03-20
Hey thanx for the answer

when Iam testing with testparm -s my shares looks like this

```
[Home]
	path = /home/sebastian/
	read only = No
	guest only = Yes
	guest ok = Yes

[Hämtningar]
	path = /home/sebastian/
	read only = No
	guest only = Yes
	guest ok = Yes

```

Why doesnt it say that Ive have writing permissions?

In smb.conf it says

```
[Home]
writable = yes
path = /home/sebastian/
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes

[Hämtningar]
path = /home/sebbastian/down
writable = yes
path = /home/sebastian/
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
```

Ive got nothing from

net usershare info
sudo net usershare info

And this is the output from 

ls -al /home/seb

```
sebastian@Laptop:~$ ls -al /home/sebastian
totalt 9116
drwxr-xr-x 57 sebastian sebastian    4096 2010-03-20 16:42 .
drwxr-xr-x  6 root      root         4096 2010-03-20 09:52 ..
-rw-r--r--  1 sebastian sebastian  722473 2010-01-24 12:29 01 The Downfall Of Us All 1.mp3
-rwxr--r--  1 sebastian sebastian   40002 2008-12-31 17:54 365.odt
drwx------  3 sebastian sebastian    4096 2010-01-13 20:54 .adobe
drwxr-xr-x  4 sebastian sebastian    4096 2010-01-24 12:29 .audacity-data
drwxr-xr-x  5 sebastian sebastian    4096 2010-01-13 18:42 Backup
-rw-------  1 sebastian sebastian    6961 2010-03-20 10:57 .bash_history
-rw-r--r--  1 sebastian sebastian     220 2010-01-13 17:52 .bash_logout
-rw-r--r--  1 sebastian sebastian    3180 2010-01-13 17:52 .bashrc
drwxr-xr-x 19 sebastian sebastian    4096 2010-01-14 16:55 Bilder
drwx------ 10 sebastian sebastian    4096 2010-02-20 18:09 .cache
drwxr-xr-x  2 sebastian sebastian    4096 2010-01-21 21:51 cbt
drwx------  3 sebastian sebastian    4096 2010-01-13 18:10 .compiz
drwxr-xr-x 19 sebastian sebastian    4096 2010-02-20 18:41 .config
-rw-r--r--  1 sebastian sebastian    2420 2010-03-13 08:37 .conkyrc
-rw-r--r--  1 sebastian sebastian    2547 2010-03-13 08:31 .conkyrc~
-rwxr-xr-x  1 sebastian sebastian      31 2010-03-14 12:18 .conky_start.sh
-rw-r--r--  1 sebastian sebastian      30 2010-02-21 09:41 .conky_start.sh~
drwx------  3 sebastian sebastian    4096 2010-01-13 17:54 .dbus
-rw-r--r--  1 root      root         4825 2010-01-14 12:19 default.pa~
-rw-r--r--  1 sebastian sebastian      42 2010-03-20 16:42 .dmrc
drwxr-xr-x 15 sebastian sebastian    4096 2010-01-23 14:51 Dokument
-rw-------  1 sebastian sebastian      16 2010-01-13 17:54 .esd_auth
drwxr-xr-x  3 sebastian sebastian    4096 2010-02-20 16:51 .evolution
-rw-r--r--  1 sebastian sebastian    5495 2010-02-20 16:51 .face
-rwxr--r--  1 sebastian sebastian  878157 2009-12-07 18:03 Fel omslag i XBMC.pdf
drwxr-xr-x  2 sebastian sebastian    4096 2010-02-27 09:10 .fontconfig
drwx------  4 sebastian sebastian    4096 2010-03-20 16:42 .gconf
drwx------  2 sebastian sebastian    4096 2010-03-20 16:53 .gconfd
drwx------  4 sebastian sebastian    4096 2010-01-14 16:59 .gegl-0.0
drwxr-xr-x 22 sebastian sebastian    4096 2010-03-13 09:21 .gimp-2.6
-rw-r-----  1 sebastian sebastian       0 2010-03-20 09:51 .gksu.lock
drwx------  9 sebastian sebastian    4096 2010-03-20 11:06 .gnome2
drwx------  2 sebastian sebastian    4096 2010-01-13 17:54 .gnome2_private
drwxr-xr-x  2 sebastian sebastian    4096 2010-02-20 16:54 .gnomenu
drwx------  2 sebastian sebastian    4096 2010-03-20 16:42 .gnupg
drwxr-xr-x  2 sebastian sebastian    4096 2010-02-18 09:28 .gstreamer-0.10
-rw-r--r--  1 sebastian sebastian     240 2010-03-20 16:42 .gtk-bookmarks
-rw-r--r--  1 sebastian sebastian     102 2010-02-20 16:59 .gtkrc-2.0
-rw-r--r--  1 sebastian sebastian     102 2010-02-20 16:59 .gtkrc-2.0~
dr-x------  2 sebastian sebastian       0 2010-03-20 16:42 .gvfs
drwxr-xr-x  2 sebastian sebastian    4096 2010-01-24 10:58 .helix
drwxr-xr-x 12 sebastian sebastian   12288 2010-03-20 09:36 Hämtningar
-rw-------  1 sebastian sebastian   37524 2010-03-20 16:42 .ICEauthority
drwxr-xr-x  5 sebastian sebastian    4096 2010-02-20 18:07 .icons
drwxr-xr-x  3 sebastian sebastian    4096 2010-03-12 17:18 .Incomplete
drwx------  3 sebastian sebastian    4096 2010-03-12 15:13 .kde
drwx------  3 sebastian sebastian    4096 2010-01-23 14:51 .kompozer.net
-rwxr--r--  1 sebastian sebastian 4112176 2009-12-07 21:01 Kopiera DVD-skiva.pdf
drwxr-xr-x  3 sebastian sebastian    4096 2010-01-13 17:57 .local
drwx------  3 sebastian sebastian    4096 2010-01-13 20:54 .macromedia
drwx------  3 sebastian sebastian    4096 2010-02-09 09:19 .mission-control
drwx------  5 sebastian sebastian    4096 2010-01-14 07:27 .mozilla
drwxr-xr-x  3 sebastian sebastian    4096 2010-01-14 07:26 .mozilla-thunderbird
drwxrwxrwx  4 sebastian sebastian   12288 2010-01-14 16:55 Musik
-rwxr--r--  1 sebastian sebastian 1718896 2009-12-07 20:34 Namnge hemladdade filmer.pdf
drwxr-xr-x  2 sebastian sebastian    4096 2010-01-13 17:54 .nautilus
drwx------  6 sebastian sebastian    4096 2010-03-20 09:06 .nx
-rw-r--r--  1 sebastian sebastian       0 2010-02-21 09:34 ny fil~
-rwxr--r--  1 sebastian sebastian 1049524 2009-12-07 20:52 Omslag saknas.pdf
drwxr-xr-x  3 sebastian sebastian    4096 2010-01-14 16:58 .openoffice.org
drwx------ 15 sebastian sebastian    4096 2010-03-13 08:42 .opera
drwx------  4 sebastian sebastian    4096 2010-01-21 21:55 .personal
drwx------  3 sebastian sebastian    4096 2010-02-19 13:38 .pki
-rw-r--r--  1 sebastian sebastian     675 2010-01-13 17:52 .profile
drwx------  2 sebastian sebastian    4096 2010-03-20 16:42 .pulse
-rw-------  1 sebastian sebastian     256 2010-01-13 17:54 .pulse-cookie
drwxr-xr-x  2 sebastian sebastian    4096 2010-03-14 10:13 .qt
-rw-------  1 sebastian sebastian    2235 2010-03-13 08:54 .recently-used
-rw-------  1 sebastian sebastian  178696 2010-03-20 11:06 .recently-used.xbel
drwxr-xr-x  5 sebastian sebastian    4096 2010-02-20 19:00 .screenlets
drwxr-xr-x  6 sebastian sebastian    4096 2010-03-19 11:47 Skrivbord
drwxr-xr-x  2 sebastian sebastian    4096 2010-01-31 12:15 .smb
drwx------  2 sebastian sebastian    4096 2010-03-14 11:02 .ssh
-rw-r--r--  1 sebastian sebastian       0 2010-01-13 17:58 .sudo_as_admin_successful
drwxr-xr-x 21 sebastian sebastian    4096 2010-02-20 15:55 .themes
drwx------  4 sebastian sebastian    4096 2010-01-13 17:56 .thumbnails
drwxr-xr-x  2 sebastian sebastian    4096 2010-01-13 18:41 .tsclient
-rwxr--r--  1 sebastian sebastian  174058 2009-12-07 21:44 Undertexter.pdf
drwxr-xr-x  2 sebastian sebastian    4096 2010-01-13 17:55 .update-manager-core
drwx------  2 sebastian sebastian    4096 2010-02-12 15:33 .update-notifier
-rw-r--r--  1 sebastian sebastian   10801 2010-03-05 23:22 .usbcreator.log
drwxr-xr-x 11 sebastian sebastian    4096 2010-03-18 18:26 Windows
drwxr-xr-x  4 sebastian sebastian    4096 2010-03-19 08:55 .wine
drwxr-xr-x 11 sebastian sebastian    4096 2010-01-31 12:13 .xbmc
drwxr-xr-x  2 sebastian sebastian    4096 2010-02-12 15:35 .xinput.d
-rw-------  1 sebastian sebastian    5970 2010-03-20 16:55 .xsession-errors
-rw-------  1 sebastian sebastian   48925 2010-03-20 11:06 .xsession-errors.old


```

---

### Post by Morbius1 on 2010-03-20
> Why doesnt it say that Ive have writing permissions?It does:
> [Home]
    path = /home/sebastian/
[COLOR=Blue]    read only = No[/COLOR]
    guest only = Yes
    guest ok = Yes
[COLOR=Blue]read only =No[/COLOR] is the same as writable = Yes

What I should have told you in my last post is that testparm does two things: It does a test of your smb.conf file to see if there are any errors in it and then it prints your smb.conf file as samba would interpret it when it runs for real.

You'll should also have noticed that testparm gave you an error meaasage:
> Global parameter guest account found in service section!> [Home]
writable = yes
path = /home/seb/
public = yes
guest ok = yes
guest only = yes
[COLOR=Blue]guest account = nobody[/COLOR]
browsable = yesguest account = nobody doesn't belong in the share portion of smb.conf, it belongs in the [global] portion. It didn't do any harm though as you can see from testparm, samba simply ignored it.

Also:
> [Hämtningar]
[COLOR=Blue]path = /home/sebbastian/down[/COLOR]
writable = yes
[COLOR=Blue]path = /home/sebastian/[/COLOR]
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yesYou can only have one path.

Back to the original problem:
> drwxr-xr-x 57 sebastian sebastian    4096 2010-03-20 16:42You've told Samba to allow for guest's to write to the share. But Linux file permissions is only allowing guests ( others in linux terms ) to read. If you really want to share your home directory to guests then you need to do one of two things:

(1) Change the permissions of your home folder to allow anyone to read and write ( add / delete ):

[B]chmod 0777 /home/sebastian

[/B](2) OR, Add a line to your [Home] section:
```
force user = sebastian
```What "force user" will do is convert the "guest" to "sebastian" for that share and give guest not only permission to add / delete to that share but also gives them permission to alter any files that are there.

---

### Post by 8301 on 2010-03-20
Thanx it worked

By the way does 

interfaces = lo eth0
bind interfaces only = yes

in smb.conf close my network for outsiders?

---

### Post by Morbius1 on 2010-03-20
I don't think so. What you want is to add the following parameter to each share:

```
hosts allow = xyz
```"xyz" can take many forms. Examples:
    
hosts allow =  192.168.0.
Allows everyone behind your router ( assuming your router allocates ip address in the 192.168.0.xxx range ) to have access.

hosts allow = 192.168.0. EXCEPT 192.168.0.102
Allows everyone except 192.168.0.102 to gain access

hosts allow = mach1, mach2
You can use netbios or machine names instead of ip address

Just to name a few.

---


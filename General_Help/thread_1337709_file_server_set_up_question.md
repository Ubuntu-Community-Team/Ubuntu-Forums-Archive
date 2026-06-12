---
title: "file server set up question"
date: 2009-11-25
forum: General Help
---

### Post by keevill on 2009-11-25
I want to set up a file server for a mixed os workgroup - linux/winxp/vista.
Do I need to go for Ubuntu Server or can I just use a desktop version and configure Samba on that.
I confess I have been trying to set up Ubuntu Server with Webadmin but even though it seems easy, I am having difficulties with permissions etc.
I don't need domain controller or ftp etc just a simple file server is what I am trying to set up.
There are about 50 users in this workgroup.

---

### Post by juancarlospaco on 2009-11-25
50 users or more needs performance, i recommend ubuntu server,
if you cant configure via CLI, just install a basic gnome desktop,
and disable GDM autostart to stay on CLI at boot, install openssh-server,
when you need to configure something logon and startx,
or even use 
ssh -X user@ip program

---

### Post by bodhi.zazen on 2009-11-25
> **keevill said:**
> I want to set up a file server for a mixed os workgroup - linux/winxp/vista.
Do I need to go for Ubuntu Server or can I just use a desktop version and configure Samba on that.
I confess I have been trying to set up Ubuntu Server with Webadmin but even though it seems easy, I am having difficulties with permissions etc.
I don't need domain controller or ftp etc just a simple file server is what I am trying to set up.
There are about 50 users in this workgroup.

perhaps if you were to explain what problem you are having.

Personally, with 50 ysers, I would aslo go Ubuntu Server and run headless, but you need to be comfortable with configuration from the command line.

Since 99 % of server configuration involves editing a text file I find it easier to use ssh then webmin.

[Samba Server]("https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html#id2540411")

---

### Post by keevill on 2009-11-25
This confirms what I already believed in that I need server for that number of users.

What I am trying to achieve is really quite simple and I am surprised by my lack of success.
Webadmin is very easy to use.
All I want to do is to set up about 3 folders for read/write access for certain users.
i.e. folder A is r/w for users 1-7 and folder B is r/w for users 8-14 etc.

However when I try to do this, either no users can write or some users can read but not write  folders which they shouldn't be able to access.
Been tinkering around for ages with this. Figured out that it takes about 2 mins for changes to be applied on server but even now I am not able to set it up correctly.
Can you point me in the write ( excuse pun ) direction ?
Thx

---

### Post by bodhi.zazen on 2009-11-25
The link I gave you goes right to the relevant section of the wiki.

If you need more specific help, please post the relevant section of your samba config file and explain how you have set up your users.

---

### Post by keevill on 2009-11-26
All I want to do is the following
set up a file server with sharefolder1 sharefolder2 and sharefolder3
Give read/write access to sharefolder1 to userA , userB userC
Give read/write access to sharefolder2 to userD
Give no access including view to sharefolder3 except to userZ ,userY and userX
It's not a pdc or print server etc
In a mix of Linux and Win clients.
Playing around now for a day or so , all I can do is either give total read/write access to anyone without being challenged for authentication or no access whatsoever.
In my setup I have done the following
made a shared folder called public
made 3 users 'ning' 'bee' & 'david'
tried to give access to public either one or all  of them 
but can't get it to work .
It looks so simple but it's defeating me so far.
I paste below content of my conf file and smbusers file.
Hope this enables you to help.
Many thanks,
________________

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
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	writeable = yes
	server string = %h server (Samba, Ubuntu)
	path = /media
	unix password sync = yes
	workgroup = WORKGROUP
	os level = 20
	security = user
        username map = /etc/samba/smbusers
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections

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
;   printing = cups
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
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones

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
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	browseable = yes
	comment = Printer Drivers
	write list = bee
	path = /var/lib/samba/printers
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
[public]
 comment = Public Folder
 path = /home/public
 public = yes
 writable = yes
 create mask = 0777
 directory mask = 0777
# force user = nobody
# force group = nogroup
 guest ok = yes
 browseable = Yes
 admin users = ning,bee
 security = user
 
 

[test]
	valid users = bee
______________________
Smbusers

system_username = "bee"
system_username = "ning"
system_username = "david"

---

### Post by bodhi.zazen on 2009-11-26
When posting config files, please either post the relevant section or post it as an attachment. They are very long ...

In your case, post your shares. I do not see where you have defined a share.

what problem are you having with that share ?

---

### Post by keevill on 2009-11-26
> **bodhi.zazen said:**
> When posting config files, please either post the relevant section or post it as an attachment. They are very long ...

In your case, post your shares. I do not see where you have defined a share.

what problem are you having with that share ?

apologies for posting long config files - I was unsure of how to do so - 
I have simply made a share called 'public' 
{sudo mkdir public} in the 'home' dir.
At the end of the config file is this entry
comment = Public Folder
path = /home/public
public = yes
writable = yes
create mask = 0777
directory mask = 0777
# force user = nobody
# force group = nogroup
guest ok = yes
browseable = Yes
admin users = ning,bee
security = user

Is that what you need to know ?
Sorry to be dumb - but I am fairly new to this .

---

### Post by bodhi.zazen on 2009-11-26
Posting your config file is not a problem, just indicating to you the preferred method.

What problem are you having with that share ?

---

### Post by keevill on 2009-11-26
> **bodhi.zazen said:**
> Posting your config file is not a problem, just indicating to you the preferred method.

What problem are you having with that share ?

Right now, it can be accessed by anybody - no challenge for authorisation.
I've played around with many different settings in the conf file but am only able to achieve full access to all or no access to anyone.
The current status according to the posted conf file gives unchallenged access to all- windows or linux machines.

---

### Post by bodhi.zazen on 2009-11-26
That is probably due to the "guest ok = yes" option in your config file.

See :

[https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration)

---

### Post by keevill on 2009-11-26
> **bodhi.zazen said:**
> That is probably due to the "guest ok = yes" option in your config file.

See :

[https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Manual%20Configuration)

I'm fairly sure that I tried removing this option but then no access was available to anyone. I cannot be sure till I get to the office in a few hours and try  - will post back- thx for your continued help.

---

### Post by bodhi.zazen on 2009-11-26
Samba is frustrating to start, but once it clicks it is straight forward.

The pitfalls are :

1. Permissions. There are system users, users who may log into the server, and there are samba users. See the second link I gave you. System users must have permission to access the shared directory.

So if you make a directory, /home/share , who owns this directory ? root ? do the other users have the rights to access this share ?

Furthermore , group shares are a bit more complex =)

2. Firewalls. Make sure you are not firewalling your connection attempts.

At the end of the day, it is a moderately long text file. Read through the examples and it will come.

---

### Post by keevill on 2009-11-28
In the end , I sorted it.
Setup afresh and did it command line rather than web admin gui.
The only way to learn really.
chmod commands were the key .
thx,

---


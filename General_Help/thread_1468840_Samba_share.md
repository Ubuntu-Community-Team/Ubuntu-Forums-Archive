---
title: "Samba share"
date: 2010-05-01
forum: General Help
---

### Post by Zer0d on 2010-05-01
I'm trying to make a folder that anybody can access but I only get permission denied or username/password is wrong.

I want the share to be totally open for any windows machine in my LAN to access.

My smb.conf, only uncommented lines:
```

[global]
## Browsing/Identification ###
	workgroup = workgroup
	server string = %h server (Samba, Ubuntu)
	dns proxy = no
#### Debugging/Accounting ####
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
####### Authentication #######
	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	map to guest = bad user
############ Misc ############
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
	guest ok = yes
#======================= Share Definitions =======================
[Storage]
	path = /media/Storage_
	writeable = yes
	browseable = yes
	guest ok = yes

```

Whole smb.con with all commented lines:
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
	workgroup = workgroup

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

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
	username map = /etc/samba/smbusers
	security = user
	guest ok = yes
;	guest account = nobody

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

;[printers]
;	comment = All Printers
;	browseable = no
;	path = /var/spool/samba
;	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers

[Storage]
	path = /media/Storage_
	writeable = yes
;	browseable = yes
	guest ok = yes

```

Is there a way I can reset the config file back to defaults, I guess it could be a bit messed up now?

---

### Post by Morbius1 on 2010-05-01
Actually, your smb.conf doesn't look that bad. Although there is something I've never seen before.

If you open a Terminal and type: **testparm -s**
Two things will happen:
(1) It will "interpret" the smb.conf as though it was actually going to run it and output errors if it finds anything odd.
(2) The second thing it does is outputs the interpreted smb.conf without all the comments.

When I run testparm against your commented smb.conf I get this for the Storage share:
> [Storage]
    path = /media/Storage_
    read only = No
But the smb.conf file has this:
> [Storage]
    path = /media/Storage_
    writeable = yes
    browseable = yes
    [COLOR=Blue]guest ok = yes[/COLOR]I don't know why but the [COLOR=Blue]guest ok = yes[/COLOR] is being totally ignored by Samba.

What I would do is this. I would first delete the Storage share and restart samba. To restart samba:

If your using 9.10 or earlier: **sudo service samba restart**
If your using 10.04 it's back to the olden days:
**sudo service smbd restart**
**sudo service nmbd restart**

Then I would create the share using Nautilus-share:

Open Nautilus
Right Click /media/Storage
Select "Sharing Options"
Select Share this folder, Allow other people to write..., and Guest access
Select Create Share.

And see if you can access the share.

There is one, maybe two more stumbling blocks:

(1) Is it really /media/Storage_ with an underscore at the end ?
(2) Is /media/Storage a FAT32 or NTFS formatted partition because it may be a linux file permissions problem as well.

---

### Post by Morbius1 on 2010-05-01
Well, I finally figured out why guest ok = yes is not in the Storage share in smb.conf. You also have that line in the [global] section of smb.conf. You need to remove that line and restart samba again.

Go into smb.conf and find these lines:
> # Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    security = user
    guest ok = yes
;    guest account = nobodyPut a # in front of the guest line so it looks like this:
> # Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    security = user
# guest ok = yes
;    guest account = nobody

I would still delete the share in smb.conf and use nautilus-share since your needs are so simple.

---

### Post by Zer0d on 2010-05-01
> **Morbius1 said:**
> Actually, your smb.conf doesn't look that bad. Although there is something I've never seen before.

If you open a Terminal and type: **testparm -s**
Two things will happen:
(1) It will "interpret" the smb.conf as though it was actually going to run it and output errors if it finds anything odd.
(2) The second thing it does is outputs the interpreted smb.conf without all the comments.

When I run testparm against your commented smb.conf I get this for the Storage share:
But the smb.conf file has this:
I don't know why but the [COLOR=Blue]guest ok = yes[/COLOR] is being totally ignored by Samba.

What I would do is this. I would first delete the Storage share and restart samba. To restart samba:

If your using 9.10 or earlier: **sudo service samba restart**
If your using 10.04 it's back to the olden days:
**sudo service smbd restart**
**sudo service nmbd restart**

Then I would create the share using Nautilus-share:

Open Nautilus
Right Click /media/Storage
Select "Sharing Options"
Select Share this folder, Allow other people to write..., and Guest access
Select Create Share.

And see if you can access the share.

There is one, maybe two more stumbling blocks:

(1) Is it really /media/Storage_ with an underscore at the end ?
(2) Is /media/Storage a FAT32 or NTFS formatted partition because it may be a linux file permissions problem as well.

Thanks for your replay :)
(1) The name Storage_ was automatically made when mounting my disk because the folder named Storage already existed. I have now deleted Storage_ so Ubuntu automatically mounts the drive to Storage.
(2) The drive is NTFS partitioned.


I get pretty much the same when running **testparm -s**
```

[Storage]
	path = /media/Storage
	read only = No

```
Strange that there are many lines it doesn't parse from the config file, like:
```

[Storage]
        available = yes
        writeable = yes
        browseable = yes

```

When sharing through Nautilus, I still get username/password prompt.

Really late now so I have to look more into this tomorrow, appreciate your help :)

---

### Post by garvinrick4 on 2010-05-01
gksudo gedit /etc/samba/smb.conf  
 

 

 Find this section in the file:  
 ####### Authentication #######  
 # “security = user” is always a good idea. This will require a Unix account  
 # in this server for every user accessing the server. See  
 # /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html 
 # in the samba-doc package for details. 
 #security = user  
 

 

 Uncomment the security line, and add another line to make it look like this:  
 security = user  
 username map = /etc/samba/smbusers

---

### Post by Zer0d on 2010-05-01
> **Morbius1 said:**
> Well, I finally figured out why guest ok = yes is not in the Storage share in smb.conf. You also have that line in the [global] section of smb.conf. You need to remove that line and restart samba again.

Go into smb.conf and find these lines:
Put a # in front of the guest line so it looks like this:


I would still delete the share in smb.conf and use nautilus-share since your needs are so simple.

Ah yea, totally forgot that I tried to change that option before. Was like a desperate thing to try to get the share to work. I could possible have messed up other things in the config file too. Getting access/permission denied now on the share. I will figure this out somehow tomorrow, at least you have given me some guidelines :) I could probably just disable samba and use Nautilus if I wont get Samba working.

---

### Post by Zer0d on 2010-05-01
Current configuration now:

**testparm -s**:
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	create mask = 0700

[Storage]
	path = /media/Storage
	read only = No
	guest ok = Yes

```

Current **smb.conf**:
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
	workgroup = workgroup

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
	security = user
	username map = /etc/samba/smbusers
# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

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
#	guest ok = yes
;	guest account = nobody

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

;[printers]
;	comment = All Printers
;	browseable = no
;	path = /var/spool/samba
;	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers

[Storage]
	path = /media/Storage
	writeable = yes
	browseable = yes
	guest ok = yes

```

Getting **Network access is denied.** from Windows machine.

---

### Post by Morbius1 on 2010-05-01
Is /media/Storage an external USB storage device formatted in NTFS or FAT32?

[COLOR=Blue]EDIT: After you've rested post the output of the following commands please:[/COLOR]

```
net userhare info
ls -dl /media/Storage
```If the linux file permissions do not allow "others" to read and write to that folder than no matter how hard samba tries to allow guest access it ain't going to happen - you will get access denied errors. An external USB FAT32 or NTFS device almost guarantees this type of situation but it could also happen to an internal partition.

Your smb.conf looks fine to me although it is getting late here also so I could have missed something. I'm betting it's a linux file permissions problem.

---

### Post by Zer0d on 2010-05-02
> **Morbius1 said:**
> Is /media/Storage an external USB storage device formatted in NTFS or FAT32?

[COLOR=Blue]EDIT: After you've rested post the output of the following commands please:[/COLOR]

```
net userhare info
ls -dl /media/Storage
```If the linux file permissions do not allow "others" to read and write to that folder than no matter how hard samba tries to allow guest access it ain't going to happen - you will get access denied errors. An external USB FAT32 or NTFS device almost guarantees this type of situation but it could also happen to an internal partition.

Your smb.conf looks fine to me although it is getting late here also so I could have missed something. I'm betting it's a linux file permissions problem.

It's an NTFS drive. Internal 1TB HDD.

net usershare info:
```

root@myusername-desktop:~# net usershare info
[storage]
path=/media/Storage
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

ls -dl info:
```
root@myusername-desktop:~# ls -dl /media/Storage/
drwx------ 1 myusername myusername 28672 2010-05-01 21:37 /media/Storage/
```

---

### Post by Morbius1 on 2010-05-02
2 things:

(1) There are two completely different ways to share folders in Ubuntu - Nautilus-share and Classic-share. You're using both methods on the same target directory:

This is Nautilus-share:
> [storage]
path=/media/Storage
comment=
usershare_acl=Everyone:F,
guest_ok=yThis is Classic-share:
> [Storage]
    path = /media/Storage
    read only = No
    guest ok = YesIt's best to use one method or the other. It's easier to delete the nautilus share.

(2)
> drwx------ 1 myusername myusername 28672 2010-05-01 21:37 /media/Storage/As I guessed the problem isn't samba it's linux file permissions. Only "myusername" can access the target folder and overrules whatever samba is allowing.

This is what I suggest:

***Step 1: Remove the Nautilus-share***

Go back into Nautilus and "unshare" /media/Storage.

***Step 2: Add a line to the share definition for /media/Storage in smb.conf:***
```
force user = myusername
```So thet the share definition looks like this:
> [Storage]
    path = /media/Storage
    read only = No
[COLOR=Blue]force user = myusername[/COLOR]
    guest ok = YesThen restart samba.

"force user" will act as a mask and convert the remote user to *myusername* as far as that share is concerned. Right now only one user has access to "Storage" and that's myusername.

---


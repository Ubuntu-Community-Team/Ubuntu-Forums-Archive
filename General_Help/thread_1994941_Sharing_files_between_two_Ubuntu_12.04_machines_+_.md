---
title: "Sharing files between two Ubuntu 12.04 machines + Windows"
date: 2012-06-03
forum: General Help
---

### Post by AnotherMuggle on 2012-06-03
Please can someone help me get my two Ubuntu 12.04 machines (and eventually Windows) talking to one another?

I have followed numerous guides online to set up and configure Samba but I'm getting nowhere fast.  I seem to have different symptoms each time I try and have so far never managed to get files from one machine visible on another.

I followed ([this guide]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/")) closely and have followed up with a variety of config changes from other sites...nothing appears to work :(

I mostly get one of two issues:
1) Machines cannot see one another and list only their own printers and share folders in the Windows Network folder.
2) Machines can see one another but clicking on them in Windows Network folder causes the folder to sit with a loading icon for a few seconds then says "Unable to mount location Failed to retireve share list from server".

Note: I have not entered Windows into the equation just yet, I am still trying to get the two Ubuntu machines talking to one another.

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> Please can someone help me get my two Ubuntu 12.04 machines (and eventually Windows) talking to one another?

I have followed numerous guides online to set up and configure Samba but I'm getting nowhere fast.  I seem to have different symptoms each time I try and have so far never managed to get files from one machine visible on another.

I followed ([this guide]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/")) closely and have followed up with a variety of config changes from other sites...nothing appears to work :(

I mostly get one of two issues:
1) Machines cannot see one another and list only their own printers and share folders in the Windows Network folder.
2) Machines can see one another but clicking on them in Windows Network folder causes the folder to sit with a loading icon for a few seconds then says "Unable to mount location Failed to retireve share list from server".

Note: I have not entered Windows into the equation just yet, I am still trying to get the two Ubuntu machines talking to one another.

The site you linked to is sooooo wrong.  Before you can do anything you need to remove all of the apps the the article referred to.  In other words, return the system back to the defaults you had before.

> [COLOR="RoyalBlue"][SIZE="3"]Configuring Winbind[/SIZE][/COLOR]

You do not need winbind.  It is one of the reasons you are having problems.  Later on the writer mentions **[COLOR="Red"][SIZE="2"]WINS[/SIZE][/COLOR]**.  WINS has nothing to do with winbind.  You don't need either service anyway.

Once again, my suggestion is to remove all the Samba apps you installed and start over.  [**_[COLOR="DarkSlateGray"]Here[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1168") is an excellent howto that works!

---

### Post by AnotherMuggle on 2012-06-03
Thanks for responding.  I am now reverting back all changes I've made to my two systems, those on that site and config changes I found elsewhere.  

Times like this I am glad I am systematic about my changes and keep a record of everything I do to my system.

I will try the method you linked and report back.

Thanks again!

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> Thanks for responding.  I am now reverting back all changes I've made to my two systems, those on that site and config changes I found elsewhere.  

Times like this I am glad I am systematic about my changes and keep a record of everything I do to my system.

I will try the method you linked and report back.

Thanks again!

Use```
sudo apt-get purge <package>
```

Substitute the app (package) that you are removing for <package>.

---

### Post by AnotherMuggle on 2012-06-03
> **bab1 said:**
> Use```
sudo apt-get purge <package>
```

Substitute the app (package) that you are removing for <package>.

Yep, I used that to remove the individual packages followed by:
```
sudo apt-get --purge autoremove
```
to remove the old dependencies.

If I look in /etc/samba then the old config files are still there, is this normal?  Should I remove them manually?

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> Yep, I used that to remove the individual packages followed by:
```
sudo apt-get --purge autoremove
```
to remove the old dependencies.

If I look in /etc/samba then the old config files are still there, is this normal?  Should I remove them manually?

No you do not need to remove them.  They are easily edited.  I believe they are reinstalled with the package ***samba-common***.  if you are using 12.04 this package is (as I recall) now called ***cifs-utils***

---

### Post by AnotherMuggle on 2012-06-03
> **bab1 said:**
> No you do not need to remove them.  They are easily edited.  I believe they are reinstalled with the package ***samba-common***.  if you are using 12.04 this package is (as I recall) now called ***cifs-utils***

OK I removed everything from the first guide and followed the guide you posted but I don't see much (any?) improvement.

One machine is listing the other machines on the network but clicking on them tells me "Unable to mount location Failed to retireve share list from server" whereas the other one doesn't list any other machines in Windows Network folder at all.

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> OK I removed everything from the first guide and followed the guide you posted but I don't see much (any?) improvement.

One machine is listing the other machines on the network but clicking on them tells me "Unable to mount location Failed to retireve share list from server" whereas the other one doesn't list any other machines in Windows Network folder at all.
Did you restore the settings in the nsswitch.conf file?

Also, find this line in the smb.conf file```
;   name resolve order = lmhosts host wins bcast
```

Edit it to look like this```
 name resolve order =  bcast
```

---

### Post by AnotherMuggle on 2012-06-03
> **bab1 said:**
> did you restore the settings in the nsswitch.conf file?

Also, find this line in the smb.conf file```
;   name resolve order = lmhosts host wins bcast
```

Edit it to look like this```
 name resolve order =  bcast
```

I removed the "wins" part because the rest of the options were already there.  Before adding wins and now, it looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

I will try changing it to your version to see what I get.

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> I removed the "wins" part because the rest of the options were already there.  Before adding wins and now, it looks like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

I will try changing it to your version to see what I get.

You will need to restart the smbd daemon each time we edit the smb.conf file like this```
sudo service smbd restart
```

---

### Post by AnotherMuggle on 2012-06-03
> **bab1 said:**
> You will need to restart the smbd daemon each time we edit the smb.conf file like this```
sudo service smbd restart
```

Yep, I have been running that along with
```
sudo service nmbd restart
```

still no change :(

AH HA, now one machine can see and browse the other... but not the other way around.

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> Yep, I have been running that along with
```
sudo service nmbd restart
```

still no change :(

AH HA, now one machine can see and browse the other... but not the other way around.

Edit the other machines smb.conf file.

---

### Post by AnotherMuggle on 2012-06-03
> **bab1 said:**
> Edit the other machines smb.conf file.

Amazing, both machines appear to be working :D

Thanks very much for your help!

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> Amazing, both machines appear to be working :D

Thanks very much for your help!

Great.  Your pretty familiar with Linux.  You were just misled by that bad tut.


Edit:  If you have multiple users you may still have permissions and ownership problems.  We can fix that too.

---

### Post by AnotherMuggle on 2012-06-03
> **bab1 said:**
> Great.  Your pretty familiar with Linux.  You were just misled by that bad tut.


Edit:  If you have multiple users you may still have permissions and ownership problems.  We can fix that too.

At the moment it's just me.  I just want to be able to get access to files on my desktop from my netbook, and vice-versa, without having to keep going back and forth with a USB stick.

Both machines are dual boot with Windows 7 so I will need to add that to the mix at some point.  If I need to do anything special to get that working then fire away otherwise I think I'm good to go.  Thanks again.

---

### Post by bab1 on 2012-06-03
> **AnotherMuggle said:**
> At the moment it's just me.  I just want to be able to get access to files on my desktop from my netbook, and vice-versa, without having to keep going back and forth with a USB stick.

Both machines are dual boot with Windows 7 so I will need to add that to the mix at some point.  If I need to do anything special to get that working then fire away otherwise I think I'm good to go.  Thanks again.

The Windows machines will work with this configuration just fine.

---

### Post by n.hinton on 2012-06-11
Same situation (2 x 12.04's), but my two still cant see one another!

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> Same situation (2 x 12.04's), but my two still cant see one another!

This doesn't tell us much. There are be multiple problems that result in the same symptoms.  Describe what you have as far as install and configuration.  Post the output of ```
cat /etc/samba/smb.conf
```

Post the output of```
smbtree -d3
```

Post the output between the [code] tags (use the # icon for this).

---

### Post by n.hinton on 2012-06-11
One is an old pc upgraded since jaunty, now at 12.04, the other is a fresh 12.04 install and wanted to be able to share files with the old pc, both apear to comply with the sugestions and the good tutorial mentioned in this thread. 

Niether see each other in browse network, they can ping each other though.

```
kingfisher@GX620:~$ cat /etc/samba/smb.conf
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
	workgroup = gx620
	netbios name = new_gx620
# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)
	null passwords = yes

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
	name resolve order = bcast

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

;	bind interfaces only = no
# ADD THE ETHERNET CARD AND IP ADDRESSES YOU ALLOW
	interfaces = wlan0 127.0.0.0/8 192.168.1.0/24

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
;	guest ok = no
;	guest account = nobody

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
[test]
	path = /home/kingfisher/test
	available = yes
	writeable = yes
	browseable = yes
	guest ok = yes
kingfisher@GX620:~$ 

```
```
kingfisher@GX620:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "null passwords" option is deprecated
added interface wlan0 ip=fe80::21f:1fff:feac:58d6%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.64 bcast=192.168.1.255 netmask=255.255.255.0
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: using netmask value 24 from config file on interface wlan0
add_interface: not adding duplicate interface 192.168.1.64
Enter kingfisher's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1d>
Got a positive name query response from 127.0.0.1 ( 192.168.1.64 )
Connecting to host=192.168.1.64
Connecting to 192.168.1.64 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 127.0.0.1 ( 192.168.1.64 )
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1d>
Got a positive name query response from 127.0.0.1 ( 192.168.1.64 )
Connecting to host=192.168.1.64
Connecting to 192.168.1.64 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
GX620
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1d>
Got a positive name query response from 127.0.0.1 ( 192.168.1.64 )
Connecting to host=192.168.1.64
Connecting to 192.168.1.64 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\NEW_GX620      		GX620 server (Samba, Ubuntu)
Connecting to host=NEW_GX620
name_resolve_bcast: Attempting broadcast lookup for name NEW_GX620<0x20>
Got a positive name query response from 127.0.0.1 ( 192.168.1.64 )
Connecting to 192.168.1.64 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\NEW_GX620\IPC$           	IPC Service (GX620 server (Samba, Ubuntu))
		\\NEW_GX620\test           	
		\\NEW_GX620\print$         	Printer Drivers
kingfisher@GX620:~$ 

```
(the old pc's ip is 192.168.1.65)

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> One is an old pc upgraded since jaunty, now at 12.04, the other is a fresh 12.04 install and wanted to be able to share files with the old pc, both apear to comply with the sugestions and the good tutorial mentioned in this thread. 

Niether see each other in browse network, they can ping each other though.

```
kingfisher@GX620:~$ cat /etc/samba/smb.conf
...
# What naming service and in what order should we use to resolve host names
# to IP addresses
	name resolve order = bcast

...
[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

...
[test]
	path = /home/kingfisher/test
	available = yes
	writeable = yes
	browseable = yes
	guest ok = yes
kingfisher@GX620:~$ 



```
```
kingfisher@GX620:~$ smbtree -d3
...
	\\NEW_GX620      		GX620 server (Samba, Ubuntu)
Connecting to host=NEW_GX620
[COLOR="Red"]name_resolve_bcast: Attempting broadcast lookup for name NEW_GX620<0x20>
Got a positive name query response from 127.0.0.1 ( 192.168.1.64 )
Connecting to 192.168.1.64 at port 445[/COLOR]
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
[COLOR="Red"]		\\NEW_GX620\IPC$           	IPC Service (GX620 server (Samba, Ubuntu))
		\\NEW_GX620\test           	
		\\NEW_GX620\print$         	Printer Drivers[/COLOR]
kingfisher@GX620:~$ 

```
(the old pc's ip is 192.168.1.65)
This all seems to be working on this host.  What do you get from 192.168.1.65?

Were both hosts on when you did this test?  It appears that the host **NEW_GX620 **is broadcasting its NETBIOS name and its shares (see red above), but I don't see any broadcasts for 192.168.1.65

You have made two changes that I would comment out for the time being.  These are```

	null passwords = yes

# ADD THE ETHERNET CARD AND IP ADDRESSES YOU ALLOW
	interfaces = wlan0 127.0.0.0/8 192.168.1.0/24

```

---

### Post by n.hinton on 2012-06-11
yes both machines were on, the old pc ip 192.168.1.65 yealded these results:
```
kingfisher@kingfisher-desktop:~$ cat /etc/samba/smb.conf
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
	workgroup = gx620
	netbios name = network
# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)
	null passwords = yes

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
	name resolve order = bcast

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

;	bind interfaces only = no
# ADD THE ETHERNET CARD AND IP ADDRESSES YOU ALLOW
	interfaces = wlan0 127.0.0.0/8 192.168.1.0/24

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
;	guest ok = no
;	guest account = nobody

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
[test]
	path = /home/kingfisher/test
;	available = yes
	writeable = yes
;	browseable = yes
	guest ok = yes

[root directory]
	comment = root directory old pc
	path = /
	writeable = yes
;	browseable = yes
	guest ok = yes

[home]
	path = /home
	writeable = yes
;	browseable = yes
	guest ok = yes
	comment = home old pc
kingfisher@kingfisher-desktop:~$
```

```
kingfisher@kingfisher-desktop:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
WARNING: The "null passwords" option is deprecated
added interface wlan0 ip=fe80::222:b0ff:fe6f:6bcb%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.65 bcast=192.168.1.255 netmask=255.255.255.0
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: using netmask value 24 from config file on interface wlan0
add_interface: not adding duplicate interface 192.168.1.65
Enter kingfisher's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1d>
Got a positive name query response from 127.0.0.1 ( 192.168.1.65 )
Connecting to host=192.168.1.65
Connecting to 192.168.1.65 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 127.0.0.1 ( 192.168.1.65 )
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1d>
Got a positive name query response from 127.0.0.1 ( 192.168.1.65 )
Connecting to host=192.168.1.65
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
GX620
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1d>
Got a positive name query response from 127.0.0.1 ( 192.168.1.65 )
Connecting to host=192.168.1.65
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\NETWORK        		kingfisher-desktop server (Samba, Ubuntu)
Connecting to host=NETWORK
name_resolve_bcast: Attempting broadcast lookup for name NETWORK<0x20>
Got a positive name query response from 127.0.0.1 ( 192.168.1.65 )
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\NETWORK\neil           	
		\\NETWORK\yvonne         	
		\\NETWORK\public         	
		\\NETWORK\Lexmark--2200-Series	Lexmark  2200 Series
		\\NETWORK\Generic-CUPS-PDF-Printer	Generic CUPS-PDF Printer
		\\NETWORK\DESKJET-840C   	HEWLETT-PACKARD DESKJET 840C
		\\NETWORK\DESKJET-840C-Photo	HEWLETT-PACKARD DESKJET 840C
		\\NETWORK\IPC$           	IPC Service (kingfisher-desktop server (Samba, Ubuntu))
		\\NETWORK\home           	home old pc
		\\NETWORK\root directory 	root directory old pc
		\\NETWORK\test           	
		\\NETWORK\print$         	Printer Drivers
kingfisher@kingfisher-desktop:~$
```

edited smb.conf results on 192.168.1.64 machine results (can no longer browse its own shares due to 'can not retrieve shares message')

```
kingfisher@GX620:~$ sudo gedit /etc/samba/smb.conf
[sudo] password for kingfisher: 
kingfisher@GX620:~$ sudo restart smbd && sudo restart nmbd
smbd start/running, process 2903
nmbd start/running, process 2914
kingfisher@GX620:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::21f:1fff:feac:58d6%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.64 bcast=192.168.1.255 netmask=255.255.255.0
Enter kingfisher's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name GX620<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
kingfisher@GX620:~$ 

```

Sorry slow, having to shut both down to swap monitor over

---

### Post by bab1 on 2012-06-11
I'm surprised you don't have ssh installed on the host that has no monitor.  Never the less; as you have the resolve method set for broadcast and neither host can receive broadcasts from the other (only from itself), I would say that you have firewall(s) in the way.  Try disabling all firewalls and try again.

To summarize; with this configured: ***name resolve order = bcast ***, all hosts on the local subnet should respond to the query *name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1> *and there should be only one *MSBROWSE* per network holding all the NETBIOS names of all the hosts.

---

### Post by n.hinton on 2012-06-11
Thats a surprise to me I thought it had, fire walls are disabled on both machines.

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> Thats a surprise to me I thought it had, fire walls are disabled on both machines.

What do you get with this (from either machine)```
ping -b 192.168.1.255
```

---

### Post by n.hinton on 2012-06-11
```
kingfisher@GX620:~$ ping -b 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
64 bytes from 192.168.1.253: icmp_req=1 ttl=64 time=5.19 ms
64 bytes from 192.168.1.253: icmp_req=2 ttl=64 time=5.46 ms
64 bytes from 192.168.1.253: icmp_req=3 ttl=64 time=4.89 ms
64 bytes from 192.168.1.253: icmp_req=4 ttl=64 time=4.93 ms
64 bytes from 192.168.1.253: icmp_req=5 ttl=64 time=5.52 ms
64 bytes from 192.168.1.253: icmp_req=6 ttl=64 time=5.51 ms
64 bytes from 192.168.1.253: icmp_req=7 ttl=64 time=5.12 ms
64 bytes from 192.168.1.253: icmp_req=8 ttl=64 time=5.11 ms
64 bytes from 192.168.1.253: icmp_req=9 ttl=64 time=5.14 ms
64 bytes from 192.168.1.253: icmp_req=10 ttl=64 time=5.61 ms
64 bytes from 192.168.1.253: icmp_req=11 ttl=64 time=5.01 ms
64 bytes from 192.168.1.253: icmp_req=12 ttl=64 time=4.81 ms
64 bytes from 192.168.1.253: icmp_req=13 ttl=64 time=5.01 ms
64 bytes from 192.168.1.253: icmp_req=14 ttl=64 time=5.01 ms
64 bytes from 192.168.1.253: icmp_req=15 ttl=64 time=5.26 ms
64 bytes from 192.168.1.253: icmp_req=16 ttl=64 time=5.08 ms
64 bytes from 192.168.1.253: icmp_req=17 ttl=64 time=5.02 ms

```

Etc. from 192.168.1.64 machine. get back to you about old one

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> ```
kingfisher@GX620:~$ ping -b 192.168.1.255
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
64 bytes from 192.168.1.253: icmp_req=1 ttl=64 time=5.19 ms
64 bytes from 192.168.1.253: icmp_req=2 ttl=64 time=5.46 ms
64 bytes from 192.168.1.253: icmp_req=3 ttl=64 time=4.89 ms...

```

Etc. from 192.168.1.64 machine. get back to you about old one

That's okay.  It looks like broadcasts are working.  If you ping .64 from this host (.65) (or visa versa) what do you get.  What do you get from the command *arp*?

These two machines must communicate at via arp (MAC address resolution).  I'd like to see both hardware (Ethernet addresses).  If you ping the IP address and the issue an *arp* command you should see the Ethernet address (MAC address).

---

### Post by n.hinton on 2012-06-11
the same just slower

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> the same just slower

Post the results of from the machine that you normally use of this ```
arp 
```> 

You have a networking problem somewhere.  Could even be a hardware problem.  What devices connect these 2 hosts together?  Do you have a spare switch you can connect these two host together with?  You do not need a router for them to communicate with each other.

Edit: what is 192.168.1.253?  Is that your router?

---

### Post by n.hinton on 2012-06-11
```
kingfisher@GX620:~$ ping 192.168.1.65
PING 192.168.1.65 (192.168.1.65) 56(84) bytes of data.
64 bytes from 192.168.1.65: icmp_req=1 ttl=64 time=1830 ms
64 bytes from 192.168.1.65: icmp_req=2 ttl=64 time=824 ms
64 bytes from 192.168.1.65: icmp_req=3 ttl=64 time=36.7 ms
64 bytes from 192.168.1.65: icmp_req=4 ttl=64 time=56.4 ms
64 bytes from 192.168.1.65: icmp_req=5 ttl=64 time=56.7 ms
64 bytes from 192.168.1.65: icmp_req=6 ttl=64 time=56.5 ms
64 bytes from 192.168.1.65: icmp_req=7 ttl=64 time=23.9 ms
64 bytes from 192.168.1.65: icmp_req=8 ttl=64 time=8.13 ms
64 bytes from 192.168.1.65: icmp_req=9 ttl=64 time=62.2 ms
64 bytes from 192.168.1.65: icmp_req=10 ttl=64 time=66.0 ms
64 bytes from 192.168.1.65: icmp_req=11 ttl=64 time=66.2 ms
64 bytes from 192.168.1.65: icmp_req=12 ttl=64 time=67.1 ms
64 bytes from 192.168.1.65: icmp_req=14 ttl=64 time=203 ms
64 bytes from 192.168.1.65: icmp_req=15 ttl=64 time=70.9 ms
64 bytes from 192.168.1.65: icmp_req=16 ttl=64 time=26.8 ms
64 bytes from 192.168.1.65: icmp_req=17 ttl=64 time=48.9 ms
64 bytes from 192.168.1.65: icmp_req=19 ttl=64 time=69.9 ms
64 bytes from 192.168.1.65: icmp_req=20 ttl=64 time=70.9 ms
64 bytes from 192.168.1.65: icmp_req=21 ttl=64 time=30.5 ms

``` other the same exept for 192.168.1.64 ip

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> ```
kingfisher@GX620:~$ ping 192.168.1.65
PING 192.168.1.65 (192.168.1.65) 56(84) bytes of data.
64 bytes from 192.168.1.65: icmp_req=1 ttl=64 time=1830 ms
64 bytes from 192.168.1.65: icmp_req=2 ttl=64 time=824 ms
...

``` other the same exept for 192.168.1.64 ip

I want to see the output of ```
arp
```

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> ```
kingfisher@GX620:~$ ping 192.168.1.65
PING 192.168.1.65 (192.168.1.65) 56(84) bytes of data.
64 bytes from 192.168.1.65: icmp_req=1 ttl=64 time=[COLOR="Blue"]**1830 ms**[/COLOR]
64 bytes from 192.168.1.65: icmp_req=2 ttl=64 time=[COLOR="DarkRed"]**824 ms**[/COLOR]
64 bytes from 192.168.1.65: icmp_req=3 ttl=64 time=36.7 ms
64 bytes from 192.168.1.65: icmp_req=4 ttl=64 time=56.4 ms
64 bytes from 192.168.1.65: icmp_req=5 ttl=64 time=56.7 ms
64 bytes from 192.168.1.65: icmp_req=6 ttl=64 time=56.5 ms
64 bytes from 192.168.1.65: icmp_req=7 ttl=64 time=23.9 ms
64 bytes from 192.168.1.65: icmp_req=8 ttl=64 time=8.13 ms
64 bytes from 192.168.1.65: icmp_req=9 ttl=64 time=62.2 ms
64 bytes from 192.168.1.65: icmp_req=10 ttl=64 time=66.0 ms
64 bytes from 192.168.1.65: icmp_req=11 ttl=64 time=66.2 ms
64 bytes from 192.168.1.65: icmp_req=12 ttl=64 time=67.1 ms
64 bytes from 192.168.1.65: icmp_req=14 ttl=64 time=203 ms
64 bytes from 192.168.1.65: icmp_req=15 ttl=64 time=70.9 ms
64 bytes from 192.168.1.65: icmp_req=16 ttl=64 time=26.8 ms
64 bytes from 192.168.1.65: icmp_req=17 ttl=64 time=48.9 ms
64 bytes from 192.168.1.65: icmp_req=19 ttl=64 time=69.9 ms
64 bytes from 192.168.1.65: icmp_req=20 ttl=64 time=70.9 ms
64 bytes from 192.168.1.65: icmp_req=21 ttl=64 time=30.5 ms

``` other the same exept for 192.168.1.64 ip

Looking at this a little more carefully, I see that the return times are slow for a host that is on the same subnet.  Here is my ping of host that is in the same subnet on my LAN.  Not the times are considerably faster. ```
 ping rincon
PING rincon (192.168.1.2) 56(84) bytes of data.
64 bytes from rincon (192.168.1.2): icmp_seq=1 ttl=64 time=[COLOR="RoyalBlue"]**2.31 ms**[/COLOR]
64 bytes from rincon (192.168.1.2): icmp_seq=2 ttl=64 time=[COLOR="Red"]0**.**086 [/COLOR]ms
64 bytes from rincon (192.168.1.2): icmp_seq=3 ttl=64 time=0.085 ms
64 bytes from rincon (192.168.1.2): icmp_seq=4 ttl=64 time=0.089 ms

```

The initial ping is really slow (in blue)

---

### Post by n.hinton on 2012-06-11
```
kingfisher@GX620:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
BThomehub.home           ether   00:24:17:16:1a:8e   C                     wlan0
kingfisher-desktop.home  ether   00:22:b0:6f:6b:cb   C                     wlan0
kingfisher@GX620:~$
```

and

```
kingfisher@kingfisher-desktop:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
GX620.home               ether   00:1f:1f:ac:58:d6   C                     wlan0
BThomehub.home           ether   00:24:17:16:1a:8e   C                     wlan0
kingfisher@kingfisher-desktop:~$
```

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> ```
kingfisher@GX620:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
BThomehub.home           ether   00:24:17:16:1a:8e   C                     wlan0
kingfisher-desktop.home  ether   00:22:b0:6f:6b:cb   C                     wlan0
kingfisher@GX620:~$
```

and

```
kingfisher@kingfisher-desktop:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
GX620.home               ether   00:1f:1f:ac:58:d6   C                     wlan0
BThomehub.home           ether   00:24:17:16:1a:8e   C                     wlan0
kingfisher@kingfisher-desktop:~$
```

This is kinda like pullin' teeth with no anaesthetic; slow and painful.

I assume that the BThomehub is 192.168.1.253 and this is the only device you are using to connect the two computers together.  Is this correct?  Do you have a way to connect these with Ethernet cable instead of wireless?

---

### Post by n.hinton on 2012-06-11
Tell me about it lol, yes you are correct, no cant connect via ethernet

---

### Post by bab1 on 2012-06-11
> **n.hinton said:**
> Tell me about it lol, no cant connect via ethernet
At this point I'm not sure what to do.  I can't see any reason for the lack of broadcasts on the segment (subnet) for samba.  The only thing I can think of could be in the configuration of Samba that I have overlooked.

If you feel up to it, tomorrow we can install Wireshark and sniff the broadcast traffic on the network.

---

### Post by n.hinton on 2012-06-11
Thanks, 
i'm up for that

---


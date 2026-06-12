---
title: "Network printing problems!!"
date: 2010-11-07
forum: General Help
---

### Post by steve509 on 2010-11-07
I'm running Mint 9 as my main network and my wifes Acer Aspire 5610 running Windows vista. My problem is that I can't print from vista. It prints a test page just fine but when I tell it to actually print a document, the status says: "Access denied, unable to connect" The printer is a HP LaserJet 2100 series and an HP Photosmart C5280
Any help would be greatly appreciated
Thanks
steve509

---

### Post by Mark Phelps on 2010-11-07
Are you using hplip?

I don't use that but instead, have network printing enabled using the CUPS Gutenprint drivers.

They've been improving those considerably to the degree that with 10.04 and 10.10, I was able to find my networked HP printers quite easily from the installation in CUPS.  To see that, open a browser and enter "localhost:631".  That will get you into the main screen for CUPS.

---

### Post by steve509 on 2010-11-09
Mark, first let me thank you for your reply.  I've tried both hplip and CUPS and still nothing. What i don't understand is that from my wifes laptop I can go into Printers, right click and click Print Test page and that works just fine. I don't know whats wrong but I would think!! that if it sees the printers well enough to print test pages then why not a document?????? I know i'm a newbie and I think i'm way over my head on this one. Any other ideas to try would be great.

Again, thanks for your help
steve509

---

### Post by todak on 2010-11-09
Do you have the printer marked as shared? In your printing properties window, right-click on the printer and make sure there is a check next to  *Shared* and *Enabled*, then click the *Server* menu and click *Settings* and make sure *Publish shared printers connected to this system* is checked. See the attached screenshot.

---

### Post by steve509 on 2010-11-09
Todak, thanks for helping. To answer your questions, yes, they are both shared and enabled and in the Settings, both printers are checked to Publish shared printers...Any other thoughts??
Again, thanks
steve509

---

### Post by efflandt on 2010-11-10
It is not clear where the printers are (on the network or on your Mint9 box) and how Vista is connected.  If using Win file/printer sharing and samba do you have the samba "server" installed and both computers set to the same workgroup?

An alternative is configuring "Internet" printing in Windows to print to your cups port.  But Windows does not seem to know what ipp port is, so if you configure "Internet" printing from Windows to your PC you have to set up the URI with the ipp port as **[http://ip_address:631/printer_name](http://ip_address:631/printer_name)** in Windows.

---

### Post by steve509 on 2010-11-10
efflandt, I will give that a try. To answer the first part of your question, the printers are connected to the Linux box and I installed the printers on the laptop as internet printers. At first the vista laptop saw the printers on the Linux box, but now (I  deleted them from Vista to try to reinstall) but now Windows wont even see the linux box

---

### Post by Morbius1 on 2010-11-11
Just some random thoughts.

By far the best way is the "internet printing" method that efflandt suggested:
> [http://ip_address:631/printer_name](http://ip_address:631/printer_name)It bypasses Samba and that is always a good thing.

It appears though that you are using the Vista Wizard to to browse to the printer and so Samba is being used. The original error you had was:
```
"Access denied, unable to connect" 
```Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```And modify the following section from this:
> [printers] 
    comment = All Printers 
    browseable = no 
    path = /var/spool/samba 
    printable = yes 
;    guest ok = no 
;    read only = yes 
    create mask = 0700 To this:
> [printers] 
    comment = All Printers 
    browseable = no 
    path = /var/spool/samba 
    printable = yes 
    **[COLOR=Blue]guest ok = yes[/COLOR]**
;    read only = yes 
    create mask = 0700 [COLOR=Blue]*Don't forget to remove the leading ";" in front of "guest ok = yes"*[/COLOR]
Save the file and restart services in this exact order:
```
sudo service cups restart
``````
sudo service smbd restart
``````
sudo service nmbd restart
```
See if that gets you any further.

---

### Post by steve509 on 2010-11-12
Morbius1, Thanks for trying to help. Now both my Linux box and my wifes Vista laptop won't communicate with each other. All file sharing and everything else i can think of is turned on but I can't see the vista box from Linus and vice-versa. I just don't know what to do any more. Am I fighting a losing battle here and just go back to Windows? Oh how i hate that thought!! Please, anyone? HELP!!!!
All help is greatly appreciated.

Thanks to all
steve509

PS, please keep in mind that I am still a newbie at this. I'm usually pretty good at figuring things out eventually but this has me stumped and my wife pissed :)

PPS, I tried what you suggested but without both computers communicating with eachother...well, you know the rest......

---

### Post by Morbius1 on 2010-11-13
There are two diagnostics commands that might let people here know what's up:
```
testparm -s
``````
smbtree
```Post the output so folks here can view the results.

---

### Post by steve509 on 2010-11-13
Morbius1, here is the output to: testparm -s

steve@steve-desktop ~ $ testparm s
Load smb config files from s
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:OpenConfFile() - Unable to open configuration file "s":
	No such file or directory
Error loading services.

and smbtree:

steve@steve-desktop ~ $ smbtree
Enter steve's password: 
Server requested plaintext password but 'client plaintext auth' is disabled
anonymous failed session setup with NT_STATUS_INVALID_PARAMETER
Server requested plaintext password but 'client plaintext auth' is disabled
anonymous failed session setup with NT_STATUS_INVALID_PARAMETER

Thanks for trying
steve509

---

### Post by Morbius1 on 2010-11-13
It's:
```
testparm -s
```

---

### Post by steve509 on 2010-11-13
Sorry about that, i thought I put the - in..here are the results


steve@steve-desktop ~ $ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[home]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, LinuxMint)
	encrypt passwords = No
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[home]
	path = /home
	read only = No
	guest ok = Yes

---

### Post by Morbius1 on 2010-11-13
Edit your smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
And change this line:
> encrypt passwords = No
To Yes:
> encrypt passwords = Yes
Save smb.conf and restart samba:
```
sudo service smbd restart
```

---

### Post by steve509 on 2010-11-13
Norbius1, I brought up the smb.conf in gedit to change the encrypt from no to yes but I do not see that line anywhere. Here is the file: 
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
	server string = %h server (Samba, LinuxMint)

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
	encrypt passwords = no

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
	security = user
	guest ok = yes
	guest account = avahi
	username map = /etc/samba/smbusers

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
;   share modes = yes

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
	guest ok = yes
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers

[home]
	path = /home
	writeable = yes
;	browseable = yes
	guest ok = yes

---

### Post by steve509 on 2010-11-13
Maybe i should change my glasses, I just found the line...sorry about that. I'll make the change and let you know how it went..thanks so much

---

### Post by steve509 on 2010-11-13
Morbius1!!!! Thank you sooooo much, it finally worked...YAAH!!!

THANK YOU!!
steve509

---


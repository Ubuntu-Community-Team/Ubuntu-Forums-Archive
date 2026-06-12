---
title: "can't print from Windows to Ubuntu 12.04"
date: 2012-05-03
forum: General Help
---

### Post by bottleman on 2012-05-03
Hi, 

I know there are lots of Samba related guides out there, but I've been through several and am still mystified.  Perhaps things are different now with 12.04?

I recently upgraded my home PC (mostly used for file storage and as a print server) from Windows XP to Ubuntu 12.04.  I want to do two things: 
1) store shared files on this Ubuntu 12.04 machine and access them from Windows and Linux laptops.
2) print from Windows and Linux laptops to the printer connected to the Ubuntu 12.04 machine.

This is not a situation that requires high security and I would prefer there to be no passwords required.

The file sharing is working fine, but I mention it because I presume both file and printer sharing use Samba.  I set the file shares up via the right-click "Sharing" menu in Nautilus.  I didn't see any folders defined in the smb.conf file after I did this, oddly.  (???)

The shared printing is not working from Windows.  Printing works fine directly from the Ubuntu 12.04 machine, and Linux laptops connected to the home network automatically detect the printer and can print fine also.  Windows laptops can see the printer but cannot get the driver from Samba or (after a driver is provided) connect to the printer.

Here's what happens if I follow [this tutorial]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu_print_server_compatible_with_Windows_.28Samba.29"). 

Here are my printer settings:
[IMG]http://farm8.staticflickr.com/7044/7137712907_d4800d4274_n_d.jpg[/IMG]

And my smb.conf:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = poa

# server string is the equivalent of the NT Description field
	server string = %h server (Ubuntu)

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
	security = share
;	guest account = nobody

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

;	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
;	passwd program = /usr/bin/passwd %u
;	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
;	map to guest = bad user

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
	printing = cups
   printcap name = cups

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
	guest ok = yes

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
	browseable = yes
	path = /var/spool/samba
	printable = yes
	guest ok = yes
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = yes
;	read only = yes
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

```

Now when in Windows I start the New Printer Wizard, I can choose Network Printer and browse until I see my printer:
[IMG]http://farm9.staticflickr.com/8007/6991631528_8a1b7b33aa_n_d.jpg[/IMG]

Then Windows tries to connect and get a driver.
It returns an error message that the wrong driver is installed on the server.  I load a driver for my printer using the "Have Disk..." option.  Then Windows tries to connect and fails.  It suggests that the printer name was typed incorrectly, or the printer lost its connection to the server.

I get the same pattern of errors on both Windows XP and Windows 7 laptops.

One more clue: when I go to the CUPS interface on my web browser on the 12.04 machine, I can see the printer there but when I ask to "administer" it, CUPS replies "forbidden."

I'm really kind of in above my head here, as I'm mostly just a user and not a network administrator.  Still I really would like this printing thing to work.

Any advice would be welcome. Cheers!

---

### Post by pezball on 2012-05-03
Hi, got same problem here...
 
Done a fresh install of Ubuntu 12.04 on my server, set it up exactly the same way as I did with older 10.04.
 
Windows can find the printers, but I notice something strange... When you click to choose the printer in the Windows XP Add Printer Wizard, the printer name flashes by in the Printer textbox, but is immediately replaced by only the server name. And then when you click on Next, it attempts to connect to the server name, not the printer name. Which would explain why it is impossible to make it work. I have no idea if it behaved same way in 10.04, but at least the printer would be installed then without any problems.
 
Is this a Samba or CUPS problem?

---

### Post by ArikZinger on 2012-05-05
I as well have a printing problem from Windows to Ubuntu 12.04

In previous  versions of Ubuntu I used to install Samba and then configure the workgroup to my workgroup, changing the Authentication mode to "Share" and the Guest Account to "nobody".

That was enough to enable me to print from my Windows machines.
For some reason this no longer works for me.

When I try to install a printer from Windows, while trying to create the local port \\compname\sharename , I get the "Access Denied" message.

It is defiantly some kind of a change in security issue, since when I try to "net view \\compname" I can see the shares on the Ubuntu machine.

Does anyone know how to fix this problem?

---

### Post by bottleman on 2012-05-05
Hi Arik and Pez, glad to know that someone else shares my pain. :)

I'm going to try experimenting with the CUPS setup and see if that changes anything.  But I don't know what I'm doing so hopefully some person with more perspective will pipe in here soon.  Cheers!

---

### Post by HermanAB on 2012-05-05
Printing is done by CUPS.  Samba is for file sharing.

[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

Basically, you just send a file to the Linux machine using IPP and it will print it for you on the default printer.

---

### Post by pezball on 2012-05-05
> **HermanAB said:**
> Printing is done by CUPS.  Samba is for file sharing.

[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

Basically, you just send a file to the Linux machine using IPP and it will print it for you on the default printer.
Yes printing is done by CUPS, but Samba handles the sharing of printers too, in same way as a Windows server would, which is more familiar to most Windows users, and it has worked perfectly in Ubuntu 10.04.  So your reply does not help much, especially the link you sent, which is all about Linux printing inside Linux.

---

### Post by Morbius1 on 2012-05-05
@bottleman,

**First**, You are missing one step in the Printers utility: **Server**.  This brings up the attached dialog. You must allow the shared printer to be "Published". Yours will look slightly different since I'm using Xubuntu.

**Second**, You need to modify a samba config file to allow clients to access the printer without requiring credentials:
[COLOR=Blue]**EDIT**: A thousand apologies. Didn't even bother to go though your smb.conf. It looks like you already did this step.[/COLOR]

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Find this section:
> [printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
    [COLOR=Blue]**guest ok = no**[/COLOR]
;    read only = yes
    create mask = 0700And change it to this to allow guest access:
> [printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
    [COLOR=Blue]**guest ok = yes**[/COLOR]
;    read only = yes
    create mask = 0700
After you change smb.conf you need to restart the following services in this exact order since Samba reads the data that cups provides so cups needs to start first:
```
sudo service cups restart
sudo service smbd restart
```**Third**,
 > I set the file shares up via the right-click "Sharing" menu in  Nautilus.  I didn't see any folders defined in the smb.conf file after I  did this, oddly.  (???)Samba allows 2 different methods to create shares. THe "Classic" way is through smb.conf. The way you created them is called "Usershares" in samba. The share definitions are in /var/lib/samba/usershares. The way you normally review these definitions is by issuing the following command:
```
net usershare info --long
```[COLOR=Blue]**EDIT**[/COLOR]: By the way. Why did you feel the need to deviate so far from the default smb.conf.

---

### Post by bottleman on 2012-05-06
Hi Morbius, thanks for the response.

You wondered..

> **Morbius1 said:**
> By the way. Why did you feel the need to deviate so far from the default smb.conf.

Um, basically I was working from a whole bunch of various Samba help files which may have been from 1-10 years old.  I just started changing stuff...  :)

Anyway I reverted to a simpler smb.conf, and double checked the server settings, but am getting exactly the same behavior.  Here are the settings...

[IMG]http://farm9.staticflickr.com/8166/7001477644_362d305dea_d.jpg[/IMG]

and here is the smb.conf...
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
	workgroup = poa

# server string is the equivalent of the NT Description field
	server string = %h server (Ubuntu)

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
	security = share
	guest ok = yes
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
	browseable = yes
	path = /var/spool/samba
	printable = yes
	guest ok = yes
;	read only = yes
	create mask = 0700





# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = yes
;	read only = yes
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

```

FWIW, I did look at the CUPS error log while I was trying to set up the windows laptop (IP address 192.x.x.102) to print to the Ubuntu machine (192.x.x.106).  At this point I was just inserting the IPP address of the printer, which is a trick that has worked before for me in other offices.   I have no idea what the following means, but it does seem to indicate that the windows laptop was trying to do something. 

```
D [06/May/2012:00:47:23 -0700] cupsdAcceptClient: 18 from localhost (Domain)
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [06/May/2012:00:47:23 -0700] cupsdAuthorize: No authentication data provided.
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [06/May/2012:00:47:23 -0700] CUPS-Get-Printers
D [06/May/2012:00:47:23 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [06/May/2012:00:47:23 -0700] cupsdAuthorize: No authentication data provided.
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [06/May/2012:00:47:23 -0700] CUPS-Get-Classes
D [06/May/2012:00:47:23 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 18 WAITING Closing on EOF
D [06/May/2012:00:47:23 -0700] cupsdCloseClient: 18
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
D [06/May/2012:00:47:23 -0700] cupsdAcceptClient: 18 from 192.168.0.102:631 (IPv4)
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 18 GET /admin HTTP/1.1
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [06/May/2012:00:47:23 -0700] cupsdAuthorize: No authentication data provided.
D [06/May/2012:00:47:23 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/admin.cgi"
D [06/May/2012:00:47:23 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [06/May/2012:00:47:23 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [06/May/2012:00:47:23 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/May/2012:00:47:23 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/May/2012:00:47:23 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [06/May/2012:00:47:23 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [06/May/2012:00:47:23 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [06/May/2012:00:47:23 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [06/May/2012:00:47:23 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [06/May/2012:00:47:23 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/May/2012:00:47:23 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@htpcacer"
D [06/May/2012:00:47:23 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.5.2"
D [06/May/2012:00:47:23 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [06/May/2012:00:47:23 -0700] [CGI] envp[13] = "USER=root"
D [06/May/2012:00:47:23 -0700] [CGI] envp[14] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [06/May/2012:00:47:23 -0700] [CGI] envp[15] = "CUPS_ENCRYPTION=IfRequested"
D [06/May/2012:00:47:23 -0700] [CGI] envp[16] = "IPP_PORT=631"
D [06/May/2012:00:47:23 -0700] [CGI] envp[17] = "LANG=en_US.UTF8"
D [06/May/2012:00:47:23 -0700] [CGI] envp[18] = "REDIRECT_STATUS=1"
D [06/May/2012:00:47:23 -0700] [CGI] envp[19] = "GATEWAY_INTERFACE=CGI/1.1"
D [06/May/2012:00:47:23 -0700] [CGI] envp[20] = "SERVER_NAME=192.168.0.106"
D [06/May/2012:00:47:23 -0700] [CGI] envp[21] = "SERVER_PORT=631"
D [06/May/2012:00:47:23 -0700] [CGI] envp[22] = "REMOTE_ADDR=192.168.0.102"
D [06/May/2012:00:47:23 -0700] [CGI] envp[23] = "REMOTE_HOST=192.168.0.102"
D [06/May/2012:00:47:23 -0700] [CGI] envp[24] = "SCRIPT_NAME=/admin"
D [06/May/2012:00:47:23 -0700] [CGI] envp[25] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/admin"
D [06/May/2012:00:47:23 -0700] [CGI] envp[26] = "SERVER_PROTOCOL=HTTP/1.1"
D [06/May/2012:00:47:23 -0700] [CGI] envp[27] = "HTTP_COOKIE=org.cups.sid=47a28f95529b4d376091781a423015ba"
D [06/May/2012:00:47:23 -0700] [CGI] envp[28] = "HTTP_USER_AGENT=Mozilla/5.0 (Windows NT 5.1; rv:11.0) Gecko/20100101 Firefox/11.0"
D [06/May/2012:00:47:23 -0700] [CGI] envp[29] = "HTTP_REFERER=http://192.168.0.106:631/"
D [06/May/2012:00:47:23 -0700] [CGI] envp[30] = "REQUEST_METHOD=GET"
D [06/May/2012:00:47:23 -0700] [CGI] envp[31] = "QUERY_STRING="
D [06/May/2012:00:47:23 -0700] [CGI] Started /usr/lib/cups/cgi-bin/admin.cgi (PID 2686)
I [06/May/2012:00:47:23 -0700] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=2686)
D [06/May/2012:00:47:23 -0700] cupsdSendCommand: 18 file=20
D [06/May/2012:00:47:23 -0700] [CGI] admin.cgi started...
D [06/May/2012:00:47:23 -0700] cupsdAcceptClient: 21 from localhost (Domain)
D [06/May/2012:00:47:23 -0700] [CGI] http=0xb96bfea8
D [06/May/2012:00:47:23 -0700] [CGI] org.cups.sid cookie is "47a28f95529b4d376091781a423015ba"
D [06/May/2012:00:47:23 -0700] [CGI] No form data, showing main menu...
D [06/May/2012:00:47:23 -0700] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 21 POST / HTTP/1.1
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Active clients"
D [06/May/2012:00:47:23 -0700] cupsdAuthorize: No authentication data provided.
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 21 1.1 Get-Subscriptions 1
D [06/May/2012:00:47:23 -0700] Get-Subscriptions ipp://localhost/
D [06/May/2012:00:47:23 -0700] Returning IPP successful-ok for Get-Subscriptions (ipp://localhost/) from localhost
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Active clients"
D [06/May/2012:00:47:23 -0700] Script header: Content-Type: text/html;charset=utf-8
D [06/May/2012:00:47:23 -0700] Script header: 
D [06/May/2012:00:47:23 -0700] cupsdReadClient: 21 WAITING Closing on EOF
D [06/May/2012:00:47:23 -0700] cupsdCloseClient: 21
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Active clients"
D [06/May/2012:00:47:23 -0700] PID 2686 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [06/May/2012:00:47:23 -0700] cupsdSetBusyState: newbusy="Not busy", busy="Active clients"
D [06/May/2012:00:47:25 -0700] cupsdReadClient: 18 GET /admin/log/error_log HTTP/1.1
D [06/May/2012:00:47:25 -0700] cupsdSetBusyState: newbusy="Active clients", busy="Not busy"
D [06/May/2012:00:47:25 -0700] cupsdAuthorize: No authentication data provided.
```

Is there an error here or is this just normal processing? This feels like an error... it is looking for some kind of driver.

```
D [06/May/2012:00:47:23 -0700] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
```

I don't think that directory even exists.

Anyway, does this help?  I need to fix this or the Windows laptop people around my office will make me convert this pc back to windows so they can print!

Cheers!

---

### Post by Morbius1 on 2012-05-06
There is a command that you need to use that will help you in all future dealings with Samba: **testparm**. It's the samba interpreter and it can help you diagnose problems with how samba is set up. If you run the following command it will will tell you how samba interprets what you have done with your smb.conf file:
```
testparm -s
```When you do that you will see 2 interesting things in the output:
> WARNING: The security=share option is deprecatedNo one still living really knows how share level security works ( that may be a slight exaggeration :wink: ). The default is user so I would change it back:
```
security = user
```[COLOR=Blue]*Note: There are a couple of very obscure bugs in samba and to work around these bugs you have to set it to SHARE but it's very rare.*[/COLOR]

The second thing you will notice is this:
> encrypt passwords = NoThe default is yes. Not sure how or why it flipped on you but you need to set it back to the default:
```
encrypt passwords = yes
```You may have created only guest shares and think that no passwords are required but remember that a Windows client passes a user name and password automatically without being asked requiring the Samba server to deal with it somehow.

Something else that should have been set up by default is in the Printing utility for that printer. Under Access Control it should have set the following as the default: **Allow printing to everyone except these users.**

After making these changes restart the services again: first cups then samba:
```
sudo service cups restart
sudo service smbd restart
```

---

### Post by HermanAB on 2012-05-06
Wow, so ridiculously complicated.

Just open the Windows print utility and select network printer, then enter ipp://ipaddressoflinuxmachine

---

### Post by pezball on 2012-05-06
I have been looking for solutions, and then I found this... [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)
 
So the Ubuntu developers are aware of this problem already, at least for Windows XP users.

---

### Post by bottleman on 2012-05-06
Thanks for the work, Morbius and Pezball. Morbius, I'll try going through those things later when I am at that machine.  FWIW, I think I changed the authentication mode from USER to SHARE because it kept challenging me for passwords.

However, the bug that Pezball linked to is exactly the same one I am experiencing, so it could be it's not my smb.conf at all.  I don't know Jack about programming, but it still seems odd that CUPS is looking for a *.dll in a directory that doesn't exist.  Is that what happens just before the Windows client reports that the correct driver is not available from on the server?

Herman, thanks for your attention to this thread.  I had already tried entering the IPP address directly, as I noted in my last message...

> At this point I was just inserting the IPP address of the printer...

... and received the same results as in my OP.  Cheers!

---

### Post by Morbius1 on 2012-05-06
The bug report shows a new dimension to this problem. It's not entirely clear to me that it's a samba issue but ....

> FWIW, I think I  changed the authentication mode from USER to SHARE because it kept  challenging me for passwords.At the moment it's somewhat academic but originally your smb.conf was missing a line in the global section. 

"security = share" in a modern Samba server is effectively handled by 2 lines:
```
security = user
map to guest = Bad User
```You didn't have the "map to guest" in your original smb.conf so if you set security to user and don't specify Bad User samba defaults to "map to guest = Never" which as you can imagine is not what you wanted.

---

### Post by pezball on 2012-05-06
Yes, it is likely a deeper problem, cos I have exactly the same problem as the original bug reporter.
 
Using an identical smb.conf as the previous Ubuntu 10.04 installation, but erratic behaviour.  From a Win 7 client everything works perfectly here with my server, so my problem is limited to Win XP clients.  Then the question is how Win XP and Win 7 differ in their smb printing protocol.  Apparently something differs.  And some clever bug fix has broken compatibility with the older XP protocol for printers.
 
As the bug reporter used Ubuntu 11.10 before, it's clear that this bug first appears with Ubuntu 12.04.

---

### Post by Morbius1 on 2012-05-06
@pezball

The path lead me to understand that the version of samba in 12.04 is in the 3.6 series ( this is Samba's version level not what Ubuntu reports ) vs the 3.5 series in earlier Ubuntu's.

And in looking at the "features": [http://wiki.samba.org/index.php/Samba_3.6_Features_added/changed#Changed_security_defaults](http://wiki.samba.org/index.php/Samba_3.6_Features_added/changed#Changed_security_defaults)
> New Spoolss code The spoolss and the old RAP printing code have been completely overhauled and refactored. 
All calls from lanman/printing code has been changed to go  through the spoolss RPC interfaces, this allows us to keep all checks in  one place and avoid special cases in the main printing code. Printing  code has been therefore confined within the spoolss code. 
Total rewrites often lead to things like this because testing is a lost art.

Just curious though I have a WinXP box and could connect to a Xubuntu 12.04 printer this way using the "Add printer" mechanism in XP ( Connect to a printer on the Internet ... ):

URL:
```
http://192.168.0.100:631/printers/HPPrinter
```Does that not work for you?

The CUPS "Printer" Utility would have to have the server set to "Allow printing from the Internet".

---

### Post by pezball on 2012-05-07
@Morbius1
 
 
Aha, that rewrite sounds like a possible problem trigger.
 
Complete rewrites are usually not recommended, but I guess they did have a good reason for not patching the already patched until it falls apart in unreadable code. So I guess that the non-existing testing will give all sorts of side-effects. Just have to wait and see what happens when Samba is updated next time. New Ubuntu releases are usually followed by bunches of updates, so that's nothing new.
 
 
Yes, I can add the printer via ipp, but the CUPS error log shows the following at the time of adding:
 
```

E [07/May/2012:12:15:37 +0200] Missing printer-uri, job-uri, or ppd-name attribute
E [07/May/2012:12:15:37 +0200] Returning IPP client-error-bad-request for windows-ext (no URI) from 10.0.0.2

```
 
When trying to print a test page the CUPS eror log shows:
 
```

E [07/May/2012:12:16:01 +0200] Returning IPP client-error-not-authorized for Print-Job (http://server:631/printers/Brother_HL-2030_series) from 10.0.0.2

```
 
I have never connected by IPP before so I have no clue about if CUPS needs some special configuration to allow it.
 
 
**EDIT:** Ok I forgot to restart CUPS after allowing internet connections, that solves the adding error, but the authorization error remains when attempting to print.

---

### Post by Morbius1 on 2012-05-07
This whole thing is getting curiouser and curiouser with every experiment I run.

Win2K ( I have a lot of useless equipment in this shop :) ) has no issues whatsoever and connects to the printer via samba just as it always did.

WinXP has to use http

Another Linux box ( when using samba ) is actually more transparent but also doesn't work - I'm in an infinite loop of it asking for credentials even though I have not specified that it needs any in either CUPS ( Printing > Printer ) or in smb.conf.

Also of note is then when I issue the following command in Xubuntu 12.04:
```
lpstat -t
```I get an error message that I've never seen before:
> WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-2vVdwk/pkcs11: No such file or directoryThat is in fact correct - there is no such file or path to that location.

There seems to be multiple issues here.
[COLOR=Blue]**EDIT**[/COLOR]: Sorry, the keyring problem was an XFCE issue - I fixed it. Wasn’t reading my own notes on how to set up XFCE.

---

### Post by bottleman on 2012-05-07
Morbius, you rock! I have Windows XP and Windows 7 laptops printing now through the Ubuntu 12.04 box.

FYI I already had the "allow printing from internet" option turned on, but previously that had no effect.  I also have made no changes to the smb.conf since the last time I posted it.

On the XP client machine, I did the "add printer from the internet" wizard, and put in the printer's full address using http:// as the prefix instead of the usual ipp:// ... e.g. ```
http://192.x.x.106:631/printers/PrinterName
```

On the Windows 7 client machine, the http:// trick failed.  I had to go through some sort of iterative process where I tried to add the printer via the wizards, which failed, and then I manually changed the port to the form of 
```
\\ServerName\PrinterName
```

(To tell you the truth I'm not precisely sure what order I the changes on the Windows 7 machine, but since it's my spouse's/partner's machine, and she really needs to print, I'm just going to let it be and not jinx it.)

Thanks to you and pezball for zeroing in on a fix. :popcorn:

ps. apologies if this message appears twice.. forum site acting weird.

---

### Post by Rigved on 2012-05-24
> **bottleman said:**
> FYI I already had the "allow printing from internet" option turned on, but previously that had no effect.  I also have made no changes to the smb.conf since the last time I posted it.

On the XP client machine, I did the "add printer from the internet" wizard, and put in the printer's full address using http:// as the prefix instead of the usual ipp:// ... e.g. ```
http://192.x.x.106:631/printers/PrinterName
```

This http method worked for me too. Now, Windows XP machines connected to the network can print properly.

As for the Windows 7 machines, I installed the drivers from the CD which came with the printers. Then, I used the procedure to "Add a network printer". This worked.

Thanks everyone for your help!

---

### Post by bottleman on 2012-05-24
Rigved, are you experiencing any problems printing PDFs from Windows 7 through the Ubuntu server, as described in [this thread]("http://ubuntuforums.org/showthread.php?t=1978230")?  I still haven't been able to fix that aspect of my setup.

---

### Post by manni122 on 2012-06-02
Dear all,
I had the same problem as u've described in your posts.
One potential fix maybe the following trick:
Look at the owner of /var/spool/cups/tmp folder
It should be root:lp
If this is the case then simply add yourself and the ones that should be able to print to this group (lp).
Restart the samba server as root /etc/init.d/smbd restart
Now everything should be fine.
Give it a shot!

Cheers, Markus

---

### Post by robbielink on 2012-06-25
#21 did not work for me. Bunch of folks having the same issue over at launchpad - bug reported.
Put in a word over there to get it escalated:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

---


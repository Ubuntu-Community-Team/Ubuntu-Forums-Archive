---
title: "Samba problem: cannot share a folder in Lucid"
date: 2010-05-11
forum: General Help
---

### Post by raffaele181188 on 2010-05-11
I'm on Lucid. I can see my Windows machine and can read/write to it.
But Windows cannot see Ubuntu (neither I can, I mean if I go to System > Places > Network I only see my Win machine, but I remember that also your samba-enhanced machine is listed)

What's wrong? I set up two share points: one with the system-wide system-config-samba (run with admin privileges and which adds an entry to smb.conf) and another one with Nautilus (right click > share)
I'm in a closed network, so there are no security concerns, I want to share some directories without authentication

Also, if I set "security = share" I cannot even see my win machine!!!

Here you are my smb.conf
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
	valid users = raffaele
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

[Test Exchange]
	comment = Please, delete me as soon as possible
	path = /data/downloads
	writeable = yes
;	browseable = yes
	guest ok = yes


```

---

### Post by Morbius1 on 2010-05-11
> What's wrong? I set up two share points: one with the system-wide system-config-samba (run with admin privileges and which adds an entry to smb.conf) and another one with Nautilus (right click > share)Since you're also using Nautilus-share can we see the output of the following commands to see if there is a conflict with what you have in smb.conf:

**net usershare info**
**sudo net usershare info**

It's best not to use Classic-share and Nautilus-share at the same time and on the same target directory.

[COLOR=Blue]EDIT: What are the permissions on /data/downloads:[/COLOR]

**ls -dl /data/downloads**

---

### Post by raffaele181188 on 2010-05-11
```
raffaele@Aldebaran:~$ net usershare info
[javalibs]
path=/home/raffaele/Storage/javalibs
comment=
usershare_acl=Everyone:F,
guest_ok=y

[music]
path=/home/raffaele/Desktop/Music
comment=Music files
usershare_acl=Everyone:F,
guest_ok=y

[exchange folder]
path=/home/raffaele/Desktop/Downloads
comment=Exchange folder
usershare_acl=Everyone:F,
guest_ok=y

```
You see, I tried other folders too


**sudo net usershare info**
(nothing)

> 
It's best not to use Classic-share and Nautilus-share at the same time and on the same target directory.

What does this mean?

```
raffaele@Aldebaran:~$ ls -ld /data/downloads/
drwxrwxrwx 10 raffaele users 4096 2010-05-11 10:44 /data/downloads/
```

---

### Post by Morbius1 on 2010-05-11
This is a Classic-share ( shares defined in smb.conf ):
> [Test Exchange]
    comment = Please, delete me as soon as possible
    path = /data/downloads
    writeable = yes
;    browseable = yes
    guest ok = yesThis is a Nautilus-share ( shares defined in /var/lib/samba/usershares ):
> [music]
path=/home/raffaele/Desktop/Music
comment=Music files
usershare_acl=Everyone:F,
guest_ok=y
Strange things happen when you use both on the same path. This is not the case with you. In fact I can't find anything wrong with the way you've set things up.

Let's see if we can generate some error messages.

From the Ubuntu box post the output of: **smbtree**

From the Windows box from "Command Prompt" post the output of: **net view**


smbtree and net view are similar utilities that should show you the shares available from each OS's perspective. It should give you error messages if somethings's not right.
And have you done anything to the firewall on Ububntu? If you have disable it. If you haven't then leave it alone.

[COLOR=Blue]EDIT: Stupid question. Is samba running?[/COLOR]

**sudo service smbd status**
**sudo service nmbd status**

---

### Post by sinner99 on 2010-05-12
yo dude, this was my problem! erg! pulln my hair out! i copied your smb.conf cleaned it up a touch and then.....wait for it....
```

sudo aptitude  remove nautilus-share

```wo0t! \o/
net view from your win boxes and smbtree from your nix boxes. FINALLY!!

when i ran **sudo net usershare info **it woke me up to the fact apparently they woz still nautilus-shared(nothin nowhere was checked i swear!) but that command clearly showed em shared. only solution to me was obvious **sudo aptitude remove nautilus-share **n crossed my fingers it didnt want to take the rest of linux with it! My only beef with linux is its apparent pertinent need to take so many dependent programs with them, when you remove them, what a pain!

big thanks to Morbius1 ^5 fer the dual sharing thing, at one point after  the lucid final installation my shares had all been  nautilus-shared...although they were not for some time, and I couldn't  figure it out. 


all good nao! <3 Morbius1 i can sleep now. ...
...
edit: theres not much linux left without perl :< that was my first go at it ways back.

another edit: take the 'e's out of browsable, raffaele181188, every one of them. typo! :p

---

### Post by Morbius1 on 2010-05-12
sinner99, removing nautilus-share was rather drastic. All you needed to do was go into Nautilus and "unshare" them. Or you could have gone into /var/lib/samba/usershares as root and deleted them.

Or you could have gone into smb.conf and deleted the Classic-shares and run with only Nautilus-shares.

I would not recommend uninstalling nautilus-share.

>  another edit: take the 'e's out of browsable, raffaele181188, every one of them. typo! :razz:     "browseable" is not a typo 

from man smb.conf:
> 
**browsable**


This parameter is a synonym for [browseable]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BROWSEABLE").

**browseable** (S)

           This controls whether this share is seen in the list of available
           shares in a net view and in the browse list.

           Default: browseable = yes



---

### Post by raffaele181188 on 2010-05-12
**Now everithing's fine** :confused:

Samba is running
```
raffaele@Aldebaran:~$ sudo service smbd status
smbd start/running, process 905
raffaele@Aldebaran:~$ sudo service nmbd status
nmbd start/running, process 3430

```

And smbtree shows the correct output.

I think I resolved by restarting **nmbd**, because his previuos status was stop/waiting. What the hell is nmbd? :P

---

### Post by Morbius1 on 2010-05-12
> What the hell is nmbd?> **The nmbd daemon**

 The nmbd server daemon understands and replies to NetBIOS name service requests such as those produced by SMB/CIFS in Windows-based systems. These systems include Windows 95/98/ME, Windows NT, Windows 2000, Windows XP, and LanManager clients. It also participates in the browsing protocols that make up the Windows **Network Neighborhood** view. The default port         that the server listens to for NMB traffic is UDP port 137.         The service called "samba" was created that combined the smbd daemon and the nmbd daemon into one service. One could do a "sudo service samba restart" to restart both daemons. Because of Ubuntu's decision to use upstart to control how services are run the "samba" service was returned to the state it was years ago when smbd and nmbd were run separately. SOmewhere along the line nmbd was not started in your case. Not exactly sure why.

Short answer: You may have a perfectly legitimate share but if nmbd isn't running Windows doesn't even know you're there.

[COLOR=Blue]EDIT: It may be that in the effort to reduce boot times upstart is executing nmbd before the network is up. As I recall nmbd will fail is the network is not up. The true test will be when you reboot. If you have to start nmbd again then that might be the problem..[/COLOR]

---

### Post by sinner99 on 2010-05-13
hm weird thanks. didn't know there was two ways, my smb.conf came with it spelled as I was, assumed the other way was a type. thanks for the info. everything is fantastic with nautilus-share gone though! the shares were unshared in nautilus way back, and I double checked, absolutely nothing shared via nautilus, yet I run sudo net usershare info...i have nautilus shares according to the output. the only thing that made sense was to simply **sudo aptitude remove nautilus-share**. today I reinstalled it and everything is still fine, although my output is still the same, pointing to nautilus created shares when i run the net usershare info command.

---


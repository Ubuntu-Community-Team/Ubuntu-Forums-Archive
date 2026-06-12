---
title: "You do not have the permissions necessary to view the contents of"
date: 2010-05-26
forum: General Help
---

### Post by fipem on 2010-05-26
Hi there, I have a problem that many seems to have... I'm trying to access some files via samba from XP to Ubuntu and the "You do not have the permissions necessary to view the contents of - FOLDER" error appears. I have Ubuntu Lucid installed on a hard drive, half Ubuntu and half Windows XP and other Hard Disc Drives that serve as a -downloaded files- disc, over Ubuntu I can have access over the three partitions (two hard disk) but, when I try to access them via SAMBA on XP I'm only able to access one of the three partitions, the one where Ubuntu is installed on, even tho I actually see the three, but when I try to access the other two the error appears.

I try to share the media folder to resolve this but the same happens...

The same happens when I try to access from Ubuntu to the shared folder in XP.

I think it maybe have something to do with CIF's, but my knowledge is limited in the issue, here is my smb.conf file

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
	workgroup = ubuntu

# server string is the equivalent of the NT Description field
	server string = Samba

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
;	guest ok = no
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

[Win]
	path = /media/9C680A226809FBB0
	writeable = yes
;	browseable = yes
	guest ok = yes
	comment = Win

[Downloads]
	comment = Descargas
	path = /media/Downloads
	writeable = yes
;	browseable = yes
	guest ok = yes

[fipem]
	comment = Ubuntu
	path = /home/fipem
	writeable = yes
;	browseable = yes
	guest ok = yes

[media]
	path = /media
	writeable = yes
;	browseable = yes
	guest ok = yes

---

### Post by bodhi.zazen on 2010-05-26
You understand samba is a network protocol meaning it is used to share files across a network and not across partitions ?

If you are running Windows and wish to access files on your Ubuntu partition either make a shared (NTFS) data partition or use fsdriver ro ext2read

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://ext2read.sf.net/](http://ext2read.sf.net/)

---

### Post by fipem on 2010-05-27
> **bodhi.zazen said:**
> You understand samba is a network protocol meaning it is used to share files across a network and not across partitions ?

If you are running Windows and wish to access files on your Ubuntu partition either make a shared (NTFS) data partition or use fsdriver ro ext2read

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://ext2read.sf.net/](http://ext2read.sf.net/)

mmm... maybe I expressed my self bad, I dont want to access the files from Windows inside my PC, I want to access those files from a laptop running Windows, connected wireless via router to the PC that have Ubuntu and Windows, the thing is that I'm able, from the laptop that runs Windows to see every folder that I share via SAMBA on Ubuntu, but I cant access them coz I dont have permission, except fpr the folders that are in the Ubuntu partition, those files like the HOME folder for example I can access and copy and modify, is when I try to access the other HDD when I come across the error posted, so... if I'm able to see the partition were Ubuntu is installed I dont think it have something to do with the NTFS or ETX issue. I leave the SAMBA config without any username and password to ovoid this and also disable the firewall on the laptop for the same reason... I'm also able to see, in Ubuntu, the folder that I share in the laptop but, also, I cant access it.

---

### Post by bodhi.zazen on 2010-05-27
I will try to help if I can, but honestly your posts are verbose to the point that it is difficult to read and understand the nature of your problem.

My initial suggestion would be:

What are the ownership and permissions of the directories you are wanting to use on the server (Ubuntu) ?

---

### Post by fipem on 2010-05-27
> **bodhi.zazen said:**
> I will try to help if I can, but honestly your posts are verbose to the point that it is difficult to read and understand the nature of your problem.

My initial suggestion would be:

What are the ownership and permissions of the directories you are wanting to use on the server (Ubuntu) ?

You are right, I should have ask in the spanish forum...

To summarize, I have a PC with two hard disc drives, one of them is where I keep the downloaded files (lets call it D), the other hard disc is divided into two partitions, one for linux (lets call it L) and one for windows (lets call it W). This PC is connected via router and wireless to a laptop with windows on it. What I want is to stream the files from D to the laptop, and to achieve that I create a network connection via SAMBA to connect the PC to the laptop. It work, but not entirely since, from the laptop I can only access to L and not to D or W. As the files I want to stream are located on D I have to move them to L and then I can watch those files on the laptop, but I’m unable to see the other two hard disc drives. What annoy me is that I can actually see on the laptop the folders shared via SAMBA from Ubuntu but I cannot access them, when I try to do so is then I get the error message. In the laptop I also have a folder shared which I can see in Ubuntu throw the network connection but, also I’m unable to explore it.

Thanks anyway for your time and consideration.

Best regards from Valparaíso - Chile

---

### Post by bodhi.zazen on 2010-05-27
OK.

It sounds as if you simply need to define a share.

You can do this from the graphical interface (desktop) or by editing and configuring smb.conf.

[Downloads]
	comment = Descargas
	path = /media/Downloads
	writeable = yes
browseable = yes
	guest ok = yes

Also check that the user you are connecting with has rwx permissions on /media/Downloads.

In the future, IMO, it helps to use the Linux syntax

I want to share /media/Downloads ....

Rather then I want to share a partition on my second hard drive called "D"

This because I know how to convert /media/Downloads to a shamba share / fstab entry, etc

But I have no idea what to do with "D".

---

### Post by fipem on 2010-05-27
> **bodhi.zazen said:**
> OK.

It sounds as if you simply need to define a share.

You can do this from the graphical interface (desktop) or by editing and configuring smb.conf.

[Downloads]
	comment = Descargas
	path = /media/Downloads
	writeable = yes
browseable = yes
	guest ok = yes

Also check that the user you are connecting with has rwx permissions on /media/Downloads.

In the future, IMO, it helps to use the Linux syntax

I want to share /media/Downloads ....

Rather then I want to share a partition on my second hard drive called "D"

This because I know how to convert /media/Downloads to a shamba share / fstab entry, etc

But I have no idea what to do with "D".

Thanks for the reply, I have already try to share that folder and I got this error "Could not change the permissions of folder "media"" I tryed this by right clicking on the folder and selecting the sharing option...

---

### Post by bodhi.zazen on 2010-05-27
If it is a NTFS partition, you need to set the permissions in fstab and re mount it.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by fipem on 2010-05-27
> **bodhi.zazen said:**
> If it is a NTFS partition, you need to set the permissions in fstab and re mount it.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

Actually, both of the hard disk drive that I'm unable to access are NTFS partitions, I downloaded the Storage Device Manager and try to set the permissions as you said, but I got lost in the middle... could you please give me some instructions about how to do it? Thanks in advance!

---

### Post by bodhi.zazen on 2010-05-27
> **fipem said:**
> Actually, both of the hard disk drive that I'm unable to access are NTFS partitions, I downloaded the Storage Device Manager and try to set the permissions as you said, but I got lost in the middle... could you please give me some instructions about how to do it? Thanks in advance!

The instructions are in the link  I gave you, where did you get stuck ?

---

### Post by fipem on 2010-05-27
> **bodhi.zazen said:**
> The instructions are in the link  I gave you, where did you get stuck ?

How do I set permissions?

---

### Post by bodhi.zazen on 2010-05-27
> **fipem said:**
> How do I set permissions?

You set permissions in fstab , in the options column, using uid,gid,dmask,and fmaks.

there are specific examples in the link I gave you.

> **_VFAT/NTFS_**:

**Ownership and permissios of vfat / ntfs are set at the time of  mounting**. This is often a source of confusion.
 
uid= Sets owner. Syntax: may use user_name or user ID #.
gid= sets group ownership of mount point. Again may use group_name or  GID #.

umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
To set permissions of 700, umask=077

[COLOR=blue]Best is to set directories with executable  permissions and file with read write. To do this, use fmask and dmask  (rather then umask):
dmask=027
fmask=137

With these options files are not executable (all colored green in a  terminal w/ ls)[/COLOR]> [SIZE=2][B]Fstab Examples

[/B][/SIZE]# NTFS ~ Use ntfs-3g for write access (rw) 
# /dev/hda1
UUID=12102C02102CEB83  /media/windows  ntfs-3g   auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137   0  0

There is no space in "fmask=13 7" , it appears that way due to the way the text is rendered.

---


---
title: "SAMBA - Win share load"
date: 2011-05-12
forum: General Help
---

### Post by OldManRiver on 2011-05-12
All,

Have a problem with SAMBA and loading some Windows shares.  I have a backup program that runs and saves to external USB drives on a Windows server in my network.  The other Windows Servers are also using these (2 ea.) drives for backups.

I looked up the HOWTO on adding the Windows Share to "fstab" to autolink in the share, but noticed on the boot sequence that the eth0 has not loaded when "fstab" is executed, in the boot sequence, so the drives do not attach.

It therefore appears that I need to write a script, that can first manually attach these drive on the windows servers as SAMBA shares and then add this script to the boot sequence as the last item to run, so I know my drives are attached and the CRON backup jobs can run unhindered.

Does anyone know of a script that will at least get me close?

Also not finding what I need for adding the script to the boot sequence, in particular how to make sure it is the last item executed when placed there.

All help appreciated!!

Thanks!!!

OMR

---

### Post by papibe on 2011-05-13
Have you tried using the IP address instead of the name? 

Regards.

---

### Post by OldManRiver on 2011-05-13
All,

So wrote this to get the share to link manually:```
#! /bin/bash
# Auto link the Window shares

smbclient -L //wbox -U wuser
mkdir /mnt/wbox/wshare
mount -t smbfs -o username=wuser,password=wpass //wbox/wshare /mnt/wbox/wshare
ln -s /mnt/wbox/wshare /w_files
```
And I got these errors:
```
Unknown parameter encountered: "winbind enable local accounts"
Ignoring unknown parameter "winbind enable local accounts"
Enter wuser's password: 
Connection to wbox failed (Error NT_STATUS_UNSUCCESSFUL)
mkdir: cannot create directory `/mnt/wbox/wshare': No such file or directory
mount error: can not change directory into mount target /mnt/wbox/wshare

```
Not sure what the first set of errors about winbind is means and guess the 'mkdir' error is syntax, and of course the last error is due to that failure, but at least this is a start.

All help appreciated.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-13
> **papibe said:**
> Have you tried using the IP address instead of the name? 

Regards.
What good will that do since eth0 has not loaded or run its init yet?

No eth0 no network, so no links at all, right?

OMR

---

### Post by Morbius1 on 2011-05-13
Create a script that will mount it only after the network is up:
```
gksu gedit /etc/network/if-up.d/mount-again
```With this content:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/mount-again
```Any script placed in if-up.d will be executed only after the network is up. "mount -a" will mount anything defined in fstab that has not already been mounted and does not have the "noauto" option.

---

### Post by OldManRiver on 2011-05-15
Morbius1,

Followed your "step-by-step" and when I have network up run the script and do not get the shares.

Guess I have an issue with the declarations in my "fstab" but not sure how to debug.

Open to suggestions.

Thanks!

OMR

---

### Post by Morbius1 on 2011-05-16
Post your fstab:
```
cat /etc/fstab
```Did notice one thing about your earlier post:
> mkdir /mnt/wbox/wshare
mkdir: cannot create directory `/mnt/wbox/wshare': No such file or directoryIf there is no /mnt/wbox then you can't create a wshare directory within it.

Create the wbox folder first:
```
sudo mkdir /mnt/wbox
```Then create the wshare folder:
```
sudo mkdir /mnt/wbox/wshare
```

---

### Post by OldManRiver on 2011-05-18
Morbius1,

Ah yes we both noticed the same thing about the "mkdir" so already had that fixed before you posted.

Here are the contents of fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

# / was on /dev/sda1 during installation
# swap was on /dev/sda5 during installation

# Mount the SWAP Drive/DIR
UUID=9ced8ad1-6d96-47bb-82b9-9290cd08ac75 none            swap    sw              0       0


# Mount the local drives and devices
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Mount Local Shares for SAMBA
/home/files	/mnt/samba/home_files smbfs username=myuser,password=mypass 0 0
/shared_files	/mnt/samba/share_files smbfs username=myuser,password=mypass 0 0
/data		/mnt/samba/data smbfs username=myuser,password=mypass 0 0

# Mount Window Shares for SAMBA
//wbox/wdir /mnt/samba/wbox/wdir smbfs username=myuser,password=mypass 0 0

# Mount Dropbox share
# Commented out by Dropbox
# UUID=04a2abe3-5292-4077-bb59-3e06e7b0eeab /               ext4    errors=remount-ro 0       1
UUID=04a2abe3-5292-4077-bb59-3e06e7b0eeab / ext4 errors=remount-ro,user_xattr 0 1

```

Hope this helps!

OMR

---

### Post by Morbius1 on 2011-05-18
This is going to be a bit confusing but:

[1] Make sure the package smbfs is installed:
```
sudo apt-get install smbfs
```[2] Change "smbfs" to "cifs" in fstab since smbfs is deprecated. The line should read:
> //wbox/wdir /mnt/samba/wbox/wdir **[COLOR=Blue]cifs[/COLOR]** username=myuser,password=mypass 0 0The "smbfs" [COLOR=Blue]filesystem[/COLOR] has been replaced by cifs which may be part of your problem if the Windows you are using is not backward compatible with the old protocol. The "smbfs" [COLOR=Blue]package[/COLOR] however conains a set of utilities that allows the mounting and unmounting of cifs shares.

[COLOR=Blue]EDIT:[/COLOR] I'm not sure what's going on here:
> # Mount Local Shares for SAMBA
/home/files    /mnt/samba/home_files smbfs username=myuser,password=mypass 0 0
/shared_files    /mnt/samba/share_files smbfs username=myuser,password=mypass 0 0
/data        /mnt/samba/data smbfs username=myuser,password=mypass 0 0
That's not the right syntax for a remote share but luckily that's not part of your original question.

---

### Post by OldManRiver on 2011-05-18
Morbius1,

Thought I'd include the smb.conf for kickers:
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
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = SO_BROADCAST TCP_NODELAY IPTOS_LOWDELAY IPTOS_THROUGHPUT
	obey pam restrictions = yes
	sync always = yes
	map to guest = bad user
	winbind trusted domains only = yes
	winbind enable local accounts = no
	encrypt passwords = true
	public = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	wins support = true
	dns proxy = no
	server string = %h (Samba)
	path = /home/files
	unix password sync = yes
	workgroup = DAVISOFT
	os level = 20
	comment = Shared Home Files
	valid users = ndavis,@users
	syslog = 0
	create mode = 775
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes
	directory mode = 775

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
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
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


[data]
   path = /data
   comment = Shared Data Files
   browseable = yes
   writeable = yes
   read only = no
   guest ok = no
   create mask = 0770
   directory mask = 0775

[files]
   path = /home/files
   comment = Shared Home Files
   browseable = yes
   writeable = yes
   read only = no
   guest ok = no
   create mask = 0770
   directory mask = 0775

[shared]
   path = /shared_files
   comment = Shared Root Files
   browseable = yes
   writeable = yes
   read only = no
   guest ok = no
   create mask = 0770
   directory mask = 0775

[WLT_local]
   path = "//wireless_lt/local files"
   browseable = yes
   writeable = yes
   read only = no
   guest ok = no
   create mask = 0770
   create mode = 775
   directory mode = 775
```
Thought there was a method to link the last share (Win) using the WBox UID/PWD, but maybe that is what is in my script below.

Can not find a source that says I can use "smbclient" in the smb.conf, but if memory serves me right, I think that was how I did it years ago.  Anyway something is wrong with this smb.conf because my WBox sees the UBox but can not see the shares.

Here is the latest manual connect script:
```

#! /bin/bash
# Auto link the Window shares

smbclient -L //wireless_lt -U myuser
mkdir /mnt/samba/wireless_lt
mkdir /mnt/samba/wireless_lt/wireless_lf
mount -t smbfs -o username=myuser,password=mypass //wbox/wdir /mnt/samba/wbox/wdir
#ln -s /mnt/samba/wbox/wdir /WLS_lfiles

```
This is now working but does not link to the dir declared in the "mkdir" but rather under the samba root "/mnt/samba".  This becomes a huge problem when more than one Win Share is added, if the subdirs are not passed and included.

Your comments and feedback please!

Thanks!

OMR

---

### Post by Morbius1 on 2011-05-18
You are out of my class I'm afraid. I should have asked you to post your smb.conf earlier.

* I have no idea what a UID/PWD is.

* you have "wins support = yes" which has turned your Ubuntu machine into a wins server. Nothing wrong with that as long as all your client machines are pointing to this box for name resolution.

* You've got a lot of winbind references which for a home lan is out of place. Maybe it has to do with whatever a UID/PWD is.

* You've got a lot of suff in the [global] section which from what I can see belongs in the [files] section: 
   >  path = /home/files
    comment = Shared Home Files
    valid users = ndavis,@usersI suppose it would still work as it has become the default and must be  overriden for every other share but it makes the output of the command "[COLOR=Blue]testparm -s[/COLOR]" look funny.

* I have never seen anything like this in my life:
> [WLT_local]
**[COLOR=Blue]   path = "//wireless_lt/local files"[/COLOR]**
   browseable = yes
   writeable = yes
   read only = no
   guest ok = no
   create mask = 0770
   create mode = 775
   directory mode = 775I am 86.42% positive that you can't have a share path with that syntax. You're creating a share on Ubuntu that points to another share on another server?

---

### Post by OldManRiver on 2011-05-21
> **Morbius1 said:**
> You are out of my class I'm afraid. I should have asked you to post your smb.conf earlier.

* I have no idea what a UID/PWD is.

* you have "wins support = yes" which has turned your Ubuntu machine into a wins server. Nothing wrong with that as long as all your client machines are pointing to this box for name resolution.

* You've got a lot of winbind references which for a home lan is out of place. Maybe it has to do with whatever a UID/PWD is.

* You've got a lot of suff in the [global] section which from what I can see belongs in the [files] section: 
   I suppose it would still work as it has become the default and must be  overriden for every other share but it makes the output of the command "[COLOR=Blue]testparm -s[/COLOR]" look funny.

* I have never seen anything like this in my life:
I am 86.42% positive that you can't have a share path with that syntax. You're creating a share on Ubuntu that points to another share on another server?

Morbius1,

How long you been around Linux?  UID/PWD has always stood for UserID/PassWord combo.

I think you are right about all the extras concerning the remote share.  Getting those out to see what I get.  I think I already disabled the windbind, but checking and knocking out all the stupid comments this file came with.

Not sure what to look at if that doesn't doe it but here goes nothing or everything!

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-21
Morbis1,

OK got my smb.conf down to:
```

#======================= Global Settings =======================
[global]
	comment = Global SAMBA Settings
	workgroup = DAVISOFT
	log file = /var/log/samba/log.%m
	map to guest = bad user
	public = yes
	dns proxy = no
	name resolve order = lmhosts host wins bcast
	syslog = 0
#        interfaces = 127.0.0.0/8 eth0
#        security = user
#        domain logons = yes
#        socket options = TCP_NODELAY

#======================= Share Definitions =======================
;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   load printers = yes
   printcap name = /etc/printcap
   printing = cups
   printcap name = cups

[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /cdrom
   guest ok = yes
   /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[data]
   path = /data
   comment = Shared Data Files
   browseable = yes
   writeable = yes
   read only = no
   guest ok = no
   create mask = 0770
   directory mask = 0775

[files]
   path = /home/files
   comment = Shared Home Files
   browseable = yes
   writeable = yes
   read only = no
   guest ok = yes
   create mask = 0770
   directory mask = 0775

[shared]
   path = /shared_files
   comment = Shared Root Files
   browseable = yes
   writeable = yes
   read only = no
   guest ok = yes
   create mask = 0770
   directory mask = 0775

[WLT_local]
   path = "//wireless_lt/local files"
   browseable = yes
   writeable = yes
   read only = no
   guest ok = yes

```
Retrying this again.

OMR

---

### Post by OldManRiver on 2011-05-21
All,

Hey all the share are now showing under "Network" on the Linux side, including the Windows share, but still getting errors accessing from the Windows side.

Also able to link and open, from Linux, the "cdrom", "files" and "shared" folders, but the other error.  Looking at the good vs. bad now.

Sure it is something about user permissions, on both sides, so need that right so all works.

All help appreciated!

Thanks!

OMR

---

### Post by OldManRiver on 2011-06-04
All,

Think the DHCP in my network router is flaky, replacing it next week and will see if that corrects the errors.

Thanks!

OMR

---

### Post by norms360 on 2011-12-02
> **Morbius1 said:**
> Create a script that will mount it only after the network is up:
```
gksu gedit /etc/network/if-up.d/mount-again
```With this content:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/mount-again
```Any script placed in if-up.d will be executed only after the network is up. "mount -a" will mount anything defined in fstab that has not already been mounted and does not have the "noauto" option.

I stumbled across this post when I was having trouble getting ubuntu to automatically mount and make available my NAS to XBMC.  I made the correct fstab entry but quickly realised that the wireless connection was not available when this entry was being executed.  Creating this file worked perfectly for me, many thanks!

---

### Post by OldManRiver on 2011-12-07
All,

Sorry have not updated this.  Reason the smbclient and win share is not working is LAN uses WiFi router to let laptops get it inet, but did not open an IP or DMZ for laptops and printers to get through the WiFi router into the LAN.

This router is LinkSys WRT54G-TM, so looking up the WRT54G family of routers and HOWTO on that to get final resolve on this.

Thanks for your patience!

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #20 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---


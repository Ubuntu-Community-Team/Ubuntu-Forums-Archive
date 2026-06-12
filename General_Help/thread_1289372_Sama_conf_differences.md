---
title: "Sama conf differences"
date: 2009-10-12
forum: General Help
---

### Post by infinitelink on 2009-10-12
Hey guys,

I'm installing updates and have been confronted--maybe too connotatively harsh, 'presented'--with 
<BLOCKQUOTE>A new version of configuration file /etc/samba/smb.conf is available, but the version installed currently has been locally modified</BLOCKQUOTE>.

I chose the option to compare the local and new version of conf side-by-side, which output,

<BLOCKQUOTE>
# #
# Sample configuration file for the Samba suite for Debian GN # Sample configuration file for the Samba suite for Debian GN
# #
# #
# This is the main Samba configuration file. You should read # This is the main Samba configuration file. You should read 
# smb.conf(5) manual page in order to understand the options # smb.conf(5) manual page in order to understand the options 
# here. Samba has a huge number of configurable options most # here. Samba has a huge number of configurable options most 
# are not shown in this example # are not shown in this example
# #
# Some options that are often worth tuning have been included # Some options that are often worth tuning have been included
# commented-out examples in this file. # commented-out examples in this file.
# - When such options are commented with ";", the proposed s # - When such options are commented with ";", the proposed s
# differs from the default Samba behaviour # differs from the default Samba behaviour
# - When commented with "#", the proposed setting is the def # - When commented with "#", the proposed setting is the def
# behaviour of Samba but the option is considered importan # behaviour of Samba but the option is considered importan
# enough to be mentioned here # enough to be mentioned here
# #
# NOTE: Whenever you modify this file you should run the comm # NOTE: Whenever you modify this file you should run the comm
# "testparm" to check that you have not made any basic syntac # "testparm" to check that you have not made any basic syntac
# errors. # errors. 
# A well-established practice is to name the original file # A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with # "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf # testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file # This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance # which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contai # However, use this with caution if your smb.conf file contai
# "include" statements. See Debian bug #483187 for a case # "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea. # where using a master file is not a good idea.
# #

#======================= Global Settings ==================== #======================= Global Settings ====================

[global] [global]

## Browsing/Identification ### ## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba serv # Change this to the workgroup/NT-domain name your Samba serv
 workgroup = WORKGROUP workgroup = WORKGROUP

# server string is the equivalent of the NT Description field # server string is the equivalent of the NT Description field
 server string = %h server (Samba, Ubuntu) server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section: # Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable # WINS Support - Tells the NMBD component of Samba to enable 
# wins support = no # wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WI # WINS Server - Tells the NMBD components of Samba to be a WI
# Note: Samba can be either a WINS Server, or a WINS Client, # Note: Samba can be either a WINS Server, or a WINS Client, 
; wins server = w.x.y.z ; wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through # This will prevent nmbd to search for NetBIOS names through 
 dns proxy = no dns proxy = no

# What naming service and in what order should we use to reso # What naming service and in what order should we use to reso
# to IP addresses # to IP addresses
; name resolve order = lmhosts host wins bcast ; name resolve order = lmhosts host wins bcast

#### Networking #### #### Networking ####

# The specific set of interfaces / networks to bind to # The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netm # This can be either the interface name or an IP address/netm
# interface names are normally preferred # interface names are normally preferred
; interfaces = 127.0.0.0/8 eth0 ; interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must # Only bind to the named interfaces and/or networks; you must
# 'interfaces' option above to use this. # 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samb # It is recommended that you enable this feature if your Samb
# not protected by a firewall or is a firewall itself. Howev # not protected by a firewall or is a firewall itself. Howev
# option cannot handle dynamic or non-broadcast interfaces co # option cannot handle dynamic or non-broadcast interfaces co
; bind interfaces only = yes ; bind interfaces only = yes



#### Debugging/Accounting #### #### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machin # This tells Samba to use a separate log file for each machin
# that connects # that connects
 log file = /var/log/samba/log.%m log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB). # Cap the size of the individual log files (in KiB).
 max log size = 1000 max log size = 1000

# If you want Samba to only log through syslog then set the f # If you want Samba to only log through syslog then set the f
# parameter to 'yes'. # parameter to 'yes'.
# syslog only = no # syslog only = no

# We want Samba to log a minimum amount of information to sys # We want Samba to log a minimum amount of information to sys
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you # should go to /var/log/samba/log.{smbd,nmbd} instead. If you
# through syslog you should set the following parameter to so # through syslog you should set the following parameter to so
 syslog = 0 syslog = 0

# Do something sensible when Samba crashes: mail the admin a # Do something sensible when Samba crashes: mail the admin a 
 panic action = /usr/share/samba/panic-action %d panic action = /usr/share/samba/panic-action %d


####### Authentication ####### ####### Authentication #######

# "security = user" is always a good idea. This will require # "security = user" is always a good idea. This will require 
# in this server for every user accessing the server. See # in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.h # /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.h
# in the samba-doc package for details. # in the samba-doc package for details.
# security = user # security = user

# You may wish to use password encryption. See the section o # You may wish to use password encryption. See the section o
# 'encrypt passwords' in the smb.conf(5) manpage before enabl # 'encrypt passwords' in the smb.conf(5) manpage before enabl
 encrypt passwords = true encrypt passwords = true

# If you are using encrypted passwords, Samba will need to kn # If you are using encrypted passwords, Samba will need to kn
# password database type you are using. # password database type you are using. 
 passdb backend = tdbsam passdb backend = tdbsam

 obey pam restrictions = yes obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to s # This boolean parameter controls whether Samba attempts to s
# password with the SMB password when the encrypted SMB passw # password with the SMB password when the encrypted SMB passw
# passdb is changed. # passdb is changed.
 unix password sync = yes unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system # For Unix password sync to work on a Debian GNU/Linux system
# parameters must be set (thanks to Ian Kahan <<kahan@informa # parameters must be set (thanks to Ian Kahan <<kahan@informa
# sending the correct chat script for the passwd program in D # sending the correct chat script for the passwd program in D
 passwd program = /usr/bin/passwd %u passwd program = /usr/bin/passwd %u
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew

# This boolean controls whether PAM will be used for password # This boolean controls whether PAM will be used for password
# when requested by an SMB client instead of the program list # when requested by an SMB client instead of the program list
# 'passwd program'. The default is 'no'. # 'passwd program'. The default is 'no'.
 pam password change = yes pam password change = yes

# This option controls how unsuccessful authentication attemp # This option controls how unsuccessful authentication attemp
# to anonymous connections # to anonymous connections
 map to guest = bad user map to guest = bad user

########## Domains ########### ########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BD # Is this machine able to authenticate users. Both PDC and BD
# must have this setting enabled. If you are the BDC you must # must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no # change the 'domain master' setting to no
# #
; domain logons = yes ; domain logons = yes
# #
# The following setting only takes effect if 'domain logons' # The following setting only takes effect if 'domain logons' 
# It specifies the location of the user's profile directory # It specifies the location of the user's profile directory
# from the client point of view) # from the client point of view)
# The following required a [profiles] share to be setup on th # The following required a [profiles] share to be setup on th
# samba server (see below) # samba server (see below)
; logon path = \\%N\profiles\%U ; logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's # Another common choice is storing the profile in the user's 
# (this is Samba's default) # (this is Samba's default)
# logon path = \\%N\%U\profile # logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' # The following setting only takes effect if 'domain logons' 
# It specifies the location of a user's home directory (from # It specifies the location of a user's home directory (from 
# point of view) # point of view)
; logon drive = H: ; logon drive = H:
# logon home = \\%N\%U # logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' # The following setting only takes effect if 'domain logons' 
# It specifies the script to run during logon. The script mus # It specifies the script to run during logon. The script mus
# in the [netlogon] share # in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention # NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd ; logon script = logon.cmd

# This allows Unix users to be created on the domain controll # This allows Unix users to be created on the domain controll
# RPC pipe. The example command creates a user account with # RPC pipe. The example command creates a user account with 
# password; please adapt to your needs # password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-pass ; add user script = /usr/sbin/adduser --quiet --disabled-pass

# This allows machine accounts to be created on the domain co # This allows machine accounts to be created on the domain co
# SAMR RPC pipe. # SAMR RPC pipe. 
# The following assumes a "machines" group exists on the syst # The following assumes a "machines" group exists on the syst
; add machine script = /usr/sbin/useradd -g machines -c "%u ; add machine script = /usr/sbin/useradd -g machines -c "%u 

# This allows Unix groups to be created on the domain control # This allows Unix groups to be created on the domain control
# RPC pipe. # RPC pipe. 
; add group script = /usr/sbin/addgroup --force-badname %g ; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ########## ########## Printing ##########

# If you want to automatically load your printer list rather # If you want to automatically load your printer list rather
# than setting them up individually then you'll need this # than setting them up individually then you'll need this
# load printers = yes # load printers = yes

# lpr(ng) printing. You may wish to override the location of # lpr(ng) printing. You may wish to override the location of 
# printcap file # printcap file
; printing = bsd ; printing = bsd
; printcap name = /etc/printcap ; printcap name = /etc/printcap

# CUPS printing. See also the cupsaddsmb(8) manpage in the # CUPS printing. See also the cupsaddsmb(8) manpage in the
# cupsys-client package. # cupsys-client package.
; printing = cups ; printing = cups
; printcap name = cups ; printcap name = cups

############ Misc ############ ############ Misc ############

# Using the following line enables you to customise your conf # Using the following line enables you to customise your conf
# on a per machine basis. The %m gets replaced with the netbi # on a per machine basis. The %m gets replaced with the netbi
# of the machine that is connecting # of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m ; include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better perform # Most people will find that this option gives better perform
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba # See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba
# for details # for details
# You may want to add the following on a Linux system: # You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192 # SO_RCVBUF=8192 SO_SNDBUF=8192
# socket options = TCP_NODELAY # socket options = TCP_NODELAY

# The following parameter is useful only if you have the linp # The following parameter is useful only if you have the linp
# installed. The samba maintainer and the linpopup maintainer # installed. The samba maintainer and the linpopup maintainer
# working to ease installation and configuration of linpopup # working to ease installation and configuration of linpopup 
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" ; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m"

# Domain Master specifies Samba to be the Domain Master Brows # Domain Master specifies Samba to be the Domain Master Brows
# machine will be configured as a BDC (a secondary logon serv # machine will be configured as a BDC (a secondary logon serv
# must set this to 'no'; otherwise, the default behavior is r # must set this to 'no'; otherwise, the default behavior is r
# domain master = auto # domain master = auto

# Some defaults for winbind (make sure you're not using the r # Some defaults for winbind (make sure you're not using the r
# for something else.) # for something else.)
; idmap uid = 10000-20000 ; idmap uid = 10000-20000
; idmap gid = 10000-20000 ; idmap gid = 10000-20000
; template shell = /bin/bash ; template shell = /bin/bash

# The following was the default behaviour in sarge, # The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might in # but samba upstream reverted the default because it might in
# performance issues in large organizations. # performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not # See Debian bug #368251 for some of the consequences of *not
# having this setting and smb.conf(5) for details. # having this setting and smb.conf(5) for details.
; winbind enum groups = yes ; winbind enum groups = yes
; winbind enum users = yes ; winbind enum users = yes

# Setup usershare options to enable non-root users to share f # Setup usershare options to enable non-root users to share f
# with the net usershare command. # with the net usershare command.

# Maximum number of usershare. 0 (default) means that usersha # Maximum number of usershare. 0 (default) means that usersha
; usershare max shares = 100 ; usershare max shares = 100

# Allow users who've been granted usershare privileges to cre # Allow users who've been granted usershare privileges to cre
# public shares, not just authenticated ones # public shares, not just authenticated ones
 usershare allow guests = yes usershare allow guests = yes

#======================= Share Definitions ================== #======================= Share Definitions ==================

# Un-comment the following (and tweak the other settings belo # Un-comment the following (and tweak the other settings belo
# to enable the default home directory shares. This will sha # to enable the default home directory shares. This will sha
# user's home directory as \\server\username # user's home directory as \\server\username
;[homes] ;[homes]
; comment = Home Directories ; comment = Home Directories
; browseable = no ; browseable = no

# By default, the home directories are exported read-only. Ch # By default, the home directories are exported read-only. Ch
# next parameter to 'no' if you want to be able to write to t # next parameter to 'no' if you want to be able to write to t
; read only = yes ; read only = yes

# File creation mask is set to 0700 for security reasons. If # File creation mask is set to 0700 for security reasons. If 
# create files with group=rw permissions, set next parameter # create files with group=rw permissions, set next parameter 
; create mask = 0700 ; create mask = 0700

# Directory creation mask is set to 0700 for security reasons # Directory creation mask is set to 0700 for security reasons
# create dirs. with group=rw permissions, set next parameter # create dirs. with group=rw permissions, set next parameter 
; directory mask = 0700 ; directory mask = 0700

# By default, \\server\username shares can be connected to by # By default, \\server\username shares can be connected to by
# with access to the samba server. Un-comment the following # with access to the samba server. Un-comment the following 
# to make sure that only "username" can connect to \\server\u # to make sure that only "username" can connect to \\server\u
# This might need tweaking when using external authentication # This might need tweaking when using external authentication
; valid users = %S ; valid users = %S

# Un-comment the following and create the netlogon directory # Un-comment the following and create the netlogon directory 
# (you need to configure Samba to act as a domain controller # (you need to configure Samba to act as a domain controller 
;[netlogon] ;[netlogon]
; comment = Network Logon Service ; comment = Network Logon Service
; path = /home/samba/netlogon ; path = /home/samba/netlogon
; guest ok = yes ; guest ok = yes
; read only = yes ; read only = yes
; share modes = no ; share modes = no

# Un-comment the following and create the profiles directory # Un-comment the following and create the profiles directory 
# users profiles (see the "logon path" option above) # users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller # (you need to configure Samba to act as a domain controller 
# The path below should be writable by all users so that thei # The path below should be writable by all users so that thei
# profile directory may be created the first time they log on # profile directory may be created the first time they log on
;[profiles] ;[profiles]
; comment = Users profiles ; comment = Users profiles
; path = /home/samba/profiles ; path = /home/samba/profiles
; guest ok = no ; guest ok = no
; browseable = no ; browseable = no
; create mask = 0600 ; create mask = 0600
; directory mask = 0700 ; directory mask = 0700

wins support = no <
[printers] [printers]
 comment = All Printers comment = All Printers
 browseable = no browseable = no
 path = /var/spool/samba path = /var/spool/samba
 printable = yes printable = yes
 guest ok = no guest ok = no
 read only = yes read only = yes
 create mask = 0700 create mask = 0700

# Windows clients look for this share name as a source of dow # Windows clients look for this share name as a source of dow
# printer drivers # printer drivers
[print$] [print$]
 comment = Printer Drivers comment = Printer Drivers
 path = /var/lib/samba/printers path = /var/lib/samba/printers
 browseable = yes browseable = yes
 read only = yes read only = yes
 guest ok = no guest ok = no
# Uncomment to allow remote administration of Windows print d # Uncomment to allow remote administration of Windows print d
# You may need to replace 'lpadmin' with the name of the grou # You may need to replace 'lpadmin' with the name of the grou
# admin users are members of. # admin users are members of.
# Please note that you also need to set appropriate Unix perm # Please note that you also need to set appropriate Unix perm
# to the drivers directory for these users to have write righ # to the drivers directory for these users to have write righ
; write list = root, @lpadmin ; write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others. # A sample share for sharing your CD-ROM with others.
;[cdrom] ;[cdrom]
; comment = Samba server's CD-ROM ; comment = Samba server's CD-ROM
; read only = yes ; read only = yes
; locking = no ; locking = no
; path = /cdrom ; path = /cdrom
; guest ok = yes ; guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM whe # The next two parameters show how to auto-mount a CD-ROM whe
# cdrom share is accesed. For this to work /etc/fstab m # cdrom share is accesed. For this to work /etc/fstab m
# an entry like this: # an entry like this:
# #
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user # /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 
# #
# The CD-ROM gets unmounted automatically after the connectio # The CD-ROM gets unmounted automatically after the connectio
# #
# If you don't want to use auto-mounting/unmounting make sure # If you don't want to use auto-mounting/unmounting make sure
# is mounted on /cdrom # is mounted on /cdrom
# #
; preexec = /bin/mount /cdrom ; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom ; postexec = /bin/umount /cdrom

 [File System]
[File System] path = /
path = / available = yes
available = yes browsable = yes
browsable = yes public = yes
public = yes writable = no
writable = no (
</BLOCKQUOTE>

So several questions. The first is, any way I can discover how/whether some other program is reliant upon this config file? Another is, advice on what option to choose? The last is, how important is samba, and why would it be localy modified (I certainly haven't done it, and I'm unsure whether another program has for some needy reason, or something, hence the first question). 

Thanks much to all who may help. Just in case: running Xubuntu though much of Gnome (for dependencies, Gnome-do, etc. is installed (doubt that being Xu... rather than one of the others affects this issue, though).

---

### Post by pricetech on 2009-10-12
> **infinitelink said:**
> 
So several questions. The first is, any way I can discover how/whether some other program is reliant upon this config file? Another is, advice on what option to choose? The last is, how important is samba, and why would it be localy modified (I certainly haven't done it, and I'm unsure whether another program has for some needy reason, or something, hence the first question). 

There shouldn't be anything but Samba using your smb.conf file.
Choose the option to keep your current smb.conf.
Samba is used to communicate with winders for file and printer sharing.  Your smb.conf file would have gotten modified if you did anything with Samba after it was installed, such as add a share, or if you installed a printer since Samba shares them automatically.

---

### Post by infinitelink on 2009-10-12
Thanks for the advice. : )

---


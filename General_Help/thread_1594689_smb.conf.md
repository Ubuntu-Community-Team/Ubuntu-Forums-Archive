---
title: "smb.conf"
date: 2010-10-12
forum: General Help
---

### Post by Swiftjay on 2010-10-12
I've just tried to install smb and i've done the walk thorugh on the site but I can't seem to access public.

Here is my smb.conf code:

```

#======================= Global Settings=======================

[global]

## Browsing/Identification ###
   
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = JOSEPH

# server string is the equivalent of the NT Description field
   server string = %h james (Samba, Ubuntu)

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
   interfaces = 127,0,0,1, 192.168.0.101/24 eth0
;   interfaces = 127.0.0.0/8  eth0

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
;   security = user
    security = share
    guest account = nobody
# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = false
;   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
#   passdb backend = tdbsam

;   obey pam restrictions = yes

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
   load printers = yes

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
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = yes

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
   guest ok = yes
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
# [Files]
;   comment = Shared folder
;   read only = no
;   locking = no
;   path = /home/james/Downloads
;   guest ok = yes


 [public]
   comment = Shared folder
   path = /home/jay/Downloads
   read only = no
   guest only = no
   guest ok = yes

```But when I go into the network in windows it say's checkname of folder and spelling etc.

Any idea's on what i'm doing wrong?

---

### Post by Carlbc18 on 2010-10-12
what is the output you get if you do:

```
sudo testparm
```

from a terminal window?

attach what it says for [public]

---

### Post by luvshines on 2010-10-12
Also may give this a try.
1. Change 'encrypt password = yes'
2. Make sure every directory starting from / upto Downloads is having a permission of atleast 755

Then do , 'sudo service smbd restart' and give it a try

---

### Post by Swiftjay on 2010-10-12
from tesparm

```
 Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = JOSEPH
    server string = %h james (Samba, Ubuntu)
    interfaces = 127, 0, 0, 1, 192.168.0.101/24, eth0
    security = SHARE
    map to guest = Bad User
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
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

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    guest ok = Yes

[public]
    comment = Shared folder
    path = /home/jay/Downloads
    read only = No
    guest ok = Yes

```so that's fine, going to test the setting on the smb.conf from what you said about encryption = yes will edit post with results

*edit*

Yes that worked perfectly I set the chmod on my home folder to 755 and that allowed me to share the files just fine. 

Now, the only problem I have left is sharing the printer, where would I put windows printer drivers to, how would that get set up?

---

### Post by Morbius1 on 2010-10-12
>  Now, the only problem I have left is sharing the printer, where would I  put windows printer drivers to, how would that get set up?
Are you trying to access a Linux attached printer from Windows?

Or a Windows attached printer from Linux?

---

### Post by Swiftjay on 2010-10-12
> **Morbius1 said:**
> Are you trying to access a Linux attached printer from Windows?

Or a Windows attached printer from Linux?
I'm trying to access a linux attached pritner from windows.  I thought I set up the cups config in my smb.  I just now uncommented the smb.conf to allow cups to pick up my printer.  But it can't find the driver for it.

---

### Post by Morbius1 on 2010-10-12
I'm sorry I don't know what this means:
> I just now uncommented the smb.conf to allow cups to pick up my printer.CUPS will pick up your printer regardless of what smb.conf says. In fact you don't need Samba to access a printer from windows.

Can you print to the printer from Linux? And have you configured cups to share and publish the printer.

Just so I understand the problem, Windows can see the printer but it can't find a driver for it?

---

### Post by Swiftjay on 2010-10-12
> **Morbius1 said:**
> I'm sorry I don't know what this means:
CUPS will pick up your printer regardless of what smb.conf says. In fact you don't need Samba to access a printer from windows.

Can you print to the printer from Linux? And have you configured cups to share and publish the printer.

Just so I understand the problem, Windows can see the printer but it can't find a driver for it?

Yes windows can see the printer, but it cannot get the driver for it.  In cups, do I need to add windows drivers to the printer?

---

### Post by Morbius1 on 2010-10-12
You need to add windows printer drivers in windows. Linux wouldn't know what to do with them. Do you not have the drivers for it?

---

### Post by Swiftjay on 2010-10-12
> **Morbius1 said:**
> You need to add windows printer drivers in windows. Linux wouldn't know what to do with them. Do you not have the drivers for it?


I can get them from brother website, however I wanted to find a place where I could put them in my linux machine so it could load them up in the future.  But if that can't be done, then that's fine.

*edit* Windows had the drivers pre-loaded, it's a bit weird it say's access denied to the printer but when I printed a test page it worked so everything seems alright.

Thanks for all the help guy's closing thread as I got all the help I needed.

---

### Post by luvshines on 2010-10-12
I am just wondering about the 'encrypt passwords' values.

man pages says yes/no
Default smb.conf says true/false

Do they support both :confused:

---

### Post by Swiftjay on 2010-10-12
> **luvshines said:**
> I am just wondering about the 'encrypt passwords' values.

man pages says yes/no
Default smb.conf says true/false

Do they support both :confused:


Well, considering I changed it from yes from false it seems so, that or maybe it was cause I changed permissions on folders to 755 so that they were all readable each is a possibility.

---


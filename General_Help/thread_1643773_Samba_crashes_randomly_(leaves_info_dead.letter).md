---
title: "Samba crashes randomly (leaves info dead.letter)"
date: 2010-12-12
forum: General Help
---

### Post by V-Turn on 2010-12-12
Hi,

I am using samba to share some folders from a Ubuntu server (10.04) onto Windows XP. This works fine, but once in a while (once/twice a day), samba crashes and leaves a dead.letter in the folder I was accessing.

Here are mode details:

_lsb_release -a_
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:        10.04
Codename:       lucid

```

_dead.letter_
```
To: root
Subject: Panic or segfault in Samba

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 12882 ().

This means there was a problem with the program, such as a segfault.
However, the executable could not be found for process 12882.
It may have died unexpectedly, or you may not have permission to debug the process.
```

_dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | grep samba_
```
libpam-smbpass 2:3.4.7~dfsg-1ubuntu3.2 samba install ok installed
libsmbclient 2:3.4.7~dfsg-1ubuntu3.2 samba install ok installed
libwbclient0 2:3.4.7~dfsg-1ubuntu3.2 samba install ok installed
samba 2:3.4.7~dfsg-1ubuntu3.2  install ok installed
samba-common 2:3.4.7~dfsg-1ubuntu3.2 samba install ok installed
samba-common-bin 2:3.4.7~dfsg-1ubuntu3.2 samba install ok installed
smbclient 2:3.4.7~dfsg-1ubuntu3.2 samba install ok installed
```

_/var/log/samba_
```
[2010/12/12 15:24:55,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/vturn-home failed. Permission denied
[2010/12/12 15:24:55,  0] lib/substitute.c:560(alloc_sub_basic)
  alloc_sub_basic: NULL source string!  This should not happen
[2010/12/12 15:24:55,  0] lib/substitute.c:560(alloc_sub_basic)
  alloc_sub_basic: NULL source string!  This should not happen
[2010/12/12 15:24:55,  0] lib/fault.c:46(fault_report)
  ===============================================================
[2010/12/12 15:24:55,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 29420 (3.4.7)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2010/12/12 15:24:55,  0] lib/fault.c:49(fault_report)

  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2010/12/12 15:24:55,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2010/12/12 15:24:55,  0] lib/util.c:1480(smb_panic)
  PANIC (pid 29420): internal error
[2010/12/12 15:24:55,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 19 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb73d662d]
   #1 smbd(smb_panic+0x2d) [0xb73d674d]
   #2 smbd(+0x31cc8e) [0xb73c3c8e]
   #3 [0xb7089400]
   #4 smbd(+0xdfb87) [0xb7186b87]
   #5 smbd(+0xec66f) [0xb719366f]
   #6 smbd(reply_trans2+0x71e) [0xb719509e]
   #7 smbd(+0x112c0e) [0xb71b9c0e]
   #8 smbd(+0x11307d) [0xb71ba07d]
   #9 smbd(+0x113958) [0xb71ba958]
   #10 smbd(run_events+0x124) [0xb73e7d24]
   #11 smbd(smbd_process+0x7d2) [0xb71b94a2]
   #12 smbd(+0x615a38) [0xb76bca38]
   #13 smbd(run_events+0x124) [0xb73e7d24]
   #14 smbd(+0x340fcf) [0xb73e7fcf]
   #15 smbd(_tevent_loop_once+0x98) [0xb73e8618]
   #16 smbd(main+0xcaa) [0xb76bd77a]
   #17 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb6bf8bd6]
   #18 smbd(+0x8b231) [0xb7132231]
[2010/12/12 15:24:55,  0] lib/util.c:1485(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 29420]
/usr/lib/sendmail: No such file or directory
[2010/12/12 15:24:55,  0] lib/util.c:1493(smb_panic)
  smb_panic(): action returned status 0
[2010/12/12 15:24:55,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
. . . message not sent.
```

This seems related to this bug : [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/407297](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/407297), which does not seem to have been resolved yet ([https://bugzilla.samba.org/show_bug.cgi?id=6725](https://bugzilla.samba.org/show_bug.cgi?id=6725)).

I'm not sure what to do there, should I open a bug myself?

Thank you for the advice.

V.

---

### Post by V-Turn on 2010-12-17
Any kind soul to let me know how I should proceed?

Thank you.

V.

---

### Post by Don Barzini on 2010-12-17
Post the contents of your **/etc/samba/smb.conf** file.

---

### Post by V-Turn on 2010-12-17
Thank you for the reply, here is my file (I stripped down the header with many comments
```
#======================= Global Settings =======================

[global]

usershare owner only = false
netbios name = maya
local master = false

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

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
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

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


```

---

### Post by Don Barzini on 2010-12-17
That is your **smb.conf** file from an Ubuntu 10.04 server?

It doesn't look like you have any share definitions created. What directory/directories on the server do you wish to share?

You also need to set a security level such as **User** or **Share**.

Is your Win XP box set for the workgroup WORKGROUP? You can set the workgroup with the Network Setup Wizard on the XP box. Both the Samba server and Windows boxes need to be set for the same workgroup name.

Also, prior to doing anything, make sure the server packages are up to date. Run....

```
sudo apt-get update
```

then...
 
```
sudo apt-get upgrade
```

You will also need to create Samba accounts for the users to connect to the Samba share using the **smbpasswd** command. E.g...

```
smbpasswd -a username
```

Then make sure permissioning is correct on the shares.

Have you done any of this yet?

---

### Post by V-Turn on 2010-12-17
Thank you again for the help.

Drive sharing works, the folders are accessible and password protected. However, I created shares from Nautilus (selecting folders and right-clicking, then choosing the "share" option), I never touched the samba configuration file, actually. So my share config is in **/var/lib/samba/usershares**. Also, **net usershare info** returns those shares config properly.

I doubt the problem has anything to do with the shares themselves as the symptoms are those random crashes. If anything at all, this would be in the smbd.conf.

Regarding upgrading to 10.10 yet, I'm not quite ready to do so yet, but all smb packages are up-to-date on 10.04

Thank you.

V.

---

### Post by Don Barzini on 2010-12-17
> **V-Turn said:**
> Thank you again for the help.

Drive sharing works, the folders are accessible and password protected. However, I created shares from Nautilus (selecting folders and right-clicking, then choosing the "share" option)

Nautilus?  So then you are **not** using Ubuntu Server 10.04

> Regarding upgrading to 10.10 yet, I'm not quite ready to do so yet, but all smb packages are up-to-date on 10.04

I didn't say to upgrade to version 10.10. I said to upgrade your packages.

---

### Post by V-Turn on 2010-12-19
> **Don Barzini said:**
> Nautilus?  So then you are **not** using Ubuntu Server 10.04

I didn't say to upgrade to version 10.10. I said to upgrade your packages.
Ah, sorry for the misunderstanding. I use the machine as a server, even though it is Ubuntu Desktop.

Any advice on how to proceed with the samba crashes?

V.

---

### Post by V-Turn on 2010-12-29
Bumping for advice.

V.

---

### Post by muederkrieger on 2011-02-08
Have the same issue (identical backtrace) but also no solution.

It happens always I access the share first time with Windows XP client, running in a virtualbox (any version) with host-only-network. 
And it happens spontaneously later on. 

Windows 7 client looks like working fine.

---


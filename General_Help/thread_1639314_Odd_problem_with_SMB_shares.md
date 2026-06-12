---
title: "Odd problem with SMB shares"
date: 2010-12-06
forum: General Help
---

### Post by paulttt on 2010-12-06
Hi there, relatively new so please bare with me :)

I have Ubuntu 10.04 set up on my acer revo, this is connected to a wireless router via ethernet.  Next door, is a pc that is running windows XP, and an original XBOX running XBMC.  Those are connected via a crossover cable. The XP machine connects to the web wirelessly using my router, and the connections are bridged for XBMC's TV show scrappers.

The idea is we use the revo for downloading as it consumes a relatively small ammount of electricity. I have two external 1tb drives connected to the revo with Tv shows and movies, I would set up a network share so the XP machine could see them, and the xbox would be able to share the videos present.

I have installed samba, right clicked the drives in question and clicked the sharing options.  I have ticked to allow guest access, and write access.  This worked!

I the shared the /home directory on the revos harddrive using exactly the same method.  This worked.  However I was no longer able to access the External drives.

The UID has remained the same.

I then tried unsharing /home, still no joy.

Tried resharing /home  Home now works, but still the externals don't.


Can anyone shed any light on this situation.


Regards
Paul

---

### Post by lrgmmc on 2010-12-06
could you post your smb.conf file.
in terminal ```
cat /etc/samba/smb.conf
```

---

### Post by Joebewan on 2010-12-06
Did you share the folders using Samba configuration or some other way ??

---

### Post by paulttt on 2010-12-06
Didn't edit smb.conf directly, used nautilus for the shares.  Right clicked the drive/home directory and chose sharing.

Will post smb/conf in a sec :)

---

### Post by paulttt on 2010-12-06
```
aul@paul-desktop:~$ cat /etc/samba/smb.cont
cat: /etc/samba/smb.cont: No such file or directory
paul@paul-desktop:~$ cat /etc/samba/smb.conf
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



[disk1]
	writeable = yes
	public = yes
	path = /media/08F407B85A303A90
        guest ok = yes

[disk2]
	writeable = yes
	public = yes
	path = /media/FreeAgent Drive
        guest ok = yes

```

---

### Post by lrgmmc on 2010-12-06
are you wanting passwords or just guest?

---

### Post by paulttt on 2010-12-06
Hmmm, just checked the xp machine, and looked for the shares.  It does say they are present, but wont list the directories :(

---

### Post by paulttt on 2010-12-06
> **lrgmmc said:**
> are you wanting passwords or just guest?

Just guest, my network is secure, and the only stuff on there are video files.  Would like to have full write access though.

Also just to add, I did have a play with webmin, after everything went **** up. Dont know if that will effect the outcome.

---

### Post by lrgmmc on 2010-12-06
ok open smb.conf
```
sudo gedit /etc/samba/smb.conf
```
 
replace 
```
#   security = user
 
with
 
   security = share
 

```
 
then 
```
[disk1]
    writeable = yes
    public = yes
    path = /media/08F407B85A303A90
        guest ok = yes
 
[disk2]
    writeable = yes
    public = yes
    path = /media/FreeAgent Drive
        guest ok = yes
```
 
to 
 
```
[disk1]
    writeable = yes
    public = yes
    path = /media/08F407B85A303A90
    guest ok = yes
    browseable = yes
 
[disk2]
    writeable = yes
    public = yes
    path = /media/FreeAgent Drive
    guest ok = yes
    browseable = yes
```
then
```
sudo /etc/init.d/samba restart
```
should get you going

---

### Post by paulttt on 2010-12-06
Another quick update.  Just tried accessig the shares with an ubuntu laptop 10.04 again, and the same problem persists.  Can list the /home share, but not the 2 externals.

---

### Post by lrgmmc on 2010-12-06
try my changes should make the browseble

---

### Post by paulttt on 2010-12-06
> **lrgmmc said:**
> ok open smb.conf
```
sudo gedit /etc/samba/smb.conf
```
 
replace 
```
#   security = user
 
with
 
   security = share
 

```
 
then 
```
[disk1]
    writeable = yes
    public = yes
    path = /media/08F407B85A303A90
        guest ok = yes
 
[disk2]
    writeable = yes
    public = yes
    path = /media/FreeAgent Drive
        guest ok = yes
```
 
to 
 
```
[disk1]
    writeable = yes
    public = yes
    path = /media/08F407B85A303A90
    guest ok = yes
    browseable = yes
 
[disk2]
    writeable = yes
    public = yes
    path = /media/FreeAgent Drive
    guest ok = yes
    browseable = yes
```
then
```
sudo /etc/init.d/samba restart
```
should get you going

Have made the necissary alterations. But get this..
"/etc/init.d/samba: command not found"

after executing..
"sudo /etc/init.d/samba restart"

---

### Post by lrgmmc on 2010-12-06
ok i am on a windows machine. ```
sudo /etc/init.d/smbd restart
```

---

### Post by paulttt on 2010-12-06
I had to use this command instead..

"service smbd restat"

It has restarted, but now cant even see the machine lol.

---

### Post by paulttt on 2010-12-06
Machine has now reappeared hoever still got the same problem :(  Thanks for trying though.

---

### Post by paulttt on 2010-12-06
[disk1]
    writeable = yes
    public = yes
    path = /media/08F407B85A303A90
    guest ok = yes
    browseable = yes
**    force user - paul**
[disk2]
    writeable = yes
    public = yes
    path = /media/FreeAgent Drive
    guest ok = yes
    browseable = yes
**    force user - paul**

Has done the trick, should have mentioned the drives are NTFS :oops:

Thanks for all your help :)

---


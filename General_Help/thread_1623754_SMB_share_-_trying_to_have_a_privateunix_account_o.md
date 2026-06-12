---
title: "SMB share - trying to have a private/unix account only access share to access from W7"
date: 2010-11-17
forum: General Help
---

### Post by Francisco on 2010-11-17
Maverick 10.10

Hi guys

I am trying to get my unix user to be the only one with privileges to read-write-do-anything to a shared folder in my ubuntu.

I need to be able to access the shares from my Windows 7 laptop and workstaion. I have tried some tutorials here and there. 

smbpasswd -e myuser won't work because we don't use smbpasswd database. 

> [2010/11/16 22:12:16.442386,  2] smbd/service.c:587(create_connection_server_info)
  guest user (from session setup) not permitted to access this share (public)
[2010/11/16 22:12:16.442410,  1] smbd/service.c:678(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/11/16 22:12:16.442435,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/reply.c(776) cmd=117 (SMBtconX) NT_STATUS_ACCESS_DENIED
[2010/11/16 22:13:05.342838,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:14:05.343706,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:14:05.343781,  3] smbd/process.c:2081(check_reload)
  Printcap cache time expired.
[2010/11/16 22:14:05.343812,  3] printing/pcap.c:136(pcap_cache_reload)
  reloading printcap cache
[2010/11/16 22:14:05.346848,  2] printing/print_cups.c:550(cups_async_callback)
  cups_async_callback: failed to read a new printer list
[2010/11/16 22:14:05.346893,  3] printing/pcap.c:243(pcap_cache_reload)
  reload status: error
[2010/11/16 22:14:05.346931,  3] printing/pcap.c:136(pcap_cache_reload)
  reloading printcap cache
[2010/11/16 22:14:05.349595,  2] printing/print_cups.c:550(cups_async_callback)
  cups_async_callback: failed to read a new printer list
[2010/11/16 22:14:05.349644,  3] printing/pcap.c:243(pcap_cache_reload)
  reload status: error
[2010/11/16 22:15:05.399551,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:16:05.399593,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:17:05.451289,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:18:05.510241,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:19:05.570283,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:20:05.576666,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:21:05.576804,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:22:05.629711,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/16 22:23:05.688020,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0


> root@Gserver:~# cat /etc/samba/smb.conf 
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
log level = 3
;usershare owner only = false
## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOME

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
   guest account = nobody

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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[public]
        comment = Public Share
        path = /home/giovanni/Desktop/shh
        read only = no
        browseable = no
        guest ok = no
        admin users = giovanni
root@Gserver:~# ls -la /home/giovanni/Desktop/shh/
total 715760
drwxrwxrwx 2 giovanni giovanni      4096 2010-11-16 21:44 .
drwxr-xr-x 3 giovanni giovanni      4096 2010-11-16 20:37 ..
-rwxr--r-- 1 nobody   nogroup  732923904 2010-07-03 21:36 l-allaboutsteve.avi
root@Gserver:~# p
Display all 175 possibilities? (y or n)
root@Gserver:~# 
Display all 2224 possibilities? (y or n)
root@Gserver:~# pdbedit -Lv giovanni
Unix username:        giovanni
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-4185131855-2558899455-481689380-3000
Primary Group SID:    S-1-5-21-4185131855-2558899455-481689380-513
Full Name:            
Home Directory:       \\gserver\giovanni
HomeDir Drive:        
Logon Script:         
Profile Path:         \\gserver\giovanni\profile
Domain:               GSERVER
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          9223372036854775807 seconds since the Epoch
Kickoff time:         9223372036854775807 seconds since the Epoch
Password last set:    Tue, 16 Nov 2010 22:26:20 PST
Password can change:  Tue, 16 Nov 2010 22:26:20 PST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF


Thanks in advance. BTW don't know if it makes a difference but windows tries to submit my user/pw combination using WINDOWS7-name\user should GSERVER\giovanni be used or just giovanni should work? -- tried and neither worked...

---

### Post by luvshines on 2010-11-17
When you are connecting through Windows, you will use glovani only.
I think, using win-name\glovani is making Samba treat that user as guest and since you have 'guest ok' = no, it is denying access
```

[2010/11/16 22:12:16.442386, 2] smbd/service.c:587(create_connection_server_info)
guest user (from session setup) not permitted to access this share (public)
```

Also, in the [public] section, you may want to change the following```

browseable = yes
# admin users = glovani
valid users = glovani

```

---

### Post by Francisco on 2010-11-18
> **luvshines said:**
> When you are connecting through Windows, you will use glovani only.
I think, using win-name\glovani is making Samba treat that user as guest and since you have 'guest ok' = no, it is denying access
```

[2010/11/16 22:12:16.442386, 2] smbd/service.c:587(create_connection_server_info)
guest user (from session setup) not permitted to access this share (public)
```




I tried using Giovanni only. See screenshot below.

I have tried:

localhost/giovanni
gserver/giovanni (hostname of server)
(blank)/giovanni

Any ideas

---

### Post by Grant Walters on 2010-11-18
Off the top of my head I think you still need to have an smbpasswd file unless you are going to do all validation against an existing windows server.  the pam password sync takes care of the rest.
You definitely want "valid users" to limit the share to your own user account.

---

### Post by luvshines on 2010-11-18
> **Francisco said:**
> I tried using Giovanni only. See screenshot below.

I have tried:

localhost/giovanni
gserver/giovanni (hostname of server)
(blank)/giovanni

Any ideas

Can you connect to the share from the Ubuntu server itself with that specified user```

smbclient //<server-ip>/<share-name> -U<username>%<passwd>
```

---

### Post by zaphod777 on 2010-11-18
> **Francisco said:**
> 

I have tried:

localhost/giovanni
gserver/giovanni (hostname of server)
(blank)/giovanni

Any ideas

try using "workgroup\giovanni" notice I used "\" not "/".

---

### Post by Francisco on 2010-11-18
> **luvshines said:**
> Can you connect to the share from the Ubuntu server itself with that specified user```

smbclient //<server-ip>/<share-name> -U<username>%<passwd>
```

No

root@Gserver:~# smbclient //Gserver/please -ugiovanni%password
Enter root's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
root@Gserver:~#

---

### Post by Francisco on 2010-11-18
> **Grant Walters said:**
> Off the top of my head I think you still need to have an smbpasswd file unless you are going to do all validation against an existing windows server.  the pam password sync takes care of the rest.
You definitely want "valid users" to limit the share to your own user account.

I have added that


[please]
        username = giovanni
        valid users = giovanni     
        read only = no           
        writeable = yes
        path = /gio/music  


also after [global]

smb passwd file = /etc/samba/smbpasswd
        log level = 7
;usershare owner only = false
                              [ Wrote 361 lines ]

root@Gserver:~# service smbd restart
smbd start/running, process 2054
root@Gserver:~# smbclient //Gserver/please/  -U giovanni
Enter giovanni's password: 
Domain=[HOME] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_ACCESS_DENIED
root@Gserver:~# smbpasswd giovanni
New SMB password:
Retype new SMB password:
root@Gserver:~# smbclient //Gserver/please/  -U giovanni
Enter giovanni's password: 
Domain=[HOME] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_ACCESS_DENIED
root@Gserver:~#


root@Gserver:~# smbpasswd -a giovanni
New SMB password:
Retype new SMB password:
root@Gserver:~# smbpasswd -e giovanni
Enabled user giovanni.
root@Gserver:~# cat /etc/samba/smbpasswd 
root@Gserver:~#


/etc/samba/smbpasswd  permissions are 777

root@Gserver:~# ls -la /etc/samba/smbpasswd 
-rwxrwxrwx 1 root root 0 2010-11-16 22:07 /etc/samba/smbpasswd
root@Gserver:~# 


Yet smbpasswd file is blank.

---

### Post by capscrew on 2010-11-18
> **Francisco said:**
> I have added that


[please]
        username = giovanni
        valid users = giovanni     
        read only = no           
        writeable = yes
        path = /gio/music  


also after [global]

smb passwd file = /etc/samba/smbpasswd
        log level = 7
;usershare owner only = false
                              [ Wrote 361 lines ]

root@Gserver:~# service smbd restart
smbd start/running, process 2054
root@Gserver:~# smbclient //Gserver/please/  -U giovanni
Enter giovanni's password: 
Domain=[HOME] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_ACCESS_DENIED
root@Gserver:~# smbpasswd giovanni
New SMB password:
Retype new SMB password:
root@Gserver:~# smbclient //Gserver/please/  -U giovanni
Enter giovanni's password: 
Domain=[HOME] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_ACCESS_DENIED
root@Gserver:~#


root@Gserver:~# smbpasswd -a giovanni
New SMB password:
Retype new SMB password:
root@Gserver:~# smbpasswd -e giovanni
Enabled user giovanni.
root@Gserver:~# cat /etc/samba/smbpasswd 
root@Gserver:~#


/etc/samba/smbpasswd  permissions are 777

root@Gserver:~# ls -la /etc/samba/smbpasswd 
-rwxrwxrwx 1 root root 0 2010-11-16 22:07 /etc/samba/smbpasswd
root@Gserver:~# 


Yet smbpasswd file is blank.

That is not how you add a Samba user to smbpasswd database.

To add the user via the CLI try this```
smbpasswd -a <username>
```

The man pages are a good source of information.  You can see the HTML version [**_here_**]("http://manpages.ubuntu.com/manpages/maverick/en/man8/smbpasswd.8.html").

For Samba to authenticate users the user must be Ubuntu user and also a Samba user, even if you are using a Windows client to connect to the share.

---

### Post by asmoore82 on 2010-11-18
I would blow away all of the samba stuff you've done so far and install the "nautilus-share" package.
Then, you can simply right click a folder and share it over samba.

The first time you do this, it will detect that samba server is not installed/configured and
do it for you. It sets up samba to allow usershares and authenticate against your real UNIX account.

You can view all of your usershares at "/var/lib/samba/usershares".

---

### Post by luvshines on 2010-11-19
> **Francisco said:**
> No

root@Gserver:~# smbclient //Gserver/please -ugiovanni%password
Enter root's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
root@Gserver:~#

The command to be run is with capital U and not small one :)
```

-U<username>%<user-passwd>

```

---

### Post by Francisco on 2010-11-20
> **luvshines said:**
> The command to be run is with capital U and not small one :)
```

-U<username>%<user-passwd>

```

Thanks. It did not work. So I blew off smb.conf and copied /usr/share/samba/smb.conf (the original smb.conf)

I then used GUI from system-config-samba to re-add shares and change smbpasswd for users.

I am now able to authenticate. **But I am now unable to write to share. Help please.**

Here is the updated smb.conf - **I made sure I am able to write to /gio/music/ folder from gnome via file copy. Also chown and chmod 777**

> root@Gserver:~# cat /etc/samba/smb.conf 
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
debug level = 3

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
        workgroup = home

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
;       encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;       passdb backend = tdbsam

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
;       printing = cups
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
;       usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
        usershare allow guests = yes
        username map = /etc/samba/smbusers
        security = user
;       guest ok = no
;       guest account = nobody

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
;       guest ok = no
;       read only = yes
        create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
;       browseable = yes
;       read only = yes
;       guest ok = no
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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[shh]
        path = /home/giovanni/Desktop/shh
        writeable = yes
        browseable = no
        valid users = giovanni

[music]
        comment = Giovanni's music Library
        path = /gio/music
        writeable = yes
        read only = no
;       browseable = yes
        valid users = giovanni
        write lists = giovanni
        create mask = 0000
        directory mask = 0000
        force group = giovanni
root@Gserver:~# tail -f /var/log/samba/log.giovanni-pc
[2010/11/20 16:30:53.685123,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:16.334217,  3] smbd/process.c:1485(process_smb)
  Transaction 57 of length 53 (0 toread)
[2010/11/20 16:31:16.334266,  3] smbd/process.c:1294(switch_message)
  switch message SMBecho (pid 5945) conn 0x0
[2010/11/20 16:31:16.334283,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:16.334316,  3] smbd/reply.c:4959(reply_echo)
  echo 1 times
[2010/11/20 16:31:37.105638,  3] smbd/process.c:1485(process_smb)
  Transaction 58 of length 84 (0 toread)
[2010/11/20 16:31:37.105688,  3] smbd/process.c:1294(switch_message)
  switch message SMBtconX (pid 5945) conn 0x0
[2010/11/20 16:31:37.105718,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.105783,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.105814,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.105838,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.105880,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.105911,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.105935,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.105965,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106002,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106054,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106085,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106122,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106157,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106223,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106247,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106269,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106298,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2010/11/20 16:31:37.106321,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106347,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2010/11/20 16:31:37.106427,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106456,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106495,  3] smbd/service.c:807(make_connection_snum)
  Connect path is '/tmp' for service [IPC$]
[2010/11/20 16:31:37.106530,  3] smbd/vfs.c:97(vfs_init_default)
  Initialising default vfs hooks
[2010/11/20 16:31:37.106552,  3] smbd/vfs.c:122(vfs_init_custom)
  Initialising custom vfs hooks from [/[Default VFS]/]
[2010/11/20 16:31:37.106613,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106637,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106659,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106692,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106716,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106738,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106760,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106792,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106831,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106854,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106876,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106909,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.106955,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.106978,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/11/20 16:31:37.107000,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.107028,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2010/11/20 16:31:37.107051,  3] smbd/uid.c:429(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2010/11/20 16:31:37.107072,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2010/11/20 16:31:37.107138,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/11/20 16:31:37.107166,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.107196,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.107238,  3] smbd/service.c:1070(make_connection_snum)
  giovanni-pc (192.168.0.55) connect to service IPC$ initially as user giovanni (uid=1000, gid=1000) (pid 5945)
[2010/11/20 16:31:37.107268,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.107311,  3] smbd/reply.c:846(reply_tcon_and_X)
  tconX service=IPC$ 
[2010/11/20 16:31:37.107721,  3] smbd/process.c:1485(process_smb)
  Transaction 59 of length 104 (0 toread)
[2010/11/20 16:31:37.107747,  3] smbd/process.c:1294(switch_message)
  switch message SMBtrans2 (pid 5945) conn 0x7f303a1fde90
[2010/11/20 16:31:37.107771,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.107816,  3] smbd/msdfs.c:848(get_referred_path)
  get_referred_path: |music| in dfs path \Gserver\music is not a dfs root.
[2010/11/20 16:31:37.107842,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/trans2.c(8018) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
[2010/11/20 16:31:37.124715,  3] smbd/process.c:1485(process_smb)
  Transaction 60 of length 90 (0 toread)
[2010/11/20 16:31:37.124747,  3] smbd/process.c:1294(switch_message)
  switch message SMBntcreateX (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.124773,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.124817,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [.] [/gio/music]
[2010/11/20 16:31:37.124844,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: . reduced to /gio/music
[2010/11/20 16:31:37.124867,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [.] [/gio/music]
[2010/11/20 16:31:37.124891,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: . reduced to /gio/music
[2010/11/20 16:31:37.124918,  3] smbd/dosmode.c:166(unix_mode)
  unix_mode(.) returning 00
[2010/11/20 16:31:37.124941,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [.] [/gio/music]
[2010/11/20 16:31:37.124965,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: . reduced to /gio/music
[2010/11/20 16:31:37.125452,  3] smbd/process.c:1485(process_smb)
  Transaction 61 of length 76 (0 toread)
[2010/11/20 16:31:37.125479,  3] smbd/process.c:1294(switch_message)
  switch message SMBtrans2 (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.125504,  3] smbd/trans2.c:5012(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo: TRANSACT2_QFILEINFO: level = 1005
[2010/11/20 16:31:37.125534,  3] smbd/trans2.c:5225(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo . (fnum = 16818) level=1005 call=7 total_data=0
[2010/11/20 16:31:37.125753,  3] smbd/process.c:1485(process_smb)
  Transaction 62 of length 45 (0 toread)
[2010/11/20 16:31:37.125778,  3] smbd/process.c:1294(switch_message)
  switch message SMBclose (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.125801,  3] smbd/reply.c:4624(reply_close)
  close directory fnum=16818
[2010/11/20 16:31:37.126586,  3] smbd/process.c:1485(process_smb)
  Transaction 63 of length 40 (0 toread)
[2010/11/20 16:31:37.126611,  3] smbd/process.c:1294(switch_message)
  switch message SMBntcancel (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.126633,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.126666,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/nttrans.c(73) cmd=160 (SMBnttrans) NT_STATUS_CANCELLED
[2010/11/20 16:31:37.126700,  3] smbd/nttrans.c:1263(reply_ntcancel)
  reply_ntcancel: cancel called on mid = 34944.
[2010/11/20 16:31:37.126829,  3] smbd/process.c:1485(process_smb)
  Transaction 64 of length 45 (0 toread)
[2010/11/20 16:31:37.126853,  3] smbd/process.c:1294(switch_message)
  switch message SMBclose (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.126877,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (1000, 1000) - sec_ctx_stack_ndx = 0
[2010/11/20 16:31:37.126907,  3] smbd/reply.c:4624(reply_close)
  close directory fnum=16816
[2010/11/20 16:31:37.128439,  3] smbd/process.c:1485(process_smb)
  Transaction 65 of length 116 (0 toread)
[2010/11/20 16:31:37.128469,  3] smbd/process.c:1294(switch_message)
  switch message SMBntcreateX (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.128680,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.128758,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.128782,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.128813,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.128838,  3] smbd/dosmode.c:166(unix_mode)
  unix_mode(IMG_3897.JPG) returning 00
[2010/11/20 16:31:37.128861,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.128892,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.128915,  3] smbd/open.c:384(open_file)
  Permission denied opening IMG_3897.JPG
[2010/11/20 16:31:37.128939,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/error.c(160) cmd=162 (SMBntcreateX) NT_STATUS_ACCESS_DENIED
[2010/11/20 16:31:37.129424,  3] smbd/process.c:1485(process_smb)
  Transaction 66 of length 116 (0 toread)
[2010/11/20 16:31:37.129449,  3] smbd/process.c:1294(switch_message)
  switch message SMBntcreateX (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.129579,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.129640,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.129664,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.129694,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.129719,  3] smbd/dosmode.c:166(unix_mode)
  unix_mode(IMG_3897.JPG) returning 00
[2010/11/20 16:31:37.129742,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.129772,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.129795,  3] smbd/open.c:384(open_file)
  Permission denied opening IMG_3897.JPG
[2010/11/20 16:31:37.129818,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/error.c(160) cmd=162 (SMBntcreateX) NT_STATUS_ACCESS_DENIED
[2010/11/20 16:31:37.130284,  3] smbd/process.c:1485(process_smb)
  Transaction 67 of length 116 (0 toread)
[2010/11/20 16:31:37.130309,  3] smbd/process.c:1294(switch_message)
  switch message SMBntcreateX (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.130436,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.130496,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.130519,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.130549,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.130574,  3] smbd/dosmode.c:166(unix_mode)
  unix_mode(IMG_3897.JPG) returning 00
[2010/11/20 16:31:37.130597,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.130628,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.130650,  3] smbd/open.c:384(open_file)
  Permission denied opening IMG_3897.JPG
[2010/11/20 16:31:37.130674,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/error.c(160) cmd=162 (SMBntcreateX) NT_STATUS_ACCESS_DENIED
[2010/11/20 16:31:37.131103,  3] smbd/process.c:1485(process_smb)
  Transaction 68 of length 116 (0 toread)
[2010/11/20 16:31:37.131128,  3] smbd/process.c:1294(switch_message)
  switch message SMBntcreateX (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.131254,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.131321,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.131345,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.131375,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.131399,  3] smbd/dosmode.c:166(unix_mode)
  unix_mode(IMG_3897.JPG) returning 00
[2010/11/20 16:31:37.131422,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.131453,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.131475,  3] smbd/open.c:384(open_file)
  Permission denied opening IMG_3897.JPG
[2010/11/20 16:31:37.131498,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/error.c(160) cmd=162 (SMBntcreateX) NT_STATUS_ACCESS_DENIED
[2010/11/20 16:31:37.131922,  3] smbd/process.c:1485(process_smb)
  Transaction 69 of length 106 (0 toread)
[2010/11/20 16:31:37.131947,  3] smbd/process.c:1294(switch_message)
  switch message SMBtrans2 (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.131971,  3] smbd/trans2.c:5099(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
[2010/11/20 16:31:37.132094,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.132157,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.132182,  3] smbd/trans2.c:5208(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo: SMB_VFS_STAT of IMG_3897.JPG failed (No such file or directory)
[2010/11/20 16:31:37.132209,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/trans2.c(5210) cmd=50 (SMBtrans2) NT_STATUS_OBJECT_NAME_NOT_FOUND
[2010/11/20 16:31:37.132659,  3] smbd/process.c:1485(process_smb)
  Transaction 70 of length 106 (0 toread)
[2010/11/20 16:31:37.132684,  3] smbd/process.c:1294(switch_message)
  switch message SMBtrans2 (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.132708,  3] smbd/trans2.c:5099(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
[2010/11/20 16:31:37.132842,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.132904,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.132929,  3] smbd/trans2.c:5208(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo: SMB_VFS_STAT of IMG_3897.JPG failed (No such file or directory)
[2010/11/20 16:31:37.132949,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/trans2.c(5210) cmd=50 (SMBtrans2) NT_STATUS_OBJECT_NAME_NOT_FOUND
[2010/11/20 16:31:37.133397,  3] smbd/process.c:1485(process_smb)
  Transaction 71 of length 106 (0 toread)
[2010/11/20 16:31:37.133418,  3] smbd/process.c:1294(switch_message)
  switch message SMBtrans2 (pid 5945) conn 0x7f303a203be0
[2010/11/20 16:31:37.133437,  3] smbd/trans2.c:5099(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo: TRANSACT2_QPATHINFO: level = 1004
[2010/11/20 16:31:37.133566,  3] smbd/vfs.c:851(check_reduced_name)
  check_reduced_name [IMG_3897.JPG] [/gio/music]
[2010/11/20 16:31:37.133624,  3] smbd/vfs.c:1008(check_reduced_name)
  check_reduced_name: IMG_3897.JPG reduced to /gio/music/IMG_3897.JPG
[2010/11/20 16:31:37.133649,  3] smbd/trans2.c:5208(call_trans2qfilepathinfo)
  call_trans2qfilepathinfo: SMB_VFS_STAT of IMG_3897.JPG failed (No such file or directory)
[2010/11/20 16:31:37.133673,  3] smbd/error.c:80(error_packet_set)
  error packet at smbd/trans2.c(5210) cmd=50 (SMBtrans2) NT_STATUS_OBJECT_NAME_NOT_FOUND
^C
root@Gserver:~# ^C
root@Gserver:~# ls -la /gio/music/
total 715612
drwxrwxrwx 2 giovanni giovanni         3 2010-11-20 15:52 .
drwxrwxrwx 3 giovanni giovanni         4 2010-11-14 13:31 ..
-rwxrwxrwx 1 giovanni giovanni 732923904 2010-07-03 21:36 l-allaboutsteve.avi


I think I narrowed it down. I switched paths on "shh" share and music to see if it was a folder permission issue. Now the problem must be somewhere here:

[music]
;       comment = Giovanni's music Library
        path = /home/giovanni/Desktop/shh
        writeable = yes  
        read only = no 
        browseable = no
        valid users = giovanni
        write lists = giovanni
        create mask = 0644
        directory mask = 0755 


With simply path, writeable, browseable = no and valid users I can write to the share. Here's the catch. I want user giovanni to be the only one that can write make folders so thats why the above config is set.

---

### Post by Francisco on 2010-11-21
Issue resolved.

- SMB users/passwords are linked to system accounts.

- Windows 7 computer was browsing the smbtree un-authenticated. After running smbstatus and figuring it out, using the system password fixed the issues.

- Windows 7 computers need to be in the same workgroup for smb to work.

---


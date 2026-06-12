---
title: "New Samba Users Cant Access Shares"
date: 2012-03-15
forum: General Help
---

### Post by ShapeShiftme on 2012-03-15
Good Day All.

Im having a very interesting problem.
I have this problem currently on 3 samba servers. and i have no idea what is wrong.

The Setup:

I install samba and webmin onto an ubuntu 11.10 server setup.

Samba security = default
Server ip  192.168.20.200

I then use webmin to create the system users. in this example donovan and helen

Everything works great no problems at all

I have the following shares setup

Applications
Backups
Media
{and a few others}

I i can browse the shares from windows machines if i login via donovan or helen.
I can also smbclient -L gives me the following

```
smbclient -L //192.168.20.200
Enter donovan's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.11]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        data            Disk      
        6tb             Disk      
        media           Disk      
        Games           Disk      
        Personal        Disk      
        ATS             Disk      
        Applications    Disk      
        Backup          Disk      
        IPC$            IPC       IPC Service (atsoffice server (Samba, Ubuntu))
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.11]

        Server               Comment
        ---------            -------
        ATSOFFICE            atsoffice server (Samba, Ubuntu)
        HELENHOARE-PC        
        WEBSERWIN            

        Workgroup            Master
        ---------            -------
        WORKGROUP            WEBSERWIN
```

Now the problem comes in when i create a new user. I just added user morne via the following commands

```
sudo adduser morne
smbpasswd -a morne
```

I then added morne to see 2 of the shares, backups and applications. but he cant browse the server i get the following

```

smbclient -L //192.168.20.200 -U morne
Enter morne's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.11]
tree connect failed: NT_STATUS_ACCESS_DENIED
```

But what is strager if i i browse to \\192.168.20.200 from a xp machine my username and password does not work just keeps asking me for it again.

But if i browse to \\192.168.20.200\Backup In i put in morne user and password it works perfectly.
So it seems the new user cant list items (shares)

Here is my smb.conf

```

#======================= Global Settings =======================

[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    force group = donovan
    map to guest = bad user
    encrypt passwords = true
    winbind use default domain = no
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    wins support = true
    dns proxy = no
    writeable = yes
    server string = %h server (Samba, Ubuntu)
    path = /media/6tb
    unix password sync = yes
    workgroup = WORKGROUP
    debug level = 10
    force user = donovan
    os level = 20
    valid users = donovan,helen
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes
    max log size = 1000
    pam password change = yes

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

#client lanman auth = Yes
#lanman auth = Yes 

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
    guest account = donovan
    browseable = no
    writeable = no
    printable = yes
    path = /var/spool/samba
    create mask = 0700
    comment = All Printers
    valid users = 
    public = yes

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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[data]
    guest account = donovan
    force user = root
    valid users = 
    public = yes
    path = /data
    force group = root

[6tb]
    path = /media/6tb

[media]
    valid users = donovan,helen,muser1
    delete readonly = yes
    path = /media/6tb/Media

[Games]
    path = /media/6tb/Games

[Personal]
    path = /media/6tb/Personal

[ATS]
    path = /media/6tb/ATS

[Applications]
    guest account = donovan
    valid users = donovan,helen,morne
    path = /media/6tb/Applications

[Backup]
    guest account = donovan
    valid users = donovan,helen,morne
    path = /media/6tb/Backups

```

---

### Post by Morbius1 on 2012-03-15
You have in your [global] section the following line:
>      valid users = donovan,helenIf you put a share level parameter in the global section it will apply to all shares unless overridden in the share definition itself. When you run a "smbclient -L //192.168.20.200 -U morne" the global parameter is in control since you are connection at the host level and access is denied since morne is not one of the valid users.

By connecting to \\192.168.20.200\Backup directly, morne is on the valid users list so access is granted.
> [Backup] 
    guest account = donovan
[COLOR=Blue]valid users = donovan,helen,morne [/COLOR]
    path = /media/6tb/Backups

---


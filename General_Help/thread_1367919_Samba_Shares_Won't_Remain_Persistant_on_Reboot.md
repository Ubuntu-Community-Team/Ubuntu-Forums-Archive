---
title: "Samba Shares Won't Remain Persistant on Reboot"
date: 2009-12-30
forum: General Help
---

### Post by jamesisin on 2009-12-30
The issue has been clarified along the thread.  The real issue is a lack of communication, apparently, between Nautilus and Samba after a reboot.  The shares are shared but Nautilus is not displaying them as such.







I have four Samba shares over two storage drives.  Occasionally they will remain shared after a reboot, but the general pattern is that most or all of the shares will need to be shared over again when the drives are mounted after a reboot.  It seems to make no matter if I manually unmount the drives.

How can I force these shares to remain persistent?

This is driving me buggy, zoom zoom.

---

### Post by jamesisin on 2009-12-30
Anybody?

---

### Post by Morbius1 on 2009-12-30
Internal or external drives

Classic samba ( smb.conf ) or Nautilus-share ( right click - share in nautilus ).

You might want to post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**

---

### Post by jamesisin on 2009-12-30
I am creating the shares in the GUI (either right-click Sharing Options or right-click Properties --> Share).  I imagined that action translated into the smb.conf file, n'est-ce pas?

Thanks for the command suggestions.  I was able to deduce from their outputs that Samba is working correctly (after some small testing).  (And I removed some old deleted shares that were for deleted folders.)

Basically the four shares are represented in /var/lib/samba but Samba and Nautilus are not communicating this information.

I am able to connect to the shares on reboot from another system as expected.  However, the double-arrow share icon and all share information is absent via the context menu (right-click).

Sometimes this is not the case, but typically all four share will *appear* to be missing (under Nautilus).  Unmounting and remounting does not appear to have the same effect (but rather it remains persistent).

Any other suggestions?

---

### Post by Morbius1 on 2009-12-30
You're using nautilus-share not classic samba.

There is a bug in nautilus-share that will remove the little hand under the folder icon and remove the "write" check box on the context menu GUI. But that bug pertains only to folders that were created by the system and not to folders you create yourself.

For example it will happen to /home/morbius1/Documents but not one I created myself - /home/morbius1/TestShare for example.

In any event the bug is cosmetic and does not reflect the true status of the share. net usershare info is the only way to determine the true status of the share.

Without the output I requested there's no way for me to determine if this is the same bug.

---

### Post by jamesisin on 2009-12-30
Here is one of the four:

```
[ina]
path=/media/Tunage/InA
comment=
usershare_acl=Everyone:F,
guest_ok=n
```

And testparm:

```
$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
 server string = %h server (Samba, Ubuntu)
 map to guest = Bad User
 obey pam restrictions = Yes
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
 printable = Yes
 browseable = No
 browsable = No

[print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers
```

However, the problem you describe does not seem to apply here.  Or perhaps I have misunderstood.

Also, sorry I forgot to mention, the system in question in 9.10 (so no little hand; double-arrow).

---

### Post by louieb on 2009-12-30
To have samba shares automatically mount on startup - I use CIFS  heres the how to:    [Mount samba shares with utf8 encoding using cifs - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=288534&highlight=samba")

---

### Post by Morbius1 on 2009-12-30
It took louieb's post before I realized that I misinterpreted your post - maybe - I don't know - it's still not clear to me.

> Occasionally they will remain shared after a reboot, but the general pattern is that most or all of the shares will need to be shared over again when the drives are mounted after a reboot

> I am able to connect to the shares on reboot from another system as expected. However, the double-arrow share icon and all share information is absent via the context menu (right-click).


I'm lost here:

Are you talking about not being able to access the share from the client even though the share still exists?

Or are you talking about the directory you want to share on the server has to be "re-shared" because the share disappears?

---

### Post by jamesisin on 2009-12-30
Sorry if I obscured matters.  A close reading of the facts *should* show that I was initially under the impression that the shares were being unshared on reboot.  However, it was revealed (somewhere above) that the shares are still alive but merely Nautilus doesn't choose to either display the double-arrow share icon or include the share information in the right-click options.  I can re-add those in Nautilus but there seems little point since whether this aesthetic is fixed or not I am still able to connect to the share from outside as expected.

---

### Post by jamesisin on 2009-12-30
louieb - Isn't that post about mounting Samba shares client-side?  My issue is that they are not being displayed as though they were shared on the server-side (in Nautilus).

---

### Post by Morbius1 on 2009-12-30
> I can re-add those in Nautilus but there seems little point since whether this aesthetic is fixed or not[COLOR=Blue] I am still able to connect to the share from outside as expected[/COLOR].So there is no problem. You've discovered a bug in nautilus-share or possibly nautilus itself concerning how nautilus displays the share icon.

---

### Post by dmizer on 2009-12-30
If you are using Nautilus share, please indicate what directories you are sharing (full path).

If you are sharing mounted hard drives (external or internal), please post /etc/fstab

Also, please post your entire /etc/samba/smb.conf file.

---

### Post by jamesisin on 2009-12-30
> **dmizer said:**
> If you are using Nautilus share, please indicate what directories you are sharing (full path).

/media/Tunage/iTuna
/media/Tunage/InA
/media/Tonage/BB
/media/Tonage/Zoom

> If you are sharing mounted hard drives (external or internal), please post /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
#                
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b8c9f44c-af18-4bfc-919a-5941628aa25b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5e0c996c-676c-45a5-87ff-3f78eb157646 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

> Also, please post your entire /etc/samba/smb.conf file.

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
# parameters must be set (thanks to Ian Kahan  for
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
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
```

Have fun with that...

---

### Post by Morbius1 on 2009-12-30
> **jamesisin said:**
> Sorry if I obscured matters.  A close reading of the facts *should* show that I was initially under the impression that the shares were being unshared on reboot.  However, it was revealed (somewhere above) that the shares are still alive but merely Nautilus doesn't choose to either display the double-arrow share icon or include the share information in the right-click options. [COLOR=Blue] I can re-add those in Nautilus but there seems little point since whether this aesthetic is fixed or not I am still able to connect to the share from outside as expected[/COLOR].

**Once again, this is not a Samba issue**. You can connect to the share from the client. It's a cosmetic bug in how nautilus displays the share. I suggest you do the following 2 things:

(1) Report this bug or add it to this one: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480)

(2) Make believe you're using "Classic Samba" where the share definitions are in smb.conf. In classic samba there never was a share icon in Nautilus.

And on a personal note if anyone ever asks you to post the contents of smb.conf, open a terminal and type **testparm -s**.
My eyes can't take going through 300 lines of comments. :)

---

### Post by jamesisin on 2009-12-30
> **Morbius1 said:**
> **Once again, this is not a Samba issue**. You can connect to the share from the client. It's a cosmetic bug in how nautilus displays the share. I suggest you do the following 2 things:

(1) Report this bug or add it to this one: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480)

(2) Make believe you're using "Classic Samba" where the share definitions are in smb.conf. In classic samba there never was a share icon in Nautilus.

I mentioned all of that earlier.  I described it as a communication problem between Samba and Nautilus (who is at fault?  dunno) since it would seem that N should be aware that S is sharing something and display the correct icon (and include the S information in the right-click Properties).

I'll look into the bug unless dmizer can untangle the issue.

> And on a personal note if anyone ever asks you to post the contents of smb.conf, open a terminal and type **testparm -s**.
My eyes can't take going through 300 lines of comments. :)

I had already posted testparm's output.  Ask and ye shall receive.

---

### Post by louieb on 2009-12-30
> **jamesisin said:**
> louieb - Isn't that post about mounting Samba shares client-side?  My issue is that they are not being displayed as though they were shared on the server-side (in Nautilus).

Your right it is. I got confused and though you were trying to access data on a Windows machine. 

I'll lay back and see what Morbius1 and dmizer have to say.

---

### Post by dmizer on 2009-12-30
Your problem is that you don't have a permanent mount in /etc/fstab for your external drive. Once you add the drive to /etc/fstab, the indicators should work correctly.

PS. I don't like testparm because I can't see disabled options ;)

---

### Post by jamesisin on 2009-12-31
So basically my laziness has caused all of this.  My mother was right.  Damn it.

I'll create an entry in fstab and see if that doesn't take care of the matter.  I suppose I should prefer the UUID...

---

### Post by dmizer on 2009-12-31
> **jamesisin said:**
> I suppose I should prefer the UUID...

Indeed :P

---

### Post by jamesisin on 2010-01-02
That looks to have done it.  For those interested, I have included some additional information about fstab and UUID's in this post of mine about mounting drives:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

Thanks to all who worked on this one.

---

### Post by dmizer on 2010-01-02
> **jamesisin said:**
> That looks to have done it.  For those interested, I have included some additional information about fstab and UUID's in this post of mine about mounting drives:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

Thanks to all who worked on this one.

Good show! :)

---


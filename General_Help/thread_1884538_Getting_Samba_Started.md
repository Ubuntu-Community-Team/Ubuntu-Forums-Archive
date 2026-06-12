---
title: "Getting Samba Started?"
date: 2011-11-21
forum: General Help
---

### Post by mcman56 on 2011-11-21
I'm trying to get Samba started in 10.04 by following the instructions in this link:
[FONT=Arial][SIZE=2][COLOR=#0000cc][https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000cc][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#0000cc]When I try to edit [FONT=Courier New][COLOR=#000000]/etc/samba/smb.conf, it opens as read only.  How can I access for editing?[/COLOR][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by AmateurDev on 2011-11-21
You must be root to edit that file. You can do this by:
```
sudo gedit /etc/samba/smb.conf
```You'll need to type in your password. You can replace gedit with any text editor (i.e. mousepad, nano, etc).

---

### Post by MartyBuntu on 2011-11-21
> **AmateurDev said:**
> You must be root to edit that file. You can do this by:
```
sudo gedit /etc/samba/smb.conf
```You'll need to type in your password. You can replace gedit with any text editor (i.e. mousepad, nano, etc).


It would be preferred to use **gksudo** instead of **sudo** when using a graphical program.

---

### Post by mcman56 on 2011-11-21
Thanks, that all seemed to work.  However, I was expecting instant access to a windows system on my wireless network.  When I go to windows network, I get what is in the attachment.  I am new to this and have no idea how to proceed.

---

### Post by Morbius1 on 2011-11-22
**[1]** **Edit smb.conf as root:**
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```Save smb.conf, exit gedit, and back in the terminal restart some services:
```
sudo service smbd restart
``````
sudo service nmbd restart
```Wait a few minutes ( seriously, a few minutes ) and try to access the network again.

**[2] If that doesn't do it by itself please post the output of the following commands please:**
```
hostname
``````
testparm -sv | grep "netbios name"
```[COLOR=Blue]*The command above is rather complex so please just copy it from this post and paste it to your terminal. A missing quote or misplaced space will give us the wrong answer.*[/COLOR]
```
testparm -s
``````
smbtree
```

---

### Post by mcman56 on 2011-11-22
I get the same result.  I'm a raw beginner at this so may be missing something else quite obvious that needs to be done.  Thanks for your help with this.

us@us-laptop:~$ hostname
us-laptop
us@us-laptop:~$ 
-------------------------------------------------------------------------

us@us-laptop:~$ testparm -sv | grep "netbios name"
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
WARNING: Ignoring invalid value 'us' for parameter 'security'
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
    netbios name = US-LAPTOP
us@us-laptop:~$ 
---------------------------------------------------------------------------------------

us@us-laptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
WARNING: Ignoring invalid value 'us' for parameter 'security'
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
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
    name resolve order = bcast host lmhosts wins
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

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes
us@us-laptop:~$ 
---------------------------------------------------------------------------------

us@us-laptop:~$ smbtree
WARNING: Ignoring invalid value 'us' for parameter 'security'
Enter us's password: 
us@us-laptop:~$

---

### Post by Morbius1 on 2011-11-22
Sorry about the delay, had a real life medical emergency here.
[COLOR=Blue][B]
EDIT:[/B][/COLOR] Let's see if samba itself it working. Open a Terminal and type:
```
 nautilus smb://192.168.0.100
```
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the machine you are running.*[/COLOR]

You have a reoccurring error message:
>  WARNING: Ignoring invalid value 'us' for parameter 'security'Since it's ignoring that line you should be OK since it will default to USER but you might want to post the entire contents of your config file:
```
cat /etc/samba/smb.conf
```As for the output of smbtree that's not good. You should at least get an error message so my first guess is that a firewall is in the way. If you did anything to your firewall disable it. If you don't know if you did anything to your firewall then run this command to turn it off:
```
sudo ufw disable
```Then try smbtree

Just in case install the following utility:
```
sudo apt-get install nmap
```And post the output of the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Change 192.168.0.100 to the ip address of your machine.
You need to at least have these ports open:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm

---

### Post by mcman56 on 2011-11-22
Here goes:  
Should I be doing something on the windows side?

Thanks


________________________________________________________
Result of 
 nautilus smb://192.168.is in the attachment.

Clicking on share gets an empty folder.
Clicking on Print$ gets a repeating request for a password

________________________________________________________________________________

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
name resolve order = bcast host lmhosts wins

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
security = us

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
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
_______________________________________________________________________________

us@us-laptop:~$ smbtree
WARNING: Ignoring invalid value 'us' for parameter 'security'
Enter us's password: 
WORKGROUP
    \\US-LAPTOP              us-laptop server (Samba, Ubuntu)
        \\US-LAPTOP\IPC$               IPC Service (us-laptop server (Samba, Ubuntu))
        \\US-LAPTOP\share              Ubuntu File Server Share
        \\US-LAPTOP\print$             Printer Drivers
_________________________________________________________________________________

us@us-laptop:~$ sudo nmap -sS -sU -T4 192.168.1.222

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-11-22 20:09 PST
Interesting ports on 192.168.1.222:
Not shown: 1995 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.67 seconds

_______________________________________________________________________________

---

### Post by mcman56 on 2011-11-23
There is progress!!!!!!!  I can see the windows system by name in the Ubuntu system but can not access.  See attachment.

From the Windows system, I can see the Ubuntu system by name and can pull a file from the share folder.

I would like to be able to:

[LIST=1]
[*]Share most all files between systems
[*]From the Ubuntu system, print to a printer connected to the Windows system.
[/LIST]

Thanks

---

### Post by Morbius1 on 2011-11-23
OK, let's recap where we are now:

* Your hostname = us-laptop.
* Your "netbios-name" in the defaults = us-laptop.
* All of your samba ports are open.
* The output of smbtree shows that your Linux box is accessible by name and it's share is in fact accessible from Windows - don't worry about the Print$ share - there's nothing to see in there anyway.

** [] You still have this error however:**
>  WARNING: Ignoring invalid value 'us' for parameter 'security'Which is caused by this typo in your smb.conf:> 
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
[COLOR=Blue]**security = us**[/COLOR][COLOR=Blue][COLOR=Black] You can leave it alone and live with the  error message. It's not doing any harm as it's defaulting to USER  anyway. No need to fix something that ain't broke.

[/COLOR] [/COLOR]If you're obsessed with it just change the last line above to this> [COLOR=Blue]**security = user**[/COLOR][I]You could also have left it the way it was with a # sign in front of it. The HowTo you are following erroneously states that it must be uncommented because it's author doesn't realize that it's in the defaults or doesn't understand the relationship between smb.conf and the defaults - Sorry, that was more of a rant :).
[/I]
**[] So now we have one remaining problem:** > I can see the windows system by name in the Ubuntu system but can not access.What I would do first is run the nmap command again but this time with the ip address of the Windows system:
```
sudo nmap -sS -sU -T4 192.168.1.xxx
```[COLOR=Blue]*Change that to the ip address of the Windows system.*[/COLOR]

The same ports have to be open on Windows that you saw on Linux. So if anything is blocked, temporarily disable any firewall you have on Windows and see if you can connect to it's share.
[COLOR=Blue][B]
BTW[/B][/COLOR]: You did create a share on the Windows box, right?

---

### Post by mcman56 on 2011-11-23
I shared a folder on the windows box.  Is that the same thing as "creating a share"?



I disabled the firewall but get no connection.

us@us-laptop:~$ sudo nmap -sS -sU -T4 192.168.1.1
[sudo] password for us: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-11-23 07:42 PST
Warning: Giving up on port early because retransmission cap hit.

_______________________________________________________________

Thanks

---

### Post by Morbius1 on 2011-11-23
I think on the Linux side everything is working as it should. As far a Windows whatever expertise I have there ended with WinXP so the 3 questions I have are :

What version of Windows are you using?

What have you shared?

How did you share it ( WinXP had 2 methods - Simple and whatever they called the other one :) ) ?

---

### Post by mcman56 on 2011-11-23
It is Vista.

I shared a large folder and the printer.

A right click on the folder lead to properties where I could select share.  The shared folder has a different type of small icon now.

Thanks

---

### Post by Morbius1 on 2011-11-23
I'll have a look at how vista shares or at least how it's different from WinXP but that will not answer the original problem:
> us@us-laptop:~$ sudo nmap -sS -sU -T4 192.168.1.1
[sudo] password for us: 

Starting Nmap 5.00 ( [http://nmap.org]("http://nmap.org/") ) at 2011-11-23 07:42 PST
Warning: Giving up on port early because retransmission cap hit.
Something is in the way on your Vista box. If it's not a firewall then it's an anit-virus or some other barrier.

Are you sure that's the right ip address. Looks more like the ip address of a router to me.

What happens when you run:
```
nautilus smb://192.168.1.1
```

[COLOR=Blue]**EDIT: Just did a quick google search:**[/COLOR]
> **Definition: ****192.168.1.1** is an [IP address]("http://compnetworking.about.com/library/glossary/bldef-ipaddress.htm") normally used by Linksys [broadband routers]("http://compnetworking.about.com/cs/dslcablerouters/g/bldef_bbrouter.htm").  Some other brands of network routers also use this same address. While  technically a computer, printer or other device can be set up to use  this address instead of a router, that's uncommon.  

Run nmap against the ip address of the Vista machine.
[B]
[/B]

---

### Post by mcman56 on 2011-11-23
Thanks for looking at this

Does the windows box need a static IP?

You were right, I was using the router IP, but when I use the correct IP, I get what is below.  It seems that nothing happens until I hit enter then I get the "Warning:".  Each enter gets another "Warning"


us@us-laptop:~$ sudo nmap -sS -sU -T4 192.168.1.111
[sudo] password for us: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-11-23 14:22 PST
Warning: Giving up on port early because retransmission cap hit.
Stats: 0:02:01 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 53.45% done; ETC: 14:25 (0:00:56 remaining)
Warning: Giving up on port early because retransmission cap hit.
Stats: 0:02:09 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 54.27% done; ETC: 14:25 (0:01:01 remaining)
Stats: 0:02:29 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 57.69% done; ETC: 14:25 (0:01:07 remaining)
Stats: 0:02:35 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 58.11% done; ETC: 14:25 (0:01:11 remaining)

__________________________________________________________________________
 nautilus smb://192.168.1.111
This gets the shares screen print below
_____________________________________________________________________
clicking on a folder in shares screen gets the permissions screen print below

---

### Post by Morbius1 on 2011-11-23
You could give it a static ip address but from the looks of it it won't solve your problem entirely. 

The " you do not have permissions to view the contents of...." is an internal Windows permissions problem and best remedied in Windows. 

As for this:
>  Warning: Giving up on port early because retransmission cap hit.How many machines are on this network?

Try the command again please and just let it run - don't hit enter.

---

### Post by mcman56 on 2011-11-23
After about 10 minutes, I get this:

s@us-laptop:~$ sudo nmap -sS -sU -T4 192.168.1.116
[sudo] password for us: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-11-23 16:38 PST
Warning: Giving up on port early because retransmission cap hit..

_______________________________________________________________

Right now there are 3 machines on the network.

___________________________________________________________________

The odd thing is that I no longer see the Linux box from the windows box.  I have rebooted both.


_____________________________________________________________________________________

I tried to rerun some earlier commands and got:

us@us-laptop:~$  nautilus smb://192.168.1.222
us@us-laptop:~$ sudo service smbd restart
[sudo] password for us: 
smbd start/running, process 5038
us@us-laptop:~$ sudo service nmbd restart
restart: Unknown instance: 

The Unknown instance statement does not sound good.

---

### Post by mcman56 on 2011-11-23
I gave the visa system a static IP.  Communication/ file sharing is the same. I still can't see the linux box from windows.  (I don't understand how I could for a while.)  However, from the linux box I was able to load and print to the printer connected to the windows box.

---

### Post by Morbius1 on 2011-11-24
> us@us-laptop:~$ sudo service nmbd restart
restart: Unknown instance: 

The Unknown instance statement does not sound good.If you ever get that error message it means that nmbd has not started ( so there's nothing to restart ). When that happens you need to start it:
```
sudo service nmbd start
```Without nmbd running your linux box has no mechanism to broadcast it's name to the rest of the network.
[COLOR=Blue][B]
BTW[/B][/COLOR], On the Vista shares did you create them this way: [http://www.howtogeek.com/howto/windows-vista/how-to-share-a-folder-the-xp-way-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/how-to-share-a-folder-the-xp-way-in-windows-vista/)

---

### Post by Morbius1 on 2011-11-24
One more thing: Should you have to start nmbd manually one more time it's a bug that they claimed was fixed but .....  [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/596064](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/596064)

What I did back when I used 10.04 was this:

Create a script:
```
gksu gedit /etc/network/if-up.d/nmbd
```With this content:
```
#!/bin/sh
service nmbd start
```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/nmbd
```Any script placed in if-up.d will run only after the network is up.

---

### Post by mcman56 on 2011-11-24
I appreciate your patience.  This is strange.


[LIST=1]
[*]This morning I checked the system.   The router could see the Linux box IP but not its name.  Vista did not see the Linux box.  I could print from the Linux box to the printer connected to the Vista machine.
[*]I ran nmbd start.  The router saw the IP and name for Linux.  But Vista did not.  I continue to ge the same faults when trying to access the windows box from linux.
[*]A short time later, for reasons I don't understand, the windows box could see the Linux box by name and I could pull a file from the linux share directory.  I still anc not access the windows box from linux. Some folders state - unable to mount windows share.  Others state - do not have permissions.
[*]I did share per the link.
[*]Some screen prints are attached.
[/LIST]

---

### Post by Morbius1 on 2011-11-24
> A short time later, for reasons I don't understand, the windows box  could see the Linux box by name and I could pull a file from the linux  share directory.Anytime you restart and of the samba daemons or even when you first boot you need to wait minutes, some say as long as 15 minutes before the network resyncs itself.
> I did share per the link.And you went into the advanced settings and allowed everyone to have read/write access? 
>  Some folders state - unable to mount windows share.Others state - do not have permissions.If you were to get those error statements in reverse - when you try to access a Linux share from another machine - it would be because of a Linux file permissions problem and have nothing to do with Samba. You may have shared the folder but the file permissions themselves don't allow access to anyone other than the owner of the folder. Easy to fix on Linux - I don't know how you fix it on Vista.

---

### Post by mcman56 on 2011-11-24
You were correct.  I found some Vista help at:
[http://windows.microsoft.com/en-US/windows-vista/Demo-Sharing-files-and-folders-in-Windows-Vista](http://windows.microsoft.com/en-US/windows-vista/Demo-Sharing-files-and-folders-in-Windows-Vista)

Basically, the network type had to be changed to "private" in the Network and Sharing Center.  That certainly seems [FONT=&quot]counterintuitive[/FONT] 

It sounds like I do have to do something about nmbd.  With your instructions in "What I did back when I used 10.04 was this:", does this run automatically or do you need to trigger it in some way?

Thanks for all of your help with this.

---

### Post by Morbius1 on 2011-11-24
> It sounds like I do have to do something about nmbd.  With your  instructions in "What I did back when I used 10.04 was this:", does this  run automatically or do you need to trigger it in some way?
It runs automatically at every boot.

---


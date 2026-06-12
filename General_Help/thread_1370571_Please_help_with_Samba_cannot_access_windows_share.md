---
title: "Please help with Samba cannot access windows shared folders"
date: 2010-01-02
forum: General Help
---

### Post by RRFarFar on 2010-01-02
Hi guys,
I have spent so much time trying to get Samaba working, but with no luck
Here is my smb.conf

> 
[global]
realm =
netbios name = rlx-laptop
server string = %h server (Samba, Ubuntu)
workgroup = Juod
security = ads
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = yes
domain master = yes
preferred master = yes
domain logons = yes
os level = 80
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = yes
name resolve order = bcast host lmhosts wins
wins support = yes
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = no
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home/rlx/shared
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = no
printable = no
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =


I am using Karmic right now in Hardy Samba was working flawlessly.
By default in Karmic everybody have version 3.4.0. I have read numerous helps, tutorials and post tackling problems, and the result I have installed Samba 3.4.3 from lucid repository, because some people say that there is some kind of bug in version 3.4.0

I also have Gadmin now which is compatible with 3.4.3 and it shows me that samaba and winbind servers I running ok.

Please help.

What am I doing wrong?
I am so tired of this

THX

---

### Post by gordintoronto on 2010-01-02
You don't actually need Samba to access a Windows Share.

The workgroups are the same, and there's no firewall blocking access?

It might be helpful if you said, "I did such and such, and the result was xxx when I expected it to be yyy."

---

### Post by RRFarFar on 2010-01-02
> **gordintoronto said:**
> You don't actually need Samba to access a Windows Share.

The workgroups are the same, and there's no firewall blocking access?

It might be helpful if you said, "I did such and such, and the result was xxx when I expected it to be yyy."

Yes, workgroups are the same, in windows it is JUOD in ubuntu it is JUOD as well.

Sorry cant give the exact reference to what I did. Mostly I was experimenting when I had Samba 4.3.0. Right now Samba 3.4.3 uses its default setting after installation from Lucid repository.

I have GUFW which has tcp/udp 135, 137, 138, 139 and 445 open.

One thing I followed - [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149). I did all the fixes, I guess.

I would like to use Samba to share printers and folders. I didn't know that Ubuntu can access win folders without Samba.  

My Xp and Win7 laptops cannot see laptop Karmic laptop at all, and vice versa. When I changed my smb.conf numerous times, I have seen my iPod Touch once, but that is all I had been successful at.((((

Seriously, this very frustrating thing I have to deal with

---

### Post by RRFarFar on 2010-01-02
Any hint would be very much appreciated. I think I am just not aware of something. Ideas?

By the way sbmtree command does not give anything. Does thie mean anything?

---

### Post by Morbius1 on 2010-01-02
I'm going to regret getting involved in this one because that is the most complicated smb.conf I've ever seen outside of a textbook.
 
> My Xp and Win7 laptops cannot see laptop Karmic laptop at all, and vice versa.WinXP and Win7 aren't likely to see the Linux machine since you have no shares defined - at least not in smb.conf.
[COLOR=Blue]EDIT: you do have a share in smb.conf - sorry missed that.[/COLOR]

On the Ubuntu side run these commands and post the output please:

**net usershare info**
**sudo net usershare info**
**smbtree**
**findsmb**
**nmap -sT 192.168.0.100/22**
[I]Change 192.168.0.100 to the ip address of the Ubuntu machine

[/I]On the windows side run this command in [B]Command Prompt:

net view

[/B]None of these commands will fix anything but they should report errors if there are any.

---

### Post by RRFarFar on 2010-01-03
Thanks for the answer. You will not regret this, because I fixed this issue by going back to Hardy, which is LTS and in future I am going to stick with LTS only.
This conf was generated by GADMIN, which is awful by the way. Simply by running GADMIN one can corrupt his structure of smb.conf. I am not going to use GADMIN in future, simply because it adds a lot of things which I dont want to mess with.
My Hardy installation is just amazing, it has no issues at all.
Thanks for you reply once again)))))
Long live Ubuntu community

---

### Post by CharlesA on 2010-01-03
Man I am glad that my smb.conf is fairly clean (configured it with webmin). I've not heard of GADMIN, maybe try Webmin if you want a web-based config.

---

### Post by Silvertones on 2010-01-03
I got my network going perfectly without SAMBA. I'm so new  at this I don't even know what SAMBA is. I used the NETWORK MANAGER entered the same info as in Windows and done. Took about 2 minutes. Was actually easier then Windows. Right click on the folder to share set sharing properties. Done. Enabled the UFW through GUFW set two rules to allow the two networked computers IPs to open the ports and that's it.

---

### Post by RRFarFar on 2010-01-03
Sure, that is easy when there is no bugs. In samba 3.4.0 there is one - some people have reported it.
So it took a while till I found the decision. Actually I was able to get it working even in Karmic, but when next time I ran gadmin it spoilt everything again(((

---

### Post by sdowney717 on 2010-01-03
here is my working smb.conf file
what i did to make it work in karmic was to delete- purge all samba related programs using synaptic.
then reinstalled samba, file sharing nautilus, etc... and it is working.
this file just works for me with no logins needed.

> #
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
   encrypt passwords = no

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


---

### Post by Morbius1 on 2010-01-03
>  because I fixed this issue by going back to Hardy, which is LTS and in future I am going to stick with LTS only.I always though that in the stream of Ubuntu releases:

LTS LTS+1 LTS+2 LTS+3 newLTS

That except for the truly adventurous one only installed LTS and LTS+2.

Everything else was a beta, am I wrong? ;-)

---

### Post by CharlesA on 2010-01-04
> **Morbius1 said:**
> I always though that in the stream of Ubuntu releases:

LTS LTS+1 LTS+2 LTS+3 newLTS

That except for the truly adventurous one only installed LTS and LTS+2.

Everything else was a beta, am I wrong? ;-)

LTS are released every 2 years.

So it would be:
8.04 - LTS
8.10 - Regular
9.04 - Regular
9.10 - Regular
10.04 - LTS

---

### Post by Morbius1 on 2010-01-04
> **CharlesA said:**
> LTS are released every 2 years.

So it would be:
8.04 - LTS
8.10 - Regular
9.04 - Regular
9.10 - Regular
10.04 - LTS

Right, so what I'm saying is if you want a stable desktop OS and not something to play with as a hobby, you would install 8.04 and then 9.04. Everything else is beta level software.

I mean, how does Grub 1.97 Beta in 9.10 become Grub2 ?
Almost sounds like an Alpha :-D

---

### Post by RRFarFar on 2010-01-04
Yes, grub made me ask some questions as well. 
It was so unclear at one point I even thought I had both grub and grub2. Synaptic actually showed that I had both installed))) but it was smknd of error.
I dont like ALphas too

---


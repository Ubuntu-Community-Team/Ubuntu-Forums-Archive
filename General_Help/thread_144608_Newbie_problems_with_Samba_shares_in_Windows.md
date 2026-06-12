---
title: "Newbie problems with Samba shares in Windows"
date: 2006-03-14
forum: General Help
---

### Post by dwasifar on 2006-03-14
Very frustrated. 

I'm trying to share a folder on my Ubuntu box using Samba, and no matter what I do I can't get the Windows boxes on the network to connect to it.  I can see the Ubuntu box when I browse the network in XP, but I don't see the actual share; and when I try to connect to it I get this error from Windows: "The mapped network drive could not be created because the following error occurred: Configuration infomration could not be read from the domain controller, either because the machine is unavailable, or access has been denied."

As far as I know I've done everything right.  I set up a smb user/password.  What am I missing? 

Here's smb.conf:

# smb.conf

[global]

# netbios name
	netbios name = LinuxServer

# server string is the equivalent of the NT Description field
	server string = LinuxServer

# realm = Kerberos realm
	realm = LOCALDOMAIN

# workgroup = NT-Domain-Name or Workgroup-Name
	workgroup = Jerome

# Security mode.
	security = ADS

# Use password server option only with security = server
	password server = *

# Password encryption
	encrypt passwords = yes

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. 
;	hosts allow = 192.168.0.0/255.255.255.0 127.
        hosts allow = 127.0.0.1, 192.168.0.17
	hosts deny = 0.0.0.0/0.0.0.0

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
	guest account = nobody

# this tells Samba to use a separate log file for each machine
# that connects
;	log file = /var/log/samba/%m.log;   
	log file = /var/log/samba/samba.log

# The following are needed to allow password changing from Windows to
# update the Linux system password also.
# NOTE: Use these with 'encrypt passwords' and 'smb passwd file' above.
# NOTE2: You do NOT need these to allow workstations to change only
#        the encrypted SMB passwords. They allow the Unix password
#        to be kept in sync with the SMB password.
;	unix password sync = Yes
;	passwd program = /usr/bin/passwd %u
;	passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*

# Unix users can map to different SMB User names
	username map = /etc/samba/user.map

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;	include = /etc/samba/smb.conf.%m

# Most people will find that this option gives better performance.
# See speed.txt and the manual pages for details
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

# All NetBIOS names must be resolved to IP Addresses
# 'Name Resolve Order' allows the named resolution mechanism to be specified
# the default order is "host lmhosts wins bcast". "host" means use the unix
# system gethostbyname() function call that will use either /etc/hosts OR
# DNS or NIS depending on the settings of /etc/host.config, /etc/nsswitch.conf
# and the /etc/resolv.conf file. "host" therefore is system configuration
# dependant. This parameter is most often of use to prevent DNS lookups
# in order to resolve NetBIOS names to IP Addresses. Use with care!
# The example below excludes use of name resolution for machines that are NOT
# on the local network segment
# - OR - are not deliberately to be known via lmhosts or via WINS.
;	name resolve order = wins lmhosts bcast

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
 	wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#	Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;	wins server = 

# if you want to automatically load your printer list rather
# than setting them up individually then you'll need this
	printcap name = /etc/printcap
	load printers = yes

# It should not be necessary to spell out the print system type unless
# yours is non-standard. Currently supported print systems include:
# bsd, sysv, plp, lprng, aix, hpux, qnx
;	printing = lprng

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
	dns proxy = no 

# PAM-related
	obey pam restrictions = Yes
	pam password change = Yes

# Winbind separator
	winbind separator = /

# Winbind use default domain
# This parameter specifies whether the winbindd daemon should
# operate on users without domain component in their username. 
# Users without a domain component are treated as is part of 
# the winbindd server's own domain. While this does not benefit
# Windows users, it makes SSH, FTP and e-mail function in a way
# much closer to the way they would in a native unix system. 
# Default: winbind use default domain = no
   winbind use default domain = yes 

# RID to UID map
;	idmap backend = idmap_rid:Jerome=10000-60000

# RID idmap does not work with trusted domains
;	allow trusted domains = no

# Domain user id range
	idmap uid = 10000-60000

# Domain group id range
	idmap gid = 10000-60000

# Allow enumeration of domain users and groups
;	winbind enum users = no
;	winbind enum groups = no

# Allow nested groups
;	winbind nested groups = yes

# Winbind templates
# When filling out the user information for a Windows NT user, the
# winbindd(8) daemon uses this  parameter  to  fill  in  the  home
# directory  for that user. If the string %D is present it is sub-
# stituted with the user’s Windows NT domain name. If  the  string
# %U  is present it is substituted with the user’s Windows NT user
# name.
	template homedir = /home/%U

# This option defines the default primary group for each user cre-
# ated  by winbindd(8)’s local account management functions (simi-
# lar to the ’add user script’).   
;	template primary group = "Jerome/Domain Users"
;	template primary group = "Domain Users"

# When filling out the user information for a Windows NT user, the
# winbindd(8)  daemon  uses  this  parameter  to fill in the login
# shell for that user. 
	template shell = /bin/bash

# Services
	default service = homes
	preload = global homes printers

# Default share values
	valid users = @"Jerome/Domain Users"
	admin users = "Jerome/jon"
#==================

wins support = no
[homes]
	comment = Home Directory
	browseable = no
	writable = yes
	valid users = @"Jerome/Domain Users"
;	read only = No
;	create mask = 0664
;	directory mask = 0775

[users]
	path = /home
	comment = All Home Directories
	browseable = yes
	writable = yes
	valid users = @"Jerome/Domain Users"
	admin users = "Jerome/jon"
	read list = @"Jerome/Domain Users"
	write list = @"Jerome/Domain Users"

available = no
public = no
[data]
	path = /data
	comment = Data
	browseable = yes
	writable = yes
	valid users = @"Jerome/Domain Users"
	admin users = "Jerome/jon"
	read list = @"Jerome/Domain Users"
	write list = @"Jerome/Domain Users"

;[tmp]
;	comment = Temporary file space
;	path = /tmp
;	read only = no
;	public = yes

# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer
available = yes
public = yes
[printers]
	comment = All Printers
	path = /var/spool/samba
	browseable = no
	guest ok = no
	writable = no
	printable = yes
	;public = yes
	;to allow user 'guest account' to print

[MP3s]
path = /media/MP3s
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by dwasifar on 2006-03-14
.

---

### Post by dwasifar on 2006-03-14
Update: partial success.  

I kept fooling with it, and I replaced the smb.conf with the below, adapted from an example in the wiki.  Now the ubuntu box shows up in the Windows browse as a concatenation of most of the machine's name with the word LinuxServer, and I still can't browse it.  BUT, I can connect to it if I use the IP address instead of the name in the identifier:

//UBUNTU-LINUX-DESLinuxServer/MP3s - this does not work.
//192.168.0.25/MP3s  - this works.

I feel like Bullwinkle.  "Hey Rocky, watch me pull a rabbit out of my hat!  This time for sure!"  (ROARRRRRRR)  "Well, I'm getting close."

Here is the smb.conf.

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Jerome

# server string is the equivalent of the NT Description field
   server string = LinuxServer

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = Yes

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

# llbra Settings
;    revalidate = No
;    guest account = nobody
;    browse list = Yes
;    security = SHARE
;    interfaces = eth0, 192.168.0.0/255.255.255.0
;    wins server = Yes
;    wins support = Yes
;    guest ok = Yes
;    public = yes


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
;   passdb backend = tdbsam guest

;   obey pam restrictions = yes

;   guest account = nobody
;   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
;   passwd program = /usr/bin/passwd %u
;   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

;wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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



[mp3]
path = /media/MP3s
available = yes
browseable = yes
public = yes
writable = yes
create mask = 0777
hide dot files = No
dos filetime resolution = Yes
guest ok = yes
;revalidate = No
browse list = Yes

---

### Post by makoto149 on 2006-03-18
I'm not surprised you haven't received any replies. It seems on this forum only the simplest questions get answered.  You should see the bag of useless replies I got when I posted a question about wanting to plau a DVD.  This forum is useless.

---

### Post by ajmacca on 2006-03-18
Hey, I'm by no means an expert at this, and I'm new to the forum, but since no one else has tried to help, I will :p 

The first thing I noticed was that under the Authentication section, you have everything commented out, i.e. there's a ';' at the beginning of the line.  I'm not sure if it's critical, but my smb.conf has the "security = user" line uncommented.  This would require you to log on with the username and password of an actual Linux user when you wanted to connect to the samba shares.  The alternative would be having security=share and enabling the guest account so that anybody can access the share but I was always a little confused as to how this worked.

So if I were you, I'd uncomment the following:

[INDENT]security = user
guest account = nobody
invalid users = root (probably not necessary but seems standard)
[/INDENT]

I'm not sure what a few of your options do in your mp3 share, but if they don't work, you could try using "security = share" under authentication and "guest only = yes" (I think that option is right) under each share.

If all of this fails, you can also try installing webmin and the associated samba package.  You should be able to do this via synaptic if the right repositories are enabled.  This allows you to fill in the blanks so to speak, which generates a config file for you.

Hope this helps!

---

### Post by FredSambo on 2006-03-28
if that doesn't work for ya (which it probably will), try 

[Public]

path = home/public (make this directory)
read only = no

[Authentication]

security = shared

encrypt passwords = yes

---

### Post by Kosh42 on 2006-03-29
Just to cross refernece with this thread, where people are having similar problems (me included)...

[http://ubuntuforums.org/showthread.php?t=150003](http://ubuntuforums.org/showthread.php?t=150003)

---

### Post by DeusEx on 2006-03-29
I suggest you start over from scratch with your smb.conf file. It's full of junk. Even double declared some things.

Begin with googling for the samba project website, they have a nice tutorial for writing a config.

Where you discribed connecting to //x.y.z works, wheras //server doesn't, this is a wins problem. Make sure the box functions as a wins server, and is domain master. That is IF it's the only linux box on your windows network, DON'T add wins server = x.y.z here! Check the samba page for this too.

If you have a nice conf, test it with testparm.
then do a sudo /etc/init.d/samba restart.

check var/log/syslog if it doesn't work, maybe some usefull info is there.

My conf (slave machine):
```

[global]
   workgroup = WORKGROUP
   server string = DappereDraak 
   log file = /usr/local/samba/var/log.%m
   hosts allow = 10.10.10. EXCEPT 10.10.10.173
;  interfaces = 10.10.10.1/24
   security = share
   obey pam restrictions = Yes
   passdb backend = tdbsam, guest
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   encrypt passwords = true
   smb passwd file = /etc/samba/smbpasswd
   max log size = 1000
   os level = 40
   preferred master = no 
   domain master = no
   dns proxy = No
   wins support = no
   wins server = 10.10.10.1
   panic action = /usr/share/samba/panic-action %d
   invalid users = root
   load printers = no

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700
        browseable = No




[downloads]
comment = alle zooi
path = /mnt/stor/downloads
available = yes
guest ok = yes
browseable = yes
public = yes
writable = no

```

---


---
title: "Samba - Linux can see windows but not vice versa"
date: 2006-04-05
forum: General Help
---

### Post by renzokuken on 2006-04-05
i installed samba to my ubuntu box via apt-get and edited the smb.conf to share the folders i wanted to.

i then set up both my XP machines to be on the same "workgroup" as i specified in samba. 

thing is, ubuntu can see both the windwos comps and access their files, but neither of the XP machines can see my linux shared files.

ahve i done something wrong or just forgotten to do something?

i'll post my samba.conf as soon as i get home.

cheers

---

### Post by peibol on 2006-04-05
Do you have a firewall working? iptables maybe?

---

### Post by dengar on 2006-04-05
Quick thing also to check is that your windows xp computers don't have a firewall that is blocking your linux computer (I know I've had that problem with zone alarm before)

I'm not an expert, but when I was using a livecd (I admit it was knoppix, but its still debian so it should still be the same). They were pretty explicit that the samba client (which lets linux see windows shares) is seperate from the samba server (which smb.conf controls) although I suppose it would be neccesary for them to share the name of the server you are on.

What I did to get filesharing to work between Linux and WinXP was just change the server to MSHOME (you have probably already done this) then underneath the entry for [Home] (this is coming from some type of pre-existing smb.conf however) added:

[share2]
path = /your/path/here
browseable = yes

You can also add lines for discriptions and whatnot. I think you would do that with comment = (whatever text you want to appear as the name of the share)

Of course, I'm not big into security and this was pretty quick and dirty, so there might be holes or something I'm unaware of.

---

### Post by renzokuken on 2006-04-05
ok, i'm pretty sure its not the firewalls, so here is my samba conf file....

hat is iptables by the way?

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
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = FURLAND

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


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
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

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

wins support = no
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


[videos_one]
path = /media/storage/videos
available = yes
browseable = yes
public = yes
writable = no

[music]
path = /media/ntfs/Music
available = yes
browseable = yes
public = yes
writable = no

[VIDEOS_TWO]
path = /media/ntfs/Videos
available = yes
browseable = yes
public = yes
writable = yes

[music_new]
path = /home/rob/music
available = yes
browseable = yes
public = yes
writable = no

```

---

### Post by peibol on 2006-04-05
Ok, first of all, iptables is a linux firewall, can be used as a router, nat, etc. If you are not sure how is it configured you can use "firestarter" for gnome to edit basic rules "the easy way"

Second, you don't have a guest account for your samba server, this means you'll need to have a valid pam account to access any share in your linux pc, I'll post you my samba.conf next so you can see what the differences are.

```

# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors. 
#
#======================= Global Settings =====================================
[global]

# 1. Server Naming Options:
# workgroup = NT-Domain-Name or Workgroup-Name
   workgroup = KASBAH

# netbios name is the name you will see in "Network Neighbourhood",
# but defaults to your hostname
  netbios name = LOCAL_SERVER

# server string is the equivalent of the NT Description field
   server string = Samba Server %v

# Message command is run by samba when a "popup" message is sent to it.
# The example below is for use with LinPopUp:
; message command = /usr/bin/linpopup "%f" "%m" %s; rm %s

# 2. Printing Options:
# CHANGES TO ENABLE PRINTING ON ALL CUPS PRINTERS IN THE NETWORK
# if you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   printcap name = cups
   load printers = yes

# It should not be necessary to spell out the print system type unless
# yours is non-standard. Currently supported print systems include:
# bsd, sysv, plp, lprng, aix, hpux, qnx, cups
   printing = cups
   disable spoolss = Yes
   show add printer wizard = No

# Samba 3.x supports the Windows NT-style point-and-print feature. To
# use this, you need to be able to upload print drivers to the samba
# server. The printer admins (or root) may install drivers onto samba.
# Note that this feature uses the print$ share, so you will need to 
# enable it below.
# printer admin = @<group> <user>
;   printer admin = @adm
# This should work well for winbind:
;   printer admin = @"Domain Admins"

# 3. Logging Options:
# this tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba3/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 50

# Set the log (verbosity) level (0 <= log level <= 10)
; log level = 3

# 4. Security and Domain Membership Options:
# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page. Do not enable this if (tcp/ip) name resolution does
# not work for all the hosts in your network.
   hosts allow = 192.168.0. 127.

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
	guest account = smb-user
# Allow users to map to guest:
#  map to guest = smb-user

# Security mode. Most people will want user level security. See
# security_level.txt for details.
#   security = user
   security = share

# Use password server option only with security = server or security = domain
# When using security = domain, you should use password server = *
;   password server = <NT-Server-Name>
;   password server = *

# Password Level allows matching of _n_ characters of the password for
# all combinations of upper and lower case.
;  password level = 8
;  username level = 8

# You may wish to use password encryption. Please read
# ENCRYPTION.txt, Win95.txt and WinNT.txt in the Samba documentation.
# Do not enable this option unless you have read those documents
# Encrypted passwords are required for any use of samba in a Windows NT domain
# The smbpasswd file is only required by a server doing authentication, thus
# members of a domain do not need one.
  encrypt passwords = yes
  smb passwd file = /etc/samba/private/smbpasswd

# The following are needed to allow password changing from Windows to
# also update the Linux system password.
# NOTE: Use these with 'encrypt passwords' and 'smb passwd file' above.
# NOTE2: You do NOT need these to allow workstations to change only
#        the encrypted SMB passwords. They allow the Unix password
#        to be kept in sync with the SMB password.
;  unix password sync = Yes
# You either need to setup a passwd program and passwd chat, or
# enable pam password change
;  pam password change = yes
;  passwd program = /usr/bin/passwd %u
;  passwd chat = *New*UNIX*password* %n\n *Re*ype*new*UNIX*password* %n\n ;*passwd:*all*authentication*tokens*updated*successfully*

# Unix users can map to different SMB User names
;  username map = /etc/samba/smbusers

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /etc/samba/smb.conf.%m

# Options for using winbind. Winbind allows you to do all account and
# authentication from a Windows or samba domain controller, creating
# accounts on the fly, and maintaining a mapping of Windows RIDs to unix uid's 
# and gid's. idmap uid and idmap gid are the only required parameters.
#
# winbind separator is the character a user must use between their domain
# name and username, defaults to "\"
;  winbind separator = +
#
# winbind use default domain allows you to have winbind return usernames
# in the form user instead of DOMAIN+user for the domain listed in the
# workgroup parameter.
;  winbind use default domain = yes
#
# template homedir determines the home directory for winbind users, with 
# %D expanding to their domain name and %U expanding to their username:
;  template homedir = /home/%D/%U

# When using winbind, you may want to have samba create home directories
# on the fly for authenticated users. Ensure that /etc/pam.d/samba is
# using 'service=system-auth-winbind' in pam_stack modules, and then
# enable obedience of pam restrictions below:
;  obey pam restrictions = yes

#
# template shell determines the shell users authenticated by winbind get
;  template shell = /bin/bash

# 5. Browser Control and Networking Options:
# Most people will find that this option gives better performance.
# See speed.txt and the manual pages for details
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
#   interfaces = 192.168.0.1/24 192.168.13.2/24 
   interfaces = 192.168.0.1/24

# Configure remote browse list synchronisation here
#  request announcement to, or browse list sync from:
#       a specific host or from / to a whole subnet (see below)
;   remote browse sync = 192.168.3.25 192.168.5.255
# Cause this host to announce itself to local subnets here
;   remote announce = 192.168.1.255 192.168.2.44

# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
;   local master = no

# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
;   os level = 33

# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
;   domain master = yes 

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
;   preferred master = yes

# 6. Domain Control Options:
# Enable this if you want Samba to be a domain logon server for 
# Windows95 workstations or Primary Domain Controller for WinNT and Win2k
;   domain logons = yes

# if you enable domain logons then you may want a per-machine or
# per user logon script
# run a specific logon batch file per workstation (machine)
;   logon script = %m.bat
# run a specific logon batch file per username
;   logon script = %U.bat

# Where to store roaming profiles for WinNT and Win2k
#        %L substitutes for this servers netbios name, %U is username
#        You must uncomment the [Profiles] share below
;   logon path = \\%L\Profiles\%U

# Where to store roaming profiles for Win9x. Be careful with this as it also
# impacts where Win2k finds it's /HOME share
; logon home = \\%L\%U\.profile


# The add user script is used by a domain member to add local user accounts
# that have been authenticated by the domain controller, or when adding
# users via the Windows NT Tools (ie User Manager for Domains).

# Scripts for file (passwd, smbpasswd) backend:
; add user script = /usr/sbin/useradd -s /bin/false '%u'
; delete user script = /usr/sbin/userdel '%s'
; add user to group script = /usr/bin/gpasswd -a '%u' '%g'
; delete user from group script = /usr/bin/gpasswd -d '%u' '%g'
; set primary group script = /usr/sbin/usermod -g '%g' '%u'
; add group script = /usr/sbin/groupadd %g && getent group '%g'|awk -F: '{print $3}'
; delete group script = /usr/sbin/groupdel '%g'

# Scripts for LDAP backend (assumes nss_ldap is in use on the domain controller.
# Needs IDEALX scripts, and configuration in smbldap_conf.pm.
# This assumes you've installed the IDEALX scripts into /usr/share/samba/scripts...
; add user script = /usr/share/samba/scripts/smbldap-useradd.pl '%u'
; delete user script = /usr/share/samba/scripts/smbldap-userdel.pl '%u'
; add user to group script = /usr/share/samba/scripts/smbldap-groupmod.pl -m '%u' '%g'
; delete user from group script = /usr/share/samba/scripts/smbldap-groupmod.pl -x '%u' '%g'
; set primary group script = /usr/share/samba/scripts/smbldap-usermod.pl -g '%g' '%u'
; add group script = /usr/share/samba/scripts/smbldap-groupadd.pl '%g' && /usr/share/samba/scripts/smbldap-groupshow.pl %g|awk '/^gidNumber:/ {print $2}'
; delete group script = /usr/share/samba/scripts/smbldap-userdel.pl '%g'


# The add machine script is use by a samba server configured as a domain
# controller to add local machine accounts when adding machines to the domain.
# The script must work from the command line when replacing the macros,
# or the operation will fail. Check that groups exist if forcing a group.
# Script for domain controller for adding machines:
; add machine script = /usr/sbin/useradd -d /dev/null -g machines -c 'Machine Account' -s /bin/false -M '%u'
# Script for domain controller with LDAP backend for adding machines (You need
# the IDEALX scripts, and to configure the smbldap_conf.pm first):
; add machine script = /usr/share/samba/scripts/smbldap-useradd.pl -w -d /dev/null -g machines -c 'Machine Account' -s /bin/false '%u'

# Domain groups:
# Domain groups are now configured by using the 'net groupmap' tool

# Samba Password Database configuration:
# Samba now has runtime-configurable password database backends. Multiple
# passdb backends may be used, but users will only be added to the first one
# Default:
; passdb backend = smbpasswd guest
# TDB backen with fallback to smbpasswd and guest
; passdb backend = tdbsam smbpasswd guest
# LDAP with fallback to smbpasswd guest
# Enable SSL by using an ldaps url, or enable tls with 'ldap ssl' below.
; passdb backend = ldapsam:ldaps://ldap.mydomain.com smbpasswd guest
# Use the samba2 LDAP schema:
; passdb backend = ldapsam_compat:ldaps://ldap.mydomain.com smbpasswd guest

# idmap uid account range:
# This is a range of unix user-id's that samba will map non-unix RIDs to,
# such as when using Winbind
; idmap uid = 10000-20000
; idmap gid = 10000-20000
  
# LDAP configuration for Domain Controlling:
# The account (dn) that samba uses to access the LDAP server
# This account needs to have write access to the LDAP tree
# You will need to give samba the password for this dn, by 
# running 'smbpasswd -w mypassword'
; ldap admin dn = cn=root,dc=mydomain,dc=com
; ldap ssl = start_tls
# start_tls should run on 389, but samba defaults incorrectly to 636
; ldap port = 389
; ldap suffix = dc=mydomain,dc=com
; ldap server = ldap.mydomain.com
# Seperate suffixes are available for machines, users, groups, and idmap, if 
# ldap suffix appears first, it is appended to the specific suffix.
# Example for a unix-ish directory layout:
; ldap machine suffix = ou=Hosts
; ldap user suffix = ou=People
; ldap group suffix = ou=Group
; ldap idmap suffix = ou=Idmap
# Example for AD-ish layout:
; ldap machine suffix = cn=Computers
; ldap user suffix = cn=Users
; ldap group suffix = cn=Groups
; ldap idmap suffix = cn=Idmap


# 7. Name Resolution Options:
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
name resolve order = bcast lmhosts wins

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
;   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#       Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one  WINS Server on the network. The default is NO.
;   wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
   dns proxy = no 

# 8. File Naming Options:
# Case Preservation can be handy - system default is _no_
# NOTE: These can be set on a per share basis
;  preserve case = no
;  short preserve case = no
# Default case is normally upper case for all DOS files
;  default case = lower
# Be very careful with case sensitivity - it can break things!
case sensitive = no

# Enabling internationalization:
# you can match a Windows code page with a UNIX character set.
# Windows: 437 (US), 737 (GREEK), 850 (Latin1 - Western European),
# 852 (Czech), 861 (???), 932 (Japanese),
# 936 (Simplified Chin.), 949 (Korean Hangul),
# 950 (Trad. Chin.).
# More detail about code page is in
# "http://www.microsoft.com/globaldev/reference/oslocversion.mspx"
# UNIX: ISO8859-1 (Western European), ISO8859-2 (Eastern Eu.),
# ISO8859-5 (Russian Cyrillic), KOI8-R (Alt-Russ. Cyril.)
# This is an example for french users:
   dos charset = 850
   unix charset = ISO8859-15


#============================ Share Definitions ==============================
;[homes]
;   comment = Home Directories
;   browseable = no
;   writable = yes
# You can enable VFS recycle bin on a per share basis:
# Uncomment the next 2 lines (make sure you create a
# .recycle folder in the base of the share and ensure
# all users will have write access to it. See
# examples/VFS/recycle/REAME in the samba docs for details
;   vfs object = /usr/lib/samba/vfs/recycle.so

# Un-comment the following and create the netlogon directory for Domain Logons
; [netlogon]
;   comment = Network Logon Service
;   path = /var/lib/samba/netlogon
;   guest ok = yes
;   writable = no

# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;[Profiles]
;    path = /var/lib/samba/profiles
;    browseable = no
;    guest ok = yes
# This script can be enabled to create profile directories on the fly
# You may want to turn off guest acces if you enable this, as it
# hasn't been thoroughly tested.
;root preexec = PROFILE=/var/lib/samba/profiles/%u; if [ ! -e $PROFILE ]; ;                then mkdir -pm700 $PROFILE; chown %u:%g $PROFILE;fi

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
# to allow user 'guest account' to print.
   guest ok = yes
   writable = no
   printable = yes
   create mode = 0700
   printer = EpsonC42UX

wins support = no
[BigBoy]
	comment = Pelis, Descargas
	path = /BigBoy
	public = yes
	writable = yes
	available = yes
	browseable = yes
	guest ok = yes
	inherit permissions = yes
	force create mode = 0660
	force directory mode = 0770

[Dnl]
	comment = Recien Descargado
	path = /Dnl
	public = yes
	writable = yes
	available = yes
	browseable = yes
	guest ok = yes
	inherit permissions = yes
	force create mode = 0660
	force directory mode = 0770

[mp3]
	path = /mp3
	comment = muzica
	available = yes
	browseable = yes
	public = yes
	writable = yes
	inherit permissions = yes
	force create mode = 0660
	force directory mode = 0770

```

hope this helps ;)

---

### Post by renzokuken on 2006-04-05
thanks peibol, i'll have a peruse tomorrow and sort it out and let u know how it goes

---

### Post by dengar on 2006-04-05
I'm obviously out of my league but, whatever I'll say it anyways.

You have restarted the samba service after you changed your smb.conf settings right?

---

### Post by The Mekon on 2006-04-05
I had a similar problem when trying to see my Music files on my Ubuntu Box from my Windows Boxes.  This I tracked down to Permissions.

In Nautilus check the Permission of the files you wish to share and ensure that Others can read the files.

---

### Post by noswal on 2006-04-06
Problems I had was I could ping from ubuntu to xp but not the other way round, I installed firestarter and in there is a preference setting to allow pings.

Also, turned off firewall in windows while testing.

Static IP address in XP and Ubuntu in the same series like 192.168.1.xxx

And... turned it off and on again

---

### Post by peibol on 2006-04-06
As far as I understand, it's not a file permission issue but a share, cuz he sais wXP can't *see* smb shares, not that he gets an error while trying to copy some files from smb. 
Another thing he can try is to access your smb shares with nautilus from the same linux box that runs the smb server, maybe surfing to "smb://127.0.0.1" and then start troubleshooting from there.

---

### Post by renzokuken on 2006-04-06
still having no luck here......i just installed webmin to try and configure it that way but it is saying it has not detected an install of samba, on top of that, 

"sudo /etc/init.d/samba restart" complains about no such file 

this leads me to beleive that samba is not installed correctly, i did it via synaptic so was hoping someone might be able to tell me another way of installing it.

i also tried surfing to smb://127.0.0.1 and firefow that it cant load the page because no program is associated with the smb protocol.....

i have a feeling my synaptic is buggered, not the first time a program hasnt installed properly recently.......

yet how would i be able to see the winxp machines?

---

### Post by peibol on 2006-04-06
Samba is a server, you don't need it to surf windows shares, so it's logic that you can surf them.
When I said surf, dind't mean that you use Firefox (if i'm understanding right), use nautilus because it's capable of doing it.
And finally, try to exec samba without starting a daemon so you'll get all the errors in the standar output, and post them back here so we can take a look at it.

---

### Post by renzokuken on 2006-04-06
[QUOTE=peibol]Samba is a server, you don't need it to surf windows shares, so it's logic that you can surf them.
When I said surf, dind't mean that you use Firefox (if i'm understanding right), use nautilus because it's capable of doing it.
And finally, try to exec samba without starting a daemon so you'll get all the errors in the standar output, and post them back here so we can take a look at it.[/QUOTE]


so how do i type the smb://127.0.0.1 address into nautilus??

and what command executes samba? i typed samba in a terminal and it said no such command. 

seriously beginning to think my synaptic/apt-get is messed up.

considering installing dapper anyway so may do that and try again with fresh install, but would rather keep that as a last resort for now

---

### Post by peibol on 2006-04-06
> so how do i type the smb://127.0.0.1 address into nautilus??
open nautilus and press Ctrl+L (Location), or open gconf-editor and go to /apps/nautilus/preferences/ and check "start with location bar", close and restar nautilus (killall nautilus, this will kill all the nautilus processes, even the desktop icons :P, then Alt+F2 and run nautilus again).
> and what command executes samba? i typed samba in a terminal and it said no such command.
as root:
```

smbd -s /etc/samba/smb.conf -i

```
**-s** is for the config file and **-i** is for interactive mode, do **--help** to get extra parameters.
> seriously beginning to think my synaptic/apt-get is messed up.
Sorry cannot help you with that.

---

### Post by renzokuken on 2006-04-06
[QUOTE=peibol]open nautilus and press Ctrl+L (Location), or open gconf-editor and go to /apps/nautilus/preferences/ and check "start with location bar", close and restar nautilus (killall nautilus, this will kill all the nautilus processes, even the desktop icons :P, then Alt+F2 and run nautilus again).

as root:
```

smbd -s /etc/samba/smb.conf -i

```
**-s** is for the config file and **-i** is for interactive mode, do **--help** to get extra parameters.

Sorry cannot help you with that.[/QUOTE]


ok, so i tried the nautilus thing but nothing happened, got an error about unbale to display folder contents, so i started samba with the command u gave me and tried the nautilus thing again, and lo and behold, the folders i have configured to share in my smb.conf showed up....

im gonna go boot my xp machine and see if it works now

---

### Post by peibol on 2006-04-06
Niiiiiiiice.... so, the problem is when running the daemon with /etc/init.d .... well. It's an advance... :D

---

### Post by renzokuken on 2006-04-06
ok, so tried again with my XP machine but still no luck..........

and definately still no samba file in my /etc/init.d thingy.

wow, this is getting really frustrating.......this all worked automatically for me back when i used Xandros (dont worry, i'm never going back to that), i'll get it working in breezy if it kills me......with your help!!

>_<

---

### Post by Ramses de Norre on 2006-04-06
[http://ubuntuforums.org/showthread.php?t=150003&page=2&highlight=browse+windows]("http://ubuntuforums.org/showthread.php?t=150003&page=2&highlight=browse+windows")
Look at post #14.
(Watch the ';' in /etc/samba/smb.conf)

---

### Post by renzokuken on 2006-04-06
ok, think i'm getting closer, i tried to install a program called lilypond a month or s ago through synaptic, well something went wrong and i get an error everytime i finish a synaptic/apt-get command. i ignored it thinking it was harmless, but obviously it wasn't. i just found out how to sort it, installed lilypond properly, and did

sudo apt-get -f install

.....well turns out i had **90** items from synaptic that werent completely installed and this lilypond thing had been holding them up......just reinstalling samba properly now

i now have a samba in my init.d too......

hooray....gonna set it up again and see if it works this time

**EDIT**

ok, thanks to you both, and that thread u pointed out ramses, i can now see my ubuntu box when i go to "my Network Places" --> "Show Workgroup Computers" on my XP box. if i double click on it, i can enter my u/name and p/word and hey presto, my shared folders appear........however.......when i click on the shared folders, another box pops up asking for u/n and p/w and whatever i type in makes no difference i always get the same error message about not having permission.

heres is my current smb.conf

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
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = FURLAND

# server string is the equivalent of the NT Description field
   server string = %h homeserver (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


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
   security = user username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

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

;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

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

[ntfs]
  public=yes
  comment = Media
  path = /media/ntfs
  writeable=no
  valid users = system_username1 system_username2
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

[videonew]
  public=yes
  comment = Videos
  path = /media/storage/videos
  writeable=no
  valid users = system_username1 system_username2
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

```

i am so close i can smell it......what permissions do i need to change to access the folders from the xp box??

(and what do the two "mask" options do at the end of my smb.conf??)

also, i copied and pasted this from ramses post, was i supposed to literally put system_username1 in the valid users section, or was i suppose to replace that with the name i used when i did the smbpasswd thing??

---

### Post by peibol on 2006-04-06
well. the mask options are for file/folder creation, that specifies the octal mask that smb is going to apply to any file you write throght samba, that's surely another long story, nothing to worry right now.

I think that Ramses de Norre pointed a nice other thread that explains a lot about ubuntu's permission system, and take a look at the post #14

one thing i did to keep it more free was put a real user in the ```
guest account = nobody
``` line, to map the user so smb doesn't asks for my user name all the time.

---

### Post by renzokuken on 2006-04-07
thanks peibol, that sorted it.........

all up and running nicely now

thanks as well ramses

---

### Post by Zhukov on 2006-04-24
This worked for me as well:

Define the workgroup and add this to your samba conf:

############################# ADICIONADO A UNHA
interfaces = 192.168.0.0/255.255.255.0 127.0.0.1
bind interfaces only = Yes
netbios name = FANTASMAS
socket options = TCP_NODELAY IPTOS_LOWDELAY
local master = yes
os level = 65
domain master = yes


Note:
Set the ip range to suit yours, as well as the NETBIOS (use the same as the workgroup name)
The os level defines this machine as the "boss" because Windows machines can only go as high as 32.

---


---
title: "Need help setting up Samba"
date: 2009-07-29
forum: General Help
---

### Post by jon64 on 2009-07-29
I've set up samba once before and i was able to see my shares through my linux machines and my windows machines. This time i can see the shares but im not given access to the shares even though i've set up users.

```
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# For a step to step guide on installing, configuring and using samba,
# read the Samba-HOWTO-Collection. This may be obtained from:
#  http://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf
#
# Many working examples of smb.conf files can be found in the
# Samba-Guide which is generated daily and can be downloaded from:
#  http://www.samba.org/samba/docs/Samba-Guide.pdf
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors.
#
#---------------
# SELINUX NOTES:
#
# If you want to use the useradd/groupadd family of binaries please run:
# setsebool -P samba_domain_controller on
#
# If you want to share home directories via samba please run:
# setsebool -P samba_enable_home_dirs on
#
# If you create a new directory you want to share you should mark it as
# "samba-share_t" so that selinux will let you write into it.
# Make sure not to do that on system directories as they may already have
# been marked with othe SELinux labels.
#
# Use ls -ldZ /path to see which context a directory has
#
# Set labels only on directories you created!
# To set a label use the following: chcon -t samba_share_t /path
#
# If you need to share a system created directory you can use one of the
# following (read-only/read-write):
# setsebool -P samba_export_all_ro on
# or
# setsebool -P samba_export_all_rw on
#
# If you want to run scripts (preexec/root prexec/print command/...) please
# put them into the /var/lib/samba/scripts directory so that smbd will be
# allowed to run them.
# Make sure you COPY them and not MOVE them so that the right SELinux context
# is applied, to check all is ok use restorecon -R -v /var/lib/samba/scripts
#
#--------------
#
#======================= Global Settings =====================================

[global]

# ----------------------- Netwrok Related Options -------------------------
#
# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH
#
# server string is the equivalent of the NT Description field
#
# netbios name can be used to specify a server name not tied to the hostname
#
# Interfaces lets you configure Samba to use multiple interfaces
# If you have multiple network interfaces then you can list the ones
# you want to listen on (never omit localhost)
#
# Hosts Allow/Hosts Deny lets you restrict who can connect, and you can
# specifiy it as a per share option as well
#
	server string = My Media

;	netbios name = MYSERVER

;	interfaces = lo eth0 192.168.12.2/24 192.168.13.2/24
;	hosts allow = 127. 192.168.12. 192.168.13.

# --------------------------- Logging Options -----------------------------
#
# Log File let you specify where to put logs and how to split them up.
#
# Max Log Size let you specify the max size log files should reach

# logs split per machine
;	log file = /var/log/samba/%m.log
# max 50KB per log file, then rotate
;	max log size = 50

# ----------------------- Standalone Server Options ------------------------
#
# Scurity can be set to user, share(deprecated) or server(deprecated)
#
# Backend to store user information in. New installations should
# use either tdbsam or ldapsam. smbpasswd is available for backwards
# compatibility. tdbsam requires no further configuration.

	passdb backend = tdbsam


# ----------------------- Domain Members Options ------------------------
#
# Security must be set to domain or ads
#
# Use the realm option only with security = ads
# Specifies the Active Directory realm the host is part of
#
# Backend to store user information in. New installations should
# use either tdbsam or ldapsam. smbpasswd is available for backwards
# compatibility. tdbsam requires no further configuration.
#
# Use password server option only with security = server or if you can't
# use the DNS to locate Domain Controllers
# The argument list may include:
#   password server = My_PDC_Name [My_BDC_Name] [My_Next_BDC_Name]
# or to auto-locate the domain controller/s
#   password server = *


;	security = domain
;	passdb backend = tdbsam
;	realm = MY_REALM

;	password server = <NT-Server-Name>

# ----------------------- Domain Controller Options ------------------------
#
# Security must be set to user for domain controllers
#
# Backend to store user information in. New installations should
# use either tdbsam or ldapsam. smbpasswd is available for backwards
# compatibility. tdbsam requires no further configuration.
#
# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
#
# Domain Logons let Samba be a domain logon server for Windows workstations.
#
# Logon Scrpit let yuou specify a script to be run at login time on the client
# You need to provide it in a share called NETLOGON
#
# Logon Path let you specify where user profiles are stored (UNC path)
#
# Various scripts can be used on a domain controller or stand-alone
# machine to add or delete corresponding unix accounts
#
;	security = user
;	passdb backend = tdbsam

;	domain master = yes
;	domain logons = yes

# the login script name depends on the machine name
;	logon script = %m.bat
# the login script name depends on the unix user used
;	logon script = %u.bat
;	logon path = \\%L\Profiles\%u
# disables profiles support by specifing an empty path
;	logon path =

;	add user script = /usr/sbin/useradd "%u" -n -g users
;	add group script = /usr/sbin/groupadd "%g"
;	add machine script = /usr/sbin/useradd -n -c "Workstation (%u)" -M -d /nohome -s /bin/false "%u"
;	delete user script = /usr/sbin/userdel "%u"
;	delete user from group script = /usr/sbin/userdel "%u" "%g"
;	delete group script = /usr/sbin/groupdel "%g"


# ----------------------- Browser Control Options ----------------------------
#
# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
#
# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
#
# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
;	local master = no
;	os level = 33
;	preferred master = yes

#----------------------------- Name Resolution -------------------------------
# Windows Internet Name Serving Support Section:
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
#
# - WINS Support: Tells the NMBD component of Samba to enable it's WINS Server
#
# - WINS Server: Tells the NMBD components of Samba to be a WINS Client
#
# - WINS Proxy: Tells Samba to answer name resolution queries on
#   behalf of a non WINS capable client, for this to work there must be
#   at least one	WINS Server on the network. The default is NO.
#
# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups.

;	wins support = yes
;	wins server = w.x.y.z
;	wins proxy = yes

;	dns proxy = yes

# --------------------------- Printing Options -----------------------------
#
# Load Printers let you load automatically the list of printers rather
# than setting them up individually
#
# Cups Options let you pass the cups libs custom options, setting it to raw
# for example will let you use drivers on your Windows clients
#
# Printcap Name let you specify an alternative printcap file
#
# You can choose a non default printing system using the Printing option

	cups options = raw

;	printcap name = /etc/printcap
#obtain list of printers automatically on SystemV
;	printcap name = lpstat
;	printing = cups

# --------------------------- Filesystem Options ---------------------------
#
# The following options can be uncommented if the filesystem supports
# Extended Attributes and they are enabled (usually by the mount option
# user_xattr). Thess options will let the admin store the DOS attributes
# in an EA and make samba not mess with the permission bits.
#
# Note: these options can also be set just per share, setting them in global
# makes them the default for all shares

;	map archive = no
;	map hidden = no
;	map read only = no
;	map system = no
;	store dos attributes = yes


#============================ Share Definitions ==============================

	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	password server = None
	realm = None
	guest ok = yes
	guest account = jon64
	encrypt passwords = no
	username map = /etc/samba/smbusers
[homes]
	comment = Home Directories
	writeable = yes
;	valid users = %S
;	valid users = MYDOMAIN\%S

[printers]
	comment = All Printers
	path = /var/spool/samba
	browseable = no
	printable = yes

# Un-comment the following and create the netlogon directory for Domain Logons
;	[netlogon]
;	comment = Network Logon Service
;	path = /var/lib/samba/netlogon
;	guest ok = yes
;	writable = no
;	share modes = no


# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
;	[Profiles]
;	path = /var/lib/samba/profiles
;	browseable = no
;	guest ok = yes


# A publicly accessible directory, but read only, except for people in
# the "staff" group
;	[public]
;	comment = Public Stuff
;	path = /home/samba
;	public = yes
;	writable = yes
;	printable = no
;	write list = +staff

[Installs]
	path = /media
	valid users = jon64
	invalid users = None
	comment = My media
	guest ok = yes
```

---

### Post by jon64 on 2009-07-29
The problem im getting when trying to access the share from a windows machine is "\\localhost is not accessable. You might not have permission to use this network resource. Contact the adminitstrator of this server to find out if you have access permissions. You were not connected because a duplicate name exists on the network. Go to Systems in Control Panel to change computer name and try again" 

I dont understand why its trying to access \\localhost. It should be trying to connect to 192.168.0.104. And for the problem with duplicate computer names. There isn't any duplicate computer names in my network...

---

### Post by HappyFeet on 2009-07-29
Last time I tried to network linux and windows machines it worked perfect. But, one time I also had to go into /etc/samba/smb.conf and edit a couple things. Take your time and come back here if you still have trouble. I believe "workgroup" was one of the issues.

EDIT: If the "share" is from linux, windows won't see it. Bottom line.

---

### Post by jon64 on 2009-07-29
I've created shares on my ubuntu machine before and i was able to access it through my windows machine. But this time its being stubborn....

---

### Post by HappyFeet on 2009-07-29
> **jon64 said:**
> I've created shares on my ubuntu machine before and i was able to access it through my windows machine. But this time its being stubborn....

Sometimes it is just a matter of stepping back, and taking a deep breath. Sure, we all would like everything to work instantly, but in the real world, that does not happen. I suggest taking a break from it, and resuming at a later date. The answer is out there, it's just a matter of patience. Sorry I can't be more specific.

I have found an answer to every linux question I ever asked, it just took time. But once you know it, try to help someone else. We are all in this together.

---

### Post by t4thfavor on 2009-07-29
Im doing it right now, I will post my smb.conf, its very basic, but it should get you back to a working setup.


you also have to run the smbpasswd $username in order to set the samba password for each user.

---

### Post by jon64 on 2009-07-29
I tried copying your smb.conf but my shares still didnt work. I think im gonna walk away from this a bit and start over later. Thanks for trying guys, i appreciate it.

---

### Post by t4thfavor on 2009-07-29
You will have to modify the paths in the file, also make sure you set samba passwords for your users by doing

```

sudo smbpasswd username

```

without that it usually works from Linux, but never Windows.

Take a rest though, sometimes I get frustrated, and cannot get anything to work. Just take a few steps back, and everything will realign.

---

### Post by kelanafajar on 2009-08-13
Aku sudah mount directory di server ubuntu dengan samba. tetapi tidak dapat otomatis setiap nyala harus selalu di ulangi perintahnya. Supaya auto mount bagaimana?

---


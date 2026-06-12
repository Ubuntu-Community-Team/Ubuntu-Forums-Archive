---
title: "Windows doesn't see my SAMBA shares.."
date: 2006-06-02
forum: General Help
---

### Post by blackjack6.21.91 on 2006-06-02
That's basically it.  We're the same workgroup, I can use his printer, I can see his shares, but he just can't see me.  No errors appear or anything.  Does he need to install something or what?

-blackjack

---

### Post by blackjack6.21.91 on 2006-06-03
Anyone?  For real it's pretty important I set this network up..

---

### Post by souled on 2006-06-03
I think you have to configure the samba.conf file. Search around on the forum about configuring Samba; you're not the only one with this problem. Sorry I can't be of any more help.

---

### Post by blackjack6.21.91 on 2006-06-03
Believe me, I've looked around my fair share and have tried many, many, things..  I didn't want to resort to this b/c it sucks to be the guy who swims through so much text, but I'm going to print my smb.conf file here in hopes that someone is kind enough to look through it and offer their suggestions.  I have heard of smbpasswd setup but I'm not sure how to use it so that might be the problem,  but I dont want the other computer to have to use a password to get to my files.

I plan to have two shares set up, one that users can read from, and one they can write to, unless anyone knows a way to make just one that people can write files to but can't delete files from

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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = bloaner's shared documents (Ubuntu via SAMBA)

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
;   bind interfaces only = true



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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = flo
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

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
;   printer admin = @lpadmin


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

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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

wins support = no
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
[Bdocuments]
path = /home/bloaner/Desktop/docs
available = yes
browseable = yes
public = yes
writable = no
guest ok = yes
directory mask = 0775
create mask = 0775

[Bwritable]
path = /home/bloaner/Desktop/writeable
comment = Write all of your files to this folder
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes
directory mask = 0775
create mask = 0775

```

---

### Post by arnor on 2006-06-03
Hi,
try to ping your server from the windows machine, if ok then 
/etc/init.d/smb restart
;-)
[HTML]
[Bwritable]
path = /home/bloaner/Desktop/writeable
comment = Write all of your files to this folder
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes
directory mask = 0775
create mask = 0775
[/HTML]
i always add users = ( who you want to use it )
and also readable = yes
arnor

---

### Post by blackjack6.21.91 on 2006-06-03
$ /etc/init.d/smb restart
bash: /etc/init.d/smb: No such file or directory

Did you perhaps mean

sudo /etc/init.d/samba reload

Anyway I added the read only line, but i don't know the names of the users who should use it, and I don't know how to ping my computer.  But I can see his shares fine so I'm guessing that means there's an active connection.  Also though, this is a notebook and I tend to have alot of different users accessing my files to if there's anyway I could just let anyone on??

---

### Post by arnor on 2006-06-03
ups 
/etc/init.d/smb restart
was on mandriva...:???: 
ping -c  (how many pings) ( ip-adress )
for example : ping -c 3 127.0.0.1
is it ok now?
do you see your file?
you don't have to give the users then...but everyone can see and edit your shared files

---

### Post by blackjack6.21.91 on 2006-06-03
I don't see anything yet.  But how do I find the other computer's IP adress?  And I'm fine with there being no users.  It's not like I'm sharing my whole home directory..

---

### Post by arnor on 2006-06-03
on windows ...you will get your ip with
euh...(thinking)
=> ipconfig

---

### Post by givré on 2006-06-03
Hi guy,

It seams you follow one of my post to configure your smb.conf.
The thing is you shouldn't use me as a guest account, but your account ;)
replace it 
```
guest account = flo (my username is flo ;)

```
by yourself

---

### Post by blackjack6.21.91 on 2006-06-03
lol dude your right.. I just thought that was more advanced code that I didn't understand.  ROFL I'm glad your still on - I don't know how else I would've fixed that.

I ran the ping and the output was this

$ ping -c 3 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.

--- 192.168.1.100 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1998ms

I still don't see shares though, so i guess FLO wasn't the only problem

---

### Post by bullgr on 2006-06-03
see first of all if you network is setup correctly, for this you can get help from the internet or any experience person.

after you setup you network correctly and you can ping from a computer to another check if samba is installed and update
> sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install samba
sudo apt-get install smbfs
after that you have the latest samba server installed

next step, you must configure the smb.conf
> sudo gedit /etc/samba/smb.conf

delete all the crap, and copy-paste the following lines
> [global]
netbios name = server
server string = server
workgroup = Workgroup
security = share
log file = /var/log/samba.log
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
encrypt pass = yes
wins support = yes

[your_home_folder]
path = /home/your_home_folder
available = yes
browseable = yes
public = yes
writable = yes

[c]
path = /mnt/c
available = yes
browseable = yes
public = yes
writable = yes
note that you need to edit and write your mount-points and if you want a second disk, just copy-paste the "c" section and edit again your mount-points.
and also input your printer config.

finaly restart samba to take the changes efect
> /etc/init.d/samba restart

hope i help :D

---

### Post by blackjack6.21.91 on 2006-06-03
Well, I'm still in the same position (I see the Windows shares and the printer but the Windows doesn't see my shares), but my smb.conf looks a whole lot nicer.  I didn't put in any printer config and I can still use the printer connected to the Windows machine.  So here's what my sources.list now looks like

[global]
netbios name = server
server string = server
workgroup = Workgroup
security = share
log file = /var/log/samba.log
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
encrypt pass = yes
wins support = yes

[documents]
path = /home/bloaner/Desktop/docs
available = yes
browseable = yes
public = yes
writable = yes

[c]
path = /mnt/c
available = yes
browseable = yes
public = yes
writable = yes

Also I don't know what you mean by "mount point" or if I should add another one, so if it's necessary please explain.  I am not dual-booting on either machine

---

### Post by givré on 2006-06-03
[QUOTE=blackjack6.21.91]
Also I don't know what you mean by "mount point" or if I should add another one, so if it's necessary please explain.  I am not dual-booting on either machine[/QUOTE]
I think he speaks about sharing other directory or device, but you don't really need to play with config file until you have a good gui to do that in the administration menu, and sharing with a right click in a directory is quite easy

---

### Post by givré on 2006-06-03
I don't really know what is your problem. Your smb.conf seems to be fine, and you could see him.
Do the windows machine have a firwall or something like that? Do you have yourself a firewall.

---

### Post by givré on 2006-06-03
Sorry, double post ;)

---

### Post by bullgr on 2006-06-03
if you have a "c" drive for example and you want to share it thru the network, then you must mount it first.

to mount a disk you have to give a mount-point

in my example i make a "c" folder in "mnt" folder

> sudo mkdir /mnt/c
this makes the mount point and after that you edit the fstab file to auto-mount the disk on every boot.
> sudo gedit /etc/fstab
on the end of file or in any clean line type
> /dev/hda1       /mnt/c  vfat    iocharset=utf8,umask=000  0       0
note that in my example the disk is fat, when your disk is in another filesystem, then you must edit to the correct filesystem.

after that on any boot the "c" disk auto-mount to the mount-point /mnt/c.
this is the mount-point you need to input in smb.conf

---

### Post by denzilla on 2006-06-03
Having same problem only my ubuntu is a desktop, not a server. Can see windows printers and shares, but windows cannot see ubuntu samba shares. This is definitely one of the things that should be addressed in the update Mark Shuttleworth says is coming in a few weeks.

---

### Post by givré on 2006-06-03
It's could be a bug, but it's could be also a config problem : it's work fine with me in the both direction.
Sharing with windows has always been a problem (even between two windows machine). Sometimes you just have to unplug/plug your device, sometimes it is just a problem of firewall

---

### Post by arnor on 2006-06-03
Its your windows machine who is not well configured...because when you ping to  your server the windope can find it...
check the ip adress, do you use dhcp? or static ip? because when windows doesn't find a dhcp server, he get an ip adress who is only microsoft compatibles ( its very usefull for small home network , if you have 2 windopes they can easily make a network )
arnor

---

### Post by djsroknrol on 2006-06-03
A couple of things you might look at also....

Check /etc/nsswitch.conf...see if hosts line looks similar to this

```
hosts:          files dns wins
```

check System>Administration>Services and make sure that Samba is checked in there

---

### Post by blackjack6.21.91 on 2006-06-03
Wow!  Thanks for all the replies!

It worked!  All I did was remove the part about mnt/c from my config file and disabled trend micro on the other computer

(Edit: THANK YOU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!)

---


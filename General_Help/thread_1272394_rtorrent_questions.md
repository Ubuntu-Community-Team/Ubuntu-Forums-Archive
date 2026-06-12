---
title: "rtorrent questions"
date: 2009-09-22
forum: General Help
---

### Post by fcuk112 on 2009-09-22
i have 2 PCs, a torrent PC and a main PC.  the torrent PC is running rtorrent, watching a folder called "~/Torrents"; the downloaded files go to the same folder and this folder is shared across the network.

from my main PC i can see the "Torrents" folder, but when i try to save torrent files within Firefox it does not display any networked shares.  is this a samba configuration issue?

also, i would like to check the status of my torrents through ssh - how do i do this via my main PC?

many thanks.

---

### Post by badger_fruit on 2009-09-22
I see two issues

> **fcuk112 said:**
>  from my main PC i can see the "Torrents" folder, but when i try to save torrent files within Firefox it does not display any networked shares.  is this a samba configuration issue?

Yes, sounds like it is, please post your Samba SMB.CONF (/etc/samba/smb.conf) here.


> **fcuk112 said:**
>  also, i would like to check the status of my torrents through ssh - how do i do this via my main PC?

SSH?! Hmm, not sure, does the rTorrent have an API which will allow this?
Most come with a Web-GUI that you can use from another local PC (or with the right forwarding on your router/firewall, a remote PC - eg your office or public net cafe).

---

### Post by fcuk112 on 2009-09-22
it's just that i read somewhere i can check the status via ssh...  as for smb.conf:

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

```

---

### Post by nothingspecial on 2009-09-22
Install openssh-server and openssh-client and screen on both boxes.

```
sudo apt-get install openssh-server openssh-client screen
```

To ssh your other pc 
```

ssh username@ipadress
```

You can find your ip adress by right clicking on the network icon on your panel and choosing connection infomation.

Once you`ve shh ed in navigate to your ~/Torrents directory
```

cd ~/Torrents
```

In firefox right click on the torrent link and choose copy link location.

Back in your terminal (in your Torrents) directory type wget then hit Ctrl+Shift+V to paste the link location so it looks like
```

wget http://www.where_the_torrent_is.torrent
```

The torrent file will download into your Torrents directory.

Type ```
screen
```

launch rtorrent

```
rtorrent
```

When you`ve finished checking press Ctrl+A then D. This will detach your screen session but leave rtorrent running.

You can close your terminal if you want.

Next time you want to check ssh back into your pc and type ```
screen -r
```

This will reattach your screen session as if you`d never left.

If you configure ssh correctly and give your torrenting pc a fixed ip you can do this from any computer anywhere in the world.

Cool isn`t it?

---

### Post by badger_fruit on 2009-09-22
> **nothingspecial said:**
> Cool isn`t it?

YES! and something that will also help me get rid of one of my Windows PC which I was only holding onto as I couldn't find an adequate solution using linux.

---

### Post by fcuk112 on 2009-09-22
heh, thanks very much for your detailed explanation!

does this mean i need ssh to actually download the torrent file?  i thought i could just save it to a networked share from Firefox and have rtorrent pick it up from the torrent PC...

---

### Post by nothingspecial on 2009-09-22
No, you don`t have to, that`s just the way I do it.

Not having a windows machine I know nothing of samba, I just use ssh

---

### Post by fcuk112 on 2009-09-22
maybe samba was a red herring here - both machines are running jaunty.  so maybe it's related to NFS config?  sorry for being a noob.

i have rtorrent running in a console on my torrent PC.  ideally on my main PC i would like to connect to that instance of rtorrent to check the status.  is there any way to do this?  screen is pretty cool, but not quite what i was looking for i guess.  i would like to have both PCs running a console with the status showing...  is this possible?

either that or just running a command on my main PC to dump the status of my downloads (% complete, dl/ul rate) would be nice.

---

### Post by badger_fruit on 2009-09-22
No, you can create a share and tell firefox to download into it.
If you then tell rTorrent to download .torrent files from this folder, it will be done.

```

[global]
        printing = cups
        printcap name = cups
        cups options = raw
        map to guest = Bad User
        include = /etc/samba/dhcp.conf
        usershare allow guests = Yes
        netbios name = MYCOMPUTERNAME
        workgroup = MYWORKGROUP
        server string = "COMPUTER DESCRIPTION"
        name resolve order = bcast host lmhosts wins

[A_SHARE]
        comment = SHARE COMMENTS
        path = /path/to/share
        guest ok = yes
        read only = no
        force user = name_of_local_user

```

Edit according to your needs.

OK, so this goes into the /etc/samba/smb.conf on the rTorrent machine and restart samba .. *sudo service samba restart*
On your Windows (or any other PC) you can then browse to** //rtorrent_machine/a_share/**

---

### Post by fcuk112 on 2009-09-22
thanks, i added this:

```

[torrents]
   comment = Bazooka Torrents
   path = smb://bazooka/torrents
   browseable = yes
   read only = no
   guest ok = yes

```

but when i click "Save file" in Firefox i don't know how to navigate to the folder?

---

### Post by nothingspecial on 2009-09-22
> **fcuk112 said:**
>   screen is pretty cool, but not quite what i was looking for i guess.  i would like to have both PCs running a console with the status showing...  is this possible?




Screen is exactly what you are looking for. See [COLOR="Magenta"][here]("http://ubuntuforums.org/showthread.php?t=299286")[/COLOR]

---

### Post by fcuk112 on 2009-09-22
thanks, i tried your suggestion but when i try to connect from the main PC (or from another console on the torrent PC), i get 

```

Must run suid root for multiuser support.

```

even though i did chmod u+s /usr/bin/screen.  have you tested whether this works on jaunty?  someone also mentioned kibitz, would this be a better option?

---

### Post by lovinglinux on 2009-09-22
Install ssh server on the remote machine (the client is already installed by default)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Then mount your remote folder with sshfs

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Save your torrents in the remote folder from Firefox.

> **fcuk112 said:**
> i have rtorrent running in a console on my torrent PC.  ideally on my main PC i would like to connect to that instance of rtorrent to check the status.  is there any way to do this?  screen is pretty cool, but not quite what i was looking for i guess.  i would like to have both PCs running a console with the status showing...  is this possible?

either that or just running a command on my main PC to dump the status of my downloads (% complete, dl/ul rate) would be nice.

I never tried, but I bet Deluge can do that. With Deluge you can control your torrents via command-line, web ui or remote GTK. The last one means the client interface can connect to a remote server, so you are able to control Deluge as if it is running only on your machine, but actually connected to the remote daemon.

You need to install Deluge on both machines.

Check this thread [http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)

---

### Post by fcuk112 on 2009-09-22
great, thanks!  sshfs worked a treat, i can now drop torrents from Firefox into the Torrents folder and they are picked up by my torrent box.

would be cool if i could check the rtorrent status easily though - i'll need to take a look at wtorrent.

---

### Post by lovinglinux on 2009-09-22
> **fcuk112 said:**
> would be cool if i could check the rtorrent status easily though - i'll need to take a look at wtorrent.

Deluge is the best for remote connections. You can access your remote server using the regular interface on your local machine. Give it a try.

---

### Post by nothingspecial on 2009-09-22
> **fcuk112 said:**
> .

would be cool if i could check the rtorrent status easily though 

You can. I`ve already explained. You don`t need both computers displaying the same terminal at the same time.

Kill rtorrent.

Launch screen.

Start rtorrent in screen.

When your ready press Ctrl+A at the same time, then press D.

Go to your other computer.

Ssh in to your torrenting one.

Type ```
screen -r
```

rtorrent will appear showing you it`s progress - it`s never stopped running.

I do all my torrenting on a computer that doesn`t have a monitor. rtorrent is running constantly (I seed Ubuntu torrents).

I have 4 other computers at home. I can ssh into my monitorless box from any of them and add or remove torrents. As long as I detatch the screen session (Ctrl+A then D). I can check the progress via ssh from any of the others.

I can also do this from work or if I am on holiday, in another country.

---

### Post by fcuk112 on 2009-09-22
well after playing around some more i've finally settled on deluge, i think it's better for my requirements.

using the web UI (ajax) which absolutely rocks!  and setup auto-add so files are saved in the shared torrent folder and auto-picked up by deluge.

thank you so much for your help, i'm happy! :P

---


---
title: "Enable access to an NTFS drive on Linux box"
date: 2006-03-24
forum: General Help
---

### Post by barnabas on 2006-03-24
I am having a little trouble networking my computers. I am very new to Linux (last week I installed it), but have been doing ok with walkthroughs until now:

I have two computers: 

Desktop: dual boot Ubuntu 5.10/Windows XP Pro
  - on this machine I have two hard drives.
    1. Windows install (80 gigs)
    2. Linux install (50 gigs) formatted as ext3 and NTFS Windows storage (150 gigs).

Laptop running windows xp media center edition.

I want to be able to share this 150 gig NTFS Storage partition with the Windows machine. I have installed samba and smbfs and gone through the tutorial here: [http://help.ubuntu.com/starterguide/C/ch07.html#installsamba](http://help.ubuntu.com/starterguide/C/ch07.html#installsamba) but I am getting stuck somewhere. When I type this command: 

sudo testparm sudo /etc/init.d/samba restart 

I get this error: 

Load smb config files from sudo
params.c:OpenConfFile() - Unable to open configuration file "sudo":
        No such file or directory
Error loading services.

I have tried this command and it seems to do something (but I'm not entirely sure what everything means yet): 

sudo testparm smb.conf /etc/inti.d/samba restart

output: 

Load smb config files from smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Allow connection from /etc/init.d/samba (restart) to homes
Allow connection from /etc/init.d/samba (restart) to printers
Allow connection from /etc/init.d/samba (restart) to print$

Has anyone successfully configured a setup like what I have, or have any idea how to? If so, any help would be greatly appreciated. 

Thanks

---

### Post by gerbman on 2006-03-24
[QUOTE=barnabas]When I type this command: 

sudo testparm sudo /etc/init.d/samba restart 

I get this error: 

Load smb config files from sudo
params.c:OpenConfFile() - Unable to open configuration file "sudo":
        No such file or directory
Error loading services.[/QUOTE]
The command isn't quite right. "sudo" is a command that temporarily gives administrator privileges to whatever program follows it. "testparm" gives a summary of your samba service. So the above command is attempting to give admin privs to testparm and pass testparm a file named "sudo"...not quite right. You should be able to run testparm by ```
testparm
```alone. It will give you a summary of the services that samba is providing on your system.

> I have tried this command and it seems to do something (but I'm not entirely sure what everything means yet): 

sudo testparm smb.conf /etc/inti.d/samba restart

You've kinda put two separate commands together. One is the testparm command:```
sudo testparm smb.conf
```and the other is to restart the samba server:```
sudo /etc/init.d/samba restart
```
You should be able to run testparm without sudo. Restarting the samba server, however, will require sudo.
> Has anyone successfully configured a setup like what I have, or have any idea how to?
Yes, I'm doing exactly the same thing you are, so there is no reason to think you can't get it working :-) What makes you think it isn't working? Can you access the share from your laptop?

---

### Post by barnabas on 2006-03-24
[QUOTE=gerbman]Can you access the share from your laptop?[/QUOTE]

No, I have been trying to map a network drive using:

\\computername\username

the dialog pops up asking for a password, but none of my passwords work. I have tried everything from nothing to my root password. It seems strange (to me), but when I specify a name, the password dialog comes up with

user name: \\computername\Guest
password: 

but the user name is greyed out.

On the brighter side, thanks for explaining those two commands. I split them up like you mentioned and everything seemed to work ok. This is what it gave me about my setup:

        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .


I've got security (for the moment) set to SHARE, so shouldn't I be able to just connect without a password?  

Thanks

---

### Post by gerbman on 2006-03-24
Sounds like you're close, you've got a connection, just not authentication.> I've got security (for the moment) set to SHARE, so shouldn't I be able to just connect without a password?I've never used SHARE security, I've always used USER. Could you post all the output of 'testparm' as well as your smb.conf file?

---

### Post by barnabas on 2006-03-24
This is the ouptut from testparm smb.conf:

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

This is my smb.conf file:

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
   security = share

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

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

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

I wasn't planning on keeping the SHARE, but when I specified user, it wouldn't work at all.

Also, I took a look at my log file and it gave me these errors from my laptop trying to connect:

[2006/03/24 10:25:55, 0] smbd/service.c:make_connection(794)
  192.168.0.3 (192.168.0.3) couldn't find service guest

Does this have to do with the "guest account = nobody" above in the smb.conf file?

thanks for your help

---

### Post by gerbman on 2006-03-24
Yeah, it could be the fact that you haven't enabled the guest account, but I really don't know as I usually use 'user' security. I would recommend changing the security to user and making your [homes] definition browseable. Also, I think you'll need to create a samba user with the smbpasswd utility - have you done that? If not you can do it with the following command:```
sudo smbpasswd -a <user>
```where <user> is your username.

Cheers!

---

### Post by barnabas on 2006-03-24
Thanks a lot! I've only got one more problem. I set my security to user, created a new user and pw and all is well. I changed my mount point for my NTFS drive from /windows to /home/username/MyDocs. Is this a necessary move? Or is there a way to leave the mounted drive in /windows and give my user access to that folder? 

Also, I can create / edit files in the user's home directory on the linux box, but I cannot write to the NTFS mounted drive (which is mounted in the home directory). Where do I go from here?

Thanks again for all your help

---

### Post by gerbman on 2006-03-24
First things first. I forgot to mention that NTFS drives cannot be reliably written to when mounted in linux. You can read data from them just fine, but write support is questionable at best at this point. 

[QUOTE=barnabas]I changed my mount point for my NTFS drive from /windows to /home/username/MyDocs. Is this a necessary move? Or is there a way to leave the mounted drive in /windows and give my user access to that folder?[/QUOTE]
I don't think it's necessary from an accessibility point of view. You should be able to set the 'uid' option in your fstab file to give permissions to your account. Again, I don't think this will affect the NTFS drive because it is not writable to begin with. If you can read the NTFS drive then that's all the access you will be able to get. > Also, I can create / edit files in the user's home directory on the linux box, but I cannot write to the NTFS mounted drive (which is mounted in the home directory).Yup, this is exactly the limitation of write support for NTFS filesystems in linux. > Where do I go from here?If I were you, I would convert my NTFS partition to a FAT32 partition. FAT32 partitions can be written just fine in linux.

Lemme know if you need any clarifications. Good luck!

---

### Post by barnabas on 2006-03-24
Thanks, I wasn't aware that I couldn't write to my ntfs from my windows box. That's fine though :) So I do need a little clarification on your statement about setting the 'uid' in the fstab file. Here is a small portion of that file:

<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hdb1	 /windows	       ntfs	    nls=utf8,umask=0222 0	0

would I put the uid in the <options> portion? And would it look like this: 

nls=utf8,umask=0222,uid=username

Thanks again for all your help.

---

### Post by gerbman on 2006-03-24
> So I do need a little clarification on your statement about setting the 'uid' in the fstab file. Here is a small portion of that file:

<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hdb1	 /windows	       ntfs	    nls=utf8,umask=0222 0	0

would I put the uid in the <options> portion? And would it look like this: 

nls=utf8,umask=0222,uid=username
Yup, that's what it would look like; however, if you can already read the data in /windows then there probably isn't much point in setting the uid parameter.> Thanks again for all your help.No problem! Pass it on.

---


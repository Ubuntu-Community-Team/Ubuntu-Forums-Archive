---
title: "Default perms are 755. How can I set them to be different?"
date: 2010-09-12
forum: General Help
---

### Post by Roasted on 2010-09-12
Let's say I have a share I want multiple users to have full reign to. As a result, this share is already set up with the gid being set, so any files/folders that get written to it are automatically assigned the group "share", to which the users in question are members of this group "share."

The problem is, if Bob creates something, it comes down as bob:share with 755 perms, so Fred cannot write/delete. What it optimal is having 775 perms, but it's hard for an administrator to continually do this over and over when it'd be nice to just automatically set the perms on the fly to 775.

How can I change just one folder to default to 775 perms instead of 755?

---

### Post by 73ckn797 on 2010-09-12
> **Roasted said:**
> Let's say I have a share I want multiple users to have full reign to. As a result, this share is already set up with the gid being set, so any files/folders that get written to it are automatically assigned the group "share", to which the users in question are members of this group "share."

The problem is, if Bob creates something, it comes down as bob:share with 755 perms, so Fred cannot write/delete. What it optimal is having 775 perms, but it's hard for an administrator to continually do this over and over when it'd be nice to just automatically set the perms on the fly to 775.

How can I change just one folder to default to 775 perms instead of 755?

See if this link will help: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I believe that if you open terminal and enter:
```
 sudo nautilus
```
you can change the permissions graphically to a folder

---

### Post by Roasted on 2010-09-12
> **73ckn797 said:**
> See if this link will help: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I believe that if you open terminal and enter:
```
 sudo nautilus
```
you can change the permissions graphically to a folder

This does not solve my issue.

When you create a folder, by default it comes down as 755 permissions. THAT is my problem. When Fred creates a folder, it's fred:share 755. What about bob? Bob is out of luck now, since there is a 5 over the folder. SURE I could do what you said above and reset permissions several times a day, but... no.

How do I set it so when somebody creates a folder, it comes down as 775 perms, not 755.

Again - I do not need help setting permissions. I need help re-adjusting the current standard of 755 to something that suits my situation better.

---

### Post by 73ckn797 on 2010-09-12
Sorry my suggestions will not help. I have not had to deal with your particular situation but was more seeking to address general solution(s).

---

### Post by Noz3001 on 2010-09-12
umask? [http://linux.about.com/od/linux101/l/blnewbie3_2_6.htm](http://linux.about.com/od/linux101/l/blnewbie3_2_6.htm)

---

### Post by drs305 on 2010-09-12
I believe there is a setting in /etc/profile that sets umask to 022. I've seen posts stating that is the file to edit to change the defaults but have no experience with changing it. 

In *your* user's .profile file is this section:
> 
# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022


Added: You may need to logout to get the new settings to work.

p.s. *73ckn797* - thanks for trying to help.

---

### Post by 73ckn797 on 2010-09-12
> **drs305 said:**
> p.s. *73ckn797* - thanks for trying to help.
Thanks. I do not know all the answers and only hope to help "push" people along to look into available resources that may get people to learn and, hopefully, figure out a solution.

---

### Post by Roasted on 2010-09-12
Appreciate the help 73, but setting perms wasn't my problem, it went a little deeper than that. :P 

Umask sounds like it's it. I'll check this out.

---

### Post by drs305 on 2010-09-12
Roasted, let us know if that's the solution. As I said, I haven't tried it but would like to keep it in my bag of tricks if that is indeed the solution. Sorry I can't be more affirming and you are the guinea pig... ;-)

---

### Post by Roasted on 2010-09-13
> **drs305 said:**
> Roasted, let us know if that's the solution. As I said, I haven't tried it but would like to keep it in my bag of tricks if that is indeed the solution. Sorry I can't be more affirming and you are the guinea pig... ;-)

Hahaha no sweat. I'll test this later today. I have an Ubuntu VM set up JUST for guinea pig situations, so it should serve nicely. ;)

EDIT - though I got curious and tried to figure it out on my laptop anyway... but I don't see /etc/profile when I'm running nautilus as root. I only see profile.d, which is a directory that is empty besides a file speechd-user-report.sh... Hmm...

---

### Post by CharlesA on 2010-09-13
How was the file/folder being shared?

The umask is probably what you want. :)

---

### Post by Roasted on 2010-09-13
> **CharlesA said:**
> How was the file/folder being shared?

The umask is probably what you want. :)

Samba.

---

### Post by drs305 on 2010-09-13
Here is what I have (default) for the Lucid  /etc/profile file contents. If I have time later I'll try playing with it myself, but it's not high on my to-do list at the moment so don't hold you breath on this one.  ;-)
> 
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

---

### Post by Morbius1 on 2010-09-13
> Let's say I have a share I want multiple users to have full reign to. As  a result, this share is already set up with the gid being set, so any  files/folders that get written to it are automatically assigned the  group "share", to which the users in question are members of this group  "share."

The problem is, if Bob creates something, it comes down as bob:share  with 755 perms, so Fred cannot write/delete. What it optimal is having  775 perms, but it's hard for an administrator to continually do this  over and over when it'd be nice to just automatically set the perms on  the fly to 775.

How can I change just one folder to default to 775 perms instead of 755?This would be a lot easier if we can see how your share is set up and what method you're using to share it. If you have a classic Samba share then you could set the target directory to 775 and then insert a line in the share definition that would inherit the permissions of the target folder:
```
inherit permissions = yes
```New folders will inherit the permissions of the parent directory and new files will inherit the read / write permissions of the parent directory.

If you're using Nautilus-shares ( usershares ) then this could get complicated depending on what else you're sharing.

---

### Post by Roasted on 2010-09-13
So if I add that tag to each share entry, it should bring the perms accordingly? 

I use a very basic gui tool for managing samba, known as system-config-samba in synaptic. Are there other samba utilities that have more advanced options that might perhaps have something like "inherit permissions" as an option?

Here's my smb.conf:

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
;	passdb backend = tdbsam

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
;	printing = cups
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
;	usershare max shares = 100

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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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

[backup_data]
	path = /media/storage/backup_data
	writeable = yes
;	browseable = yes
	valid users = jason, user

[curt]
	path = /media/storage/curt
	writeable = yes
;	browseable = yes
	valid users = curt, jason

[tyler]
	path = /media/storage/tyler
	writeable = yes
;	browseable = yes
	valid users = jason, tyler

[pam]
	path = /media/storage/pam
	writeable = yes
;	browseable = yes
	valid users = jason, pam

[jason]
	path = /home/jason
	writeable = yes
;	browseable = yes
	valid users = jason

[public]
	path = /media/storage/public
	writeable = yes
;	browseable = yes
	valid users = curt, jason, pam, tyler, user

```

---

### Post by CharlesA on 2010-09-13
Ok. Here's [s]an easier way[/s] the way I do it:

```
[Shared]
        comment = Shared Folder
        create mode = 664
        invalid users = clone
        path = /array/shared
        write list = charles,htpc
        directory mode = 775

```

I use file permissions as well.

I am a member of the htpc group, and the htpc user owns the files.

---

### Post by Morbius1 on 2010-09-14
> I use a very basic gui tool for managing samba, known as  system-config-samba in synaptic. Are there other samba utilities that  have more advanced options that might perhaps have something like  "inherit permissions" as an option?If you want to implement the "inherit permissions" or CharlesA's "create mode / directory mode" method then you will in fact have to use a more advanced utility to make those changes - it's called gedit:
```
gksu gedit /etc/samba/smb.conf
```Once you make the changes save the file, exit gedit, and back in the terminal restart samba. I don't know what version of Ubuntu you're using so I'll give you two commands:
```
sudo service samba restart
``````
sudo service smbd restart
```*The last one is for 10.04*

---

### Post by Zill on 2010-09-14
To change default permissions for *all* users from 755 to 775 change umask in file /etc/profile from 022 to 002 as follows:

Backup original profile file:
```
sudo cp /etc/profile /etc/profile_bak
```
Edit profile file:
```
sudo nano /etc/profile
```
Comment out line umask:
```
# umask 022
```
Add new line:
```
umask 002
```
Save and exit nano:
ctrl-o, ctrl-x
Logout and login again

Default permissions should now be 775

---

### Post by Morbius1 on 2010-09-14
This topic is like two parallel universes colliding. :p

Unless I'm mistaken this is a specific problem with a Samba share for which the user has been given two alternatives.

Changing the default umask of the system itself will certainly fix the samba problem but at the cost of changing the default permissions of all new files and folders.

---

### Post by Zill on 2010-09-14
> **Morbius1 said:**
> ...Changing the default umask of the system itself will certainly fix the samba problem but at the cost of changing the default permissions of all new files and folders.
Maybe I misunderstood the OP...
> **Roasted said:**
> ...How do I set it so when somebody creates a folder, it comes down as 775 perms, not 755.

Again - I do not need help setting permissions. I need help re-adjusting the current standard of 755 to something that suits my situation better.

---

### Post by Roasted on 2010-09-14
> **Morbius1 said:**
> 
Changing the default umask of the system itself will certainly fix the samba problem but at the cost of changing the default permissions of all new files and folders.

My goal wasn't to do this globally. I just wanted to do this on a per-folder basis that I set accordingly.

---

### Post by Zill on 2010-09-15
> **Roasted said:**
> My goal wasn't to do this globally. I just wanted to do this on a per-folder basis that I set accordingly.
Maybe you could set umask to 002 as detailed earlier, giving default permissions of 775.  Then change user and group ownership (using chown) of files and directories accordingly.

For example  
/home/Bob should be owned by Bob:Bob (only "Bob" can write)
/home/Fred should be owned by Fred:Fred (only "Fred" can write)
/home/share should be owned by share:share ("share","Bob" and "Fred" can write)

---

### Post by Roasted on 2010-09-15
> **Zill said:**
> Maybe you could set umask to 002 as detailed earlier, giving default permissions of 775.  Then change user and group ownership (using chown) of files and directories accordingly.

For example  
/home/Bob should be owned by Bob:Bob (only "Bob" can write)
/home/Fred should be owned by Fred:Fred (only "Fred" can write)
/home/share should be owned by share:share ("share","Bob" and "Fred" can write)

That's the idea. But when Bob creates a folder in Bob, it comes down as Bob:Bob. Using the GID setting in Nautilus, it comes down as Bob:Share. Okay, great.

But with default perms coming down as 755, it restricts the group to read/execute only. So when Bob creates something, Fred still can't edit/delete.

That's where my problem lies. I just want one single folder with Windows XP style permissions that no user ever has to worry about being restricted and can have free reign over the share. Using Linux is great because of its security, but what about when I want to kick the security back 1 or 2 or 37 notches? :P

---

### Post by Zill on 2010-09-15
> **Roasted said:**
> ...But with default perms coming down as 755, it restricts the group to read/execute only...
If you change umask as suggested to 002 then default permissions *should* be 775. :confused:

---

### Post by Morbius1 on 2010-09-16
I'm still confused as to whether we are talking about users on the box with the share or users on the network accessing the share. In Samba, at least in classic samba, you have complete control over who owns and what permissions are set to any file transfered or accessed by a remote user. Samba allows many options to resolve your issue.

Let's take one of your shares as an example:

> [public]
    path = /media/storage/public
    writeable = yes
;    browseable = yes
    valid users = curt, jason, pam, tyler, user*Scenario 1: /media/storage/public has ownership / permissions set at root:root 777*
> [public]
    path = /media/storage/public
    writeable = yes
;    browseable = yes
[COLOR=Blue]     create mode = 666
directory mode = 777
[/COLOR]     valid users = curt, jason, pam, tyler, userAll new folders added by curt will have ownership / permissions set at curt:curt 777. Everyone validated by the "valid users" list will have full access to anything curt added to the share.

* Scenario 2 : You've already modified ownership / permissions of /home/storage/public*

Let's say you set up /home/storage/public as follows:
owner:group = root:remoteuser
permissions = 775
> [public]
    path = /media/storage/public
    writeable = yes
;    browseable = yes
[COLOR=Blue]     create mode = 664
directory mode = 775
[/COLOR] [COLOR=Blue]         force group = remoteuser[/COLOR]
    valid users = curt, jason, pam, tyler, userAll new folders added by curt will have ownership / permissions of curt:remoteuser 775. Everyone validated by the "valid users" list will have full access to anything added to the share assuming they are all members of the "remoteuser" group.

There are many more options available depending on how complex you want to make this.

---

### Post by Roasted on 2010-09-16
> **Zill said:**
> If you change umask as suggested to 002 then default permissions *should* be 775. :confused:

But from what I'm hearing, the umask is changed globally and not on a per-folder basis like I'm aiming for. Am I right, or misunderstanding?

---

### Post by Zill on 2010-09-16
> **Roasted said:**
> But from what I'm hearing, the umask is changed globally and not on a per-folder basis like I'm aiming for. Am I right, or misunderstanding?
Yes - but then you change your user and group *ownership* for *each* folder accordingly.

---

### Post by Roasted on 2010-09-16
> **Zill said:**
> Yes - but then you change your user and group *ownership* for *each* folder accordingly.

Maybe I'm being picky, but I don't want it set globally. I just want to have one folder that defaults to 775 perms...

It seems as if with additional tags I can do this in Samba, but other than that I have to wonder why something like this is so hard, or if I'm just completely misunderstanding the jist behind it.

---

### Post by CharlesA on 2010-09-16
Just use the options that Morbius1 posted. :)

No need to change the umask.

---

### Post by Zill on 2010-09-16
> **Roasted said:**
> Maybe I'm being picky, but I don't want it set globally. I just want to have one folder that defaults to 775 perms...
Personally, I do not use or connect to Windows so have no need for Samba - NFS works fine for me. ;-)

Linux user and group permissions seem to be a simple method of providing access control to me.  While the Ubuntu default permissions of 755 are fine with a single user, with multiple users permissions of 775 work better IMHO.  It is then simply a matter of choosing the right ownership (including its group) for each folder!

---

### Post by Roasted on 2010-09-17
> **Zill said:**
> Personally, I do not use or connect to Windows so have no need for Samba - NFS works fine for me. ;-)

Linux user and group permissions seem to be a simple method of providing access control to me.  While the Ubuntu default permissions of 755 are fine with a single user, with multiple users permissions of 775 work better IMHO.  It is then simply a matter of choosing the right ownership (including its group) for each folder!

Right. It is simply a matter of choosing the right ownership and group for each folder. That's the problem, though. With the defaults being 755, when Fred creates something it comes down as 755. Even if the group is locked in with GID by Nautilus and it comes down as fred:share, guess what? Group has 5 perms. Bob can't write/delete. 

I suppose I could just make the samba changes accordingly. But I have to wonder - how in the world would you do this at the system level (as if multiple users were sharing a computer)? At that point you have no choice but to use umask it sounds like.

---

### Post by Zill on 2010-09-17
> **Roasted said:**
> Right. It is simply a matter of choosing the right ownership and group for each folder. That's the problem, though. With the defaults being 755, when Fred creates something it comes down as 755. Even if the group is locked in with GID by Nautilus and it comes down as fred:share, guess what? Group has 5 perms. Bob can't write/delete...
That is exactly my point.  The Ubuntu default permissions of 755 only "work" for a single user, or if you are happy for other users to only have read access.  If you want multiple users to automatically have write access it is necessary to change the default permissions (via umask = 002) to 775 and then change the :group for each folder accordingly.  You can create as many groups as you wish and then allocate users to each group to give them write permissions for each folder with that group.  If they are not in that group then they will have read-only access as they will be classed as "others".

---

### Post by Morbius1 on 2010-09-17
> I suppose I could just make the samba changes accordingly. But I have to  wonder - how in the world would you do this at the system level (as if  multiple users were sharing a computer)? At that point you have no  choice but to use umask it sounds like.What you are describing is Windows. Linux , like UNIX before it, is not Windows. Having everyone and your Aunt Agnes have read write permissions on everyone else's files is pretty much a foreign concept. I believe the technical term is chaos.

There are ways around this: setgid, ACL, bindfs, .. etc. Don't know how this all works with samba but.... This is the first time I've ever seen using umask itself.

---

### Post by Roasted on 2010-09-18
> **Morbius1 said:**
> What you are describing is Windows. Linux , like UNIX before it, is not Windows. Having everyone and your Aunt Agnes have read write permissions on everyone else's files is pretty much a foreign concept. I believe the technical term is chaos.



No. It's not Windows. It's Samba. Samba utilizes the Linux permissions when you are actually writing data to the drive. That's why you need the Samba user to also exist on the Linux system. They work together. This actually has zero to do with Windows. It's the same if I'm using a Linux box via samba or a Mac box via samba as well.

---

### Post by Zill on 2010-09-19
> **Roasted said:**
> No. It's not Windows. It's Samba. Samba utilizes the Linux permissions when you are actually writing data to the drive. That's why you need the Samba user to also exist on the Linux system. They work together. This actually has zero to do with Windows. It's the same if I'm using a Linux box via samba or a Mac box via samba as well.
Err... Not *quite* true!

[Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") is a free software re-implementation of the [SMB/CIFS]("http://en.wikipedia.org/wiki/Server_Message_Block") networking protocol.  SMB was essentially developed by Microsoft and, as such, is primarily used on Windows systems.

Samba is a useful utility to network with Windows PCs, but is certainly not necessary to network with other Linux PCs.

---

### Post by Roasted on 2010-09-20
> **Zill said:**
> Err... Not *quite* true!

[Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29") is a free software re-implementation of the [SMB/CIFS]("http://en.wikipedia.org/wiki/Server_Message_Block") networking protocol.  SMB was essentially developed by Microsoft and, as such, is primarily used on Windows systems.

Samba is a useful utility to network with Windows PCs, but is certainly not necessary to network with other Linux PCs.

It's pretty DAMN handy if you have Linux, Mac, and Windows PCs, though! For me I fail to see the point in how I would ever need NFS. With having mixed platforms NFS just falls severely short, and Samba works pretty darn well with Linux to Linux. I can't recall any major issues I ever had.

I had no idea MS was ever involved with Samba... I find that hard to believe... But from further reading it seems like while they have had major involvement with it, that it wasn't originally created by MS. I remember IBM having a hand in it somewhere...

---


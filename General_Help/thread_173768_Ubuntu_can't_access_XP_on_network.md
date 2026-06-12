---
title: "Ubuntu can't access XP on network"
date: 2006-05-10
forum: General Help
---

### Post by Oomska on 2006-05-10
[B]EDIT. THIS ISSUE HAS BEEN SOLVED!

Please see last couple of posts if you are experiencing similar problems.
[/B]

Hi,

I'm a total nob when it comes to linux and networking so I hope someone can give me some clear answers:D. I am trying to network 2 PC's, one using XP and the other Ubuntu, through a cable router. I've installed Samba, set security to 'share', and set up some shared folders on both computers. 

The networked computers show up in  Network places on both machines. However, I can only browse the Ubuntu shared folders the XP computer. If I try to browse the XP shared folders using Ubuntu, I get the following error message:

'The folder contents could not be displayed.' 

Any idea how to solve this?

Further info:
1) Windows firewall is on (is it safe to disable this and let my router act as firewall?)
2) The shared folders on XP are on newly created  FAT 32 partitions. However, my primary partition for XP itself is NTFS.

Any idea how I can allow the Linux PC to access files  the XP PC?

---

### Post by hero2zero on 2006-05-10
I'm no expert on this, but I after many attempts I finally got my Samba server/shares between my ubuntu box and my wife's XP laptop working.  I used this page:

[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29")

Pay special attention to the "Mounting a Samba Share"--especially,

    sudo apt-get update 
    sudo apt-get install smbfs

Without this, I could not see my XP shares.  Good luck.  :cool:

---

### Post by MetalMusicAddict on 2006-05-10
You need to set-up a user on the XP machine same as your Ubuntu user. Sorry I cant help more. Im in a hurry. Ill check back though.

---

### Post by Oomska on 2006-05-11
[QUOTE=MetalMusicAddict]You need to set-up a user on the XP machine same as your Ubuntu user. Sorry I cant help more. Im in a hurry. Ill check back though.[/QUOTE]

Ah. You mean I just go into XP and simply add a new user account? Do I use the same name as my Ubuntu desktop or as the network name of my Linux PC? And do I need to set a passwprd for this account?

---

### Post by Oomska on 2006-05-11
Well I added a user to XP with my Linux machine name but still no dice. Turned off windows firewall, but that didn't help. I am honestly stuck here.

---

### Post by Al3xanR0 on 2006-05-11
Is the XP machine on a domain or in a workgroup? Can you ping the XP machine from the Ubuntu terminal? Have you implement the correct share perm on the windows directory you are attempting to access from your Ubuntu machine?

---

### Post by chettyk on 2006-05-11
I suggest you shut down the firewall on your XP whenever you are testing Samba.

The computer running Samba as well as the Samba system itself appears to require a user with the same username and password as the account on the XP from which you are accessing the Samba shares.

I went about it the following way:

1. First add a user with the same username and password as XP. On Ubuntu you can add a user from System -> Administration -> Users and Groups.

2. Open a terminal (Applications -> Accessories -.Terminal).Type 
```
sudo smbpasswd -a <username>
```
Once again, give the same username and password as the XP account.

I used the following posting to set up my Samba system:
[http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647)

See if this helps.

---

### Post by Oomska on 2006-05-11
[QUOTE=chettyk]I suggest you shut down the firewall on your XP whenever you are testing Samba.

The computer running Samba as well as the Samba system itself appears to require a user with the same username and password as the account on the XP from which you are accessing the Samba shares.

I went about it the following way:

1. First add a user with the same username and password as XP. On Ubuntu you can add a user from System -> Administration -> Users and Groups.

2. Open a terminal (Applications -> Accessories -.Terminal).Type 
```
sudo smbpasswd -a <username>
```
Once again, give the same username and password as the XP account.

I used the following posting to set up my Samba system:
[http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647)

See if this helps.[/QUOTE]


Thanks, I did what you said but now I can't change my smb.conf file. It seems to be read only and if I try to change permissions it says I am not the owner of the file so can't. 

Excuse me while I vent: ](*,) ](*,) :confused:

---

### Post by Al3xanR0 on 2006-05-11
[QUOTE=Oomska]Thanks, I did what you said but now I can't change my smb.conf file. It seems to be read only and if I try to change permissions it says I am not the owner of the file so can't. 

Excuse me while I vent: ](*,) ](*,) :confused:[/QUOTE]

```
chown uid filename
```

---

### Post by Oomska on 2006-05-11
Ignore my last post. Was tring to edit smb.conf through file browser instead of sudo gedit. Oh, the noob that I am. Right, be back in 5 minutes with more questions...watch this space

---

### Post by Oomska on 2006-05-11
Alright, still can't access files on XP and now that I have changed security from shared to user I can't access my Linux machine from XP. XP brings up a login box with the name 'Oomska\Guest' greyed out and I don't have a password for that.

Here's the exact error message I get when trying to access the XP machine through Places > Network Servers > (XP server):

> **The folder contents could not be displayed.**

Sorry, couldn't display all the contents of "Windows Network: ronnie".





Here's my samba config:

> #
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
   security = user

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


[MySharedFolder]
path = /home/oomska
comment = oomska on ubuntu
available = yes
browseable = yes
public = yes
writable = yes

[UbuntuDesktop]
path = /home/oomska/Desktop
comment = Oomska's ubuntu desktop
available = yes
browseable = yes
public = yes
writable = yes


---

### Post by chettyk on 2006-05-13
[QUOTE=Oomska]Alright, still can't access files on XP and now that I have changed security from shared to user I can't access my Linux machine from XP. XP brings up a login box with the name 'Oomska\Guest' greyed out and I don't have a password for that.
[/QUOTE]

Like I said in my earliest post, the machine running the Samba server must have a user account with the same username and password as the account on the XP from which you'll access the Samba server. In addition, you must add the same username and password to the Samba server as well. I have given both steps in my earlier post.

In your samba config file, change the following line
```
; wins support = no
```
to:
```
wins support = yes
```

Before you make any changes to the samba config file, I suggest you create a backup copy of it.

Have a look at this chapter in **Using Samba** published by O'Reilly. I found it useful in setting up the Windows XP end of things:
[http://www.faqs.org/docs/samba/ch03.html](http://www.faqs.org/docs/samba/ch03.html)

You can read the earlier chapters too and get a good introduction to Samba. I ultimately opted to buy a print copy.

Remember to shut down the firewall on your XP system when trying to access the Samba server. I once spent several days banging my head on a wall, wondering why nothing I tried had any effect.

Above all, have patience. Sometimes it takes a while to get things working.

---

### Post by Oomska on 2006-05-14
Thanks. I've tried whatyou said and added the relevant usernames and passwords to XP and Ubuntu. Unfortunatley, I'm still getting the same error message when trying to browse my XP shares in Ubuntu.

I've read al the material I can find but still can't figure out what's wrong.

The shared XP files are on FAT32 partitions but XP is set up on an NTFS partition - that wouldn't cause the problems would it?

---

### Post by chettyk on 2006-05-14
Oh hell! My apologies. For some reason I got it into my head that you were trying to access the Ubuntu files from XP. The instructions I gave are for that. Since I have not done it the other way about -- accessing XP files from Ubuntu -- I'll need to test how to go about it. In theory, it ought to be fairly straightforward and I am hoping that in practice it turns out that way. I'll get back to you when I am done but that may take a while though.

In the meantime, since you have the system set up, could you check whether you are able to access Ubuntu file shares from XP?

---

### Post by chettyk on 2006-05-15
This Ubuntu Wiki page gives a good idea of what needs to be done to access shared folders in Windows XP from a Ubuntu system:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29)

I haven't tried it out yet. But perhaps you could give it a shot.

Cheers.

---

### Post by KillrBuckeye on 2006-05-15
Hi Oomska.  This may be a silly question, but did you change the sharing properties of the FAT32 partitions on the Windows machine through the Properties menu?  The fact that your Ubuntu machine sees your Windows machine tells me that the network is configured properly and is properly just a permissions problem.  I didn't have any trouble seeing folders on my Windows machine from Ubuntu, as long as I had set the folders up for sharing.

---

### Post by Oomska on 2006-05-15
[QUOTE=KillrBuckeye]Hi Oomska.  This may be a silly question, but did you change the sharing properties of the FAT32 partitions on the Windows machine through the Properties menu?  The fact that your Ubuntu machine sees your Windows machine tells me that the network is configured properly and is properly just a permissions problem.  I didn't have any trouble seeing folders on my Windows machine from Ubuntu, as long as I had set the folders up for sharing.[/QUOTE]

Um, I'm not sure. Just to make sure I'm not doing anything wrong, how would I actually go about setting the right share properties say if I have a FAT partitioned drive E: with a folder of music in it called 'My Music'?



Oh and to Chetykk, thank for the link. I'll check it out tomorrow.

---

### Post by KillrBuckeye on 2006-05-15
In Windows Explorer, right-click on E: (or just the 'My Music' folder within) and select "Properties".  Then go to the "Sharing" tab and check the box labeled "Share this folder on the network" (and the other box if you want).  Then click "Appy".  If you haven't done this, then it's probably the reason why you can't see the drives/folders.  ;)

---

### Post by Oomska on 2006-05-16
Ah, I've already done that. Sorry, I thought you meant some advanced way of setting up sharing that I was unaware of. I'm going to go throgh the whole network and check to see whether I have missed something. Some troubleshooting needed I guess.

---

### Post by sparkov on 2006-05-16
I've been playing about with the Breezy live cd and have no trouble at all accessing shared folders from XP machines without installing samba.  Do you have another XP machine you can test access from?

I had a similar problem earlier this week using only XP where I couldn't access folders from my flatmate's computer, but only on one of his drives.  Shares on his other drive worked fine.  It turned out that although the folders were shared correctly, the permissions for the actual drive weren't set up properly.  I think they are changed in a similar way to the folder permissions, but I don't know exactly what he did to fix it.

---

### Post by Oomska on 2006-05-16
[QUOTE=sparkov]I've been playing about with the Breezy live cd and have no trouble at all accessing shared folders from XP machines without installing samba.  Do you have another XP machine you can test access from?

I had a similar problem earlier this week using only XP where I couldn't access folders from my flatmate's computer, but only on one of his drives.  Shares on his other drive worked fine.  It turned out that although the folders were shared correctly, the permissions for the actual drive weren't set up properly.  I think they are changed in a similar way to the folder permissions, but I don't know exactly what he did to fix it.[/QUOTE]

Unfortunately, I don't have another xp machine to test on. One thing I could do would be to partition the ubuntu machine, set it up for dual boot, and load XP onto the second partition -  would that help, or is this a samba communicating with XP issue?

---

### Post by sparkov on 2006-05-16
I only have fairly limited experience using Ubuntu, but you as far as i can tell, you shouldn't need Samba at all to access XP shares, only to share with XP (i.e. act as a server).  I don't think this problem is worth installing XP, I don't think it is a fault in your Ubuntu machine.

I can access windows shares on my network by just running the live cd and clicking "Places --> Network Servers".  All the folders appear then and are fully accessible.

You could try just booting off of a live cd and giving that a go?

Are you able to see folders on the XP machine but just not access the contents of them?

---

### Post by andy_cowman on 2006-05-16
Hiya, i have XP and Ubuntu sharing very nicely but i found the config file for samba included with ubuntu did not work properly ( icouldnt work out why though!) I wrote this one which does work although you may need to play with permissions....

[http://www.andycowman.co.uk/smb.conf](http://www.andycowman.co.uk/smb.conf)

change your the folder references to suit your needs, you may find an error if you set the home directoy to everyone access of dmrc has incorrect permissions . doesnt appear to actually have an affect and i havent bothered correcting yet on my closed network.

Hopefully it may be useful.


andy

---

### Post by jones_jj on 2006-05-17
To get ownership back just do a sudo chown -R <username> <filename> and you should be good to go, and make sure you create a samba user using the **sudo smbpasswd -a <username>** command.

The way I got Samba to work is to of course first install it, and this is the easiest way that I have found to do this is to go to ** System->Administration->Shared Folders**.  Then you will want to add a file/directory that you want to share the rest is pretty much self explanatory.  You will want to share with SMB of course, and check the allow browsing folder check box.

---

### Post by Oomska on 2006-05-17
[QUOTE=sparkov]You could try just booting off of a live cd and giving that a go?

Are you able to see folders on the XP machine but just not access the contents of them?[/QUOTE]

No, I can't see the folders themselves. No matter whether I use the standard install of Ubuntu or the Live CD, I can see the XP machine in places/network servers, but when I click on it to try to browse it, I get the following error:

> **The folder contents could not be displayed.**

Sorry, couldn't display all the contents of "Windows Network: xpmachine".



Another thing - did some troubleshooting and entered 'ping xpmachine' in the terminal, which returned the response 'unknown host xpmachine'. I think this could be part of the problem. The follwing work on both machines:

ping 127.0.0.1
ping localhost
ping localhost.localdomain
ping ubuntu
ping <IP Address of ubuntu>
ping <IPAddress of xpmachine>
ping <router/DNS server address>

Therefore, I can ping the xp machine from ubuntu by IP address but I can't ping it by name. Maybe this is what is causing the problem

---

### Post by chettyk on 2006-05-18
[QUOTE=Oomska]No, I can't see the folders themselves. No matter whether I use the standard install of Ubuntu or the Live CD, I can see the XP machine in places/network servers, but when I click on it to try to browse it, I get the following error:
[/QUOTE]

It may be your Ubuntu computer is detecting the XP correctly but is not able to mount the shared folders. Check out the Ubuntu Wiki link I mentioned earlier. I thought it described how to mount shared folders.

Over the week-end, I am hoping to enable folder sharing on my laptop which has XP loaded and see how to access the share from Ubuntu on my desktop.

---

### Post by Oomska on 2006-05-18
[QUOTE=chettyk]It may be your Ubuntu computer is detecting the XP correctly but is not able to mount the shared folders. Check out the Ubuntu Wiki link I mentioned earlier. I thought it described how to mount shared folders.

Over the week-end, I am hoping to enable folder sharing on my laptop which has XP loaded and see how to access the share from Ubuntu on my desktop.[/QUOTE]

SOLVED! :D 

Chettyk, you are a genius. Many thanks. It did turn out to be a mount problem. Well, human error actually as I followed the guide but wasn't typing in the mount command correctly. Consequently, I was making directories that were never eventually mounted. 

So for those of you who can't access your XP shares on your Ubuntu machine, or are getting the error message mentioned above, follow this guide to mount your shared XP folders in Ubuntu:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29")

---

### Post by chettyk on 2006-05-18
Congratulations! I know the feeling of exhilaration at having a problem like that licked.

---

### Post by rcarring on 2006-05-19
I don't do it that way at all.

I just go to Places on the menu and add a windows share by filling in some info in the drop down box that appears.

I specify the server, sharename, username, domain and name I want to call the shortcut, and its mounted on the desktop

---


---
title: "Samba Issues"
date: 2010-07-21
forum: General Help
---

### Post by jmg999 on 2010-07-21
Hi,
   
  So, I’ve been having this ongoing issue w/ a fileserver I have set up on a private network.  After narrowing down the problem, it appears to be an issue related to Samba, but I can’t nail it down for certain.  Here’s the setup…
   
  I work mainly from a Windows XP SP2 desktop.  I also have an Ubuntu 8.04.4 LTS fileserver.  The fileserver houses three RAID arrays.  The first is a 2x250GB RAID 1 setup for the OS.  The second array is on a Promise EX8350 controller card that has 8x500GB HDDs attached to it.  Originally, the card was set to manage a RAID 5 array, but the card went bad, and Promise replaced it, but I never set it back up.  The mount point for this array was /disk.  The third array is a direct-attached-storage (DAS) device connected to the fileserver via dual-eSATA cables.  It consists of 8x1TB HDDs in a software (MD RAID) RAID 5 array.  The mount point for this array is /disk2.  Both the XP box and the fileserver run into a Netgear Gb switch, and I connect to the DAS array via a mapped drive.
   
  When the Promise controller managed the only array, I never had any issues.  Once I introduced the DAS device, that’s when the problems began.  I work from home mostly, and the company I work for has associates and colleagues all over the world.  We share quite a few files, and the easiest (read: cheapest) way to manage this was to introduce Bit Torrent to our setup.  It just alleviates a lot of problems (no internal fileserver, no single point of failure, etc.).   
   
  The problem began, when I would download more than about 15 torrents or so all at once directly to the DAS array.  The array would go offline, and it would begin to resync.  Given the size of the array, this process takes upwards of 18 hours.  After experiencing this issue multiple times, I decided that it would be better for the health of the array to download directly to my XP box, then transfer the files over the LAN to the array.
   
  Additionally, if I ever restarted the array, mdadm would be unable to stop the array, b/c Samba would be unable to close its file handles.  At first, I would have to perform a hard shutdown.  Finally, I found somewhat of a work-around.  I started using fuser to kill Samba handles, and then mdadm was able to stop the array, and I was able to restart w/out a problem.   
   
  However, transferring from my XP box to the DAS array introduced a new problem.  File transfers from the XP box to the DAS array were taking *forever.*  For instance, a 1 GB file transfer might take 20-25 minutes.  I tried to replicate this problem from my laptop, and I was able to do so, so it doesn’t appear to be an issue directly related to the desktop XP box.
   
  To rule out the array, I created a new Samba share on the RAID 1 array housing the OS.  The transfer speeds were the same.  I also tried DD to check direct writes…
    
  ```
 sudo dd if=/dev/zero of=/disk2/arraytest bs=4k count=100000
  100000+0 records in
  100000+0 records out
  409600000 bytes (410 MB) copied, 3.98397 s, 103 MB/s 
```
   
  I even tried setting up an FTP server to test speeds from the XP box to the array.
   
  ```
 Tue Jul 20 10:14:51 2010 [pid 7709] CONNECT: Client "192.168.2.10"
  Tue Jul 20 10:14:51 2010 [pid 7708] [jeffe] OK LOGIN: Client "192.168.2.10"
  Tue Jul 20 12:10:54 2010 [pid 6819] CONNECT: Client "192.168.2.10"
  Tue Jul 20 12:10:54 2010 [pid 6818] [jeffe] OK LOGIN: Client "192.168.2.10"
  Tue Jul 20 12:16:29 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 28171.85Kbyte/sec
  Tue Jul 20 12:17:14 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
  Tue Jul 20 12:17:56 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 28461.97Kbyte/sec
  Tue Jul 20 12:18:00 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
  Tue Jul 20 12:19:18 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 28487.57Kbyte/sec
  Tue Jul 20 12:20:15 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
  Tue Jul 20 12:20:59 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 27907.82Kbyte/sec
  Tue Jul 20 12:21:14 2010 [pid 6820] [jeffe] OK DELETE: Client "192.168.2.10", "/disk2/temp/test_file.avi"
  Tue Jul 20 12:22:06 2010 [pid 6820] [jeffe] OK UPLOAD: Client "192.168.2.10", "/disk2/temp/test_file.avi", 1101266944 bytes, 21500.00Kbyte/sec 
```
   
  So, after all of this, I’m thinking that it’s something to do w/ Samba.  Here’s my smb.conf file…
   
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
     workgroup = BAMA
   
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
  # /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
  # in the samba-doc package for details.
  ;   security = user
   
  # You may wish to use password encryption.  See the section on
  # 'encrypt passwords' in the smb.conf(5) manpage before enabling.
     encrypt passwords = true
   
  # If you are using encrypted passwords, Samba will need to know what
  # password database type you are using.  
     passdb backend = tdbsam
   
     obey pam restrictions = yes
   
  ;   guest account = nobody
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
  # See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
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
  ;   browseable = yes
   
  ;[Test Share]
  ;       comment = /home/jeffe/test
  ;       browseable = yes
  ;       path = /home/jeffe/test
  ;       valid users = jeffe
  ;       writeable = yes
  ;       create mask = 0755
  [Disk]
          comment = Media
          browseable = yes
          writeable = yes
          path = /disk
          valid users = jeffe
  [Disk2]
          comment = Media
          browseable = yes
          writeable = yes
          path = /disk2
          valid users = jeffe
   
  # By default, \\server\username shares can be connected to by anyone
  # with access to the samba server.  Un-comment the following parameter
  # to make sure that only "username" can connect to \\server\username
  ;   valid users = %S
   
  # By default, the home directories are exported read-only. Change next
  # parameter to 'yes' if you want to be able to write to them.
  ;   writable = yes
   
  # File creation mask is set to 0600 for security reasons. If you want to
  # create files with group=rw permissions, set next parameter to 0664.
  ;   create mask = 0600
   
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
```
   
  Any help at all would be greatly appreciated.  Thank you.

---


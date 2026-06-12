---
title: "Write access to SMB"
date: 2010-04-16
forum: General Help
---

### Post by adave on 2010-04-16
Hello everyone.  I have tried almost everything and still can't write to the SMB share on my ubuntu machine from my mac.  The [media] section is the folder that I'm trying to enable write access for.  Any help would be greatly appreciated.  I have pasted the smb.conf file below.  Thanks.

[global]

   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   wins support = yes 
   wins server = w.x.y.z
   dns proxy = no
   name resolve order = lmhosts host wins bcast
   username map = /etc/samba/smbusers

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
#  syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = user 
   username map = /etc/samba/smbusers/
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully*
   pam password change = yes
   map to guest = bad user

########## Domains ###########

   domain logons = yes
;   logon path = \\%N\profiles\%U
#   logon path = \\%N\%U\profile
;   logon drive = H:
#   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

#   load printers = yes

# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
#   domain master = auto
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
;   usershare allow guests = yes

#======================= Share Definitions =======================

[homes]
;   comment = Home Directories
;   browseable = yes 

   read only = no 

   create mask = 0775

   directory mask = 0775

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   writable = yes 
   create mask = 0600
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[media]
   comment = media
   path = /home/media
   read only = no 
   writeable = yes
   printable = no
   public = yes
   browseable = yes
   force user = xbmc 
   create mask = 0777   
   directory mask = 0777

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @lpadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by Morbius1 on 2010-04-16
Had you done a **testparm -s** in a terminal you would have gotten this error:
> ERROR: both 'wins support = true' and 'wins server = <server list>' cannot be set in the smb.conf file. nmbd will abort with this setting.Either one of them is for a multiple subnet network. Is that what you have because you also have this in that smb.conf:
    > domain logons = YesIs this just a simple home network with a linux, mac, and maybe a windows box in it. Or is it something more complicated?

And did you make a backup copy of your original smb.conf?

---

### Post by cdenley on 2010-04-16
Also, check filesystem permissions
```

ls -ld /home/media

```

---

### Post by adave on 2010-04-16
@Morbius.  I didn't know how to run a testparm.  But thanks for the heads-up.  Will make sure to do that going forward.  I don't have a multiple subnet network so I've commented those lines away.  I have also commented off domain logons = yes.  I have a simple home network with a linux, mac and windows machine.  Yes, I made a backup of my smb.conf

After commenting off those lines I still can't write to the SMB folder.

@cdenley.  I checked the permissions filesystem permissions on the home/media folder and here is what I get

drwxr-xr-x 7 root root 4096 2010-04-16 14:56 /home/media (in blue)

---

### Post by cdenley on 2010-04-16
> **adave said:**
> @cdenley.  I checked the permissions filesystem permissions on the home/media folder and here is what I get

drwxr-xr-x 7 root root 4096 2010-04-16 14:56 /home/media (in blue)

Only root is permitted to write in that directory.
```

sudo chmod -R a+rwX /home/media

```

---

### Post by adave on 2010-04-16
> **cdenley said:**
> Only root is permitted to write in that directory.
```

sudo chmod -R a+rwX /home/media

```

That worked!  Thanks for all your help.  I'm fairly new to the Linux world but am already loving it.

---

### Post by blackhawx on 2010-05-29
actually if the files are in a directory you created, just learn to do stuff like this in the terminal...
 
```

chmod 777 /home/yourname/Desktop/thefolderyouwanttochange

```
 
You really dont need to sudo (play as root), as this is not a safe practice to do anyway. So if you create the folders - then you set your rules.

---


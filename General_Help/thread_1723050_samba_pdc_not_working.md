---
title: "samba pdc not working"
date: 2011-04-06
forum: General Help
---

### Post by crash893 on 2011-04-06
Hey all, I had a server running 8.04 lts running samba to both share drives and to act as the primary domain contorler

the server died and i updated to 10.04lts with samba 3.4 i have a copy of the smb.conf but thats all i have.


The problems im running into are 1) I can get into any folder thats shared (I can see them) 

and 2) I can't add any of my windows based laptops to the domain (win xp)


this is a copy of my current smb.conf is there anything that im doing wrong or has changed from samba2 -> samba 3



```
[global]

   workgroup = MARKON40

   netbios name = MARKON40-PDC

   server string = %h server (Samba, Ubuntu)



   security = user
   os level = 255
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts bind dns
   domain logons = yes
   preferred master = yes
   wins support = yes

   smb ports = 139
   hosts allow = 192.168.40.
   bind interfaces only = true
   interfaces = 192.168.40.40

   encrypt passwords = true

   logon drive = H:

   # LEAVE LOGON PATH EMPTY OR ELSE PROFILES WILL MOVE TO THE SERVER
   logon path =
   logon script = 
   logon home = \\%L\%U

   directory mask = 0750
   create mask = 0750
   follow symlinks = no


   # Useradd scripts
   # add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   add user script = /usr/sbin/useradd -m '%u' -g users -G users
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usernod -G %g %u

   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000
   template shell = /bin/bash

   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat debug = yes
   unix password sync = yes


   # set the loglevel
   log file = /var/log/samba/smbd-%U.log
   log level = 3


########
#  BEGIN BUILT-IN SAMBA / NT SPECIAL SHARES
#  These files are 'managed' by the
#  MARKON network admins, and are handled by
#  SAMBA.
#########


[homes]

        comment = Home
        path = /home/%S/smbhome
        browseable = no
        writable = yes
        read only = no

        veto files = /.recycle/
        vfs objects = recycle
                recycle:keeptree=True
                recycle:versions=True
                recycle:touch=True
        hide dot files = yes

        force directory mode = 0770
        force create mode = 0660
        force group = grp-it

        valid users = @grp-it, %S
        invalid users =


[netlogon]

        path = /home/0-samba/netlogon
        browseable = no
        read only = yes
        public = no

########
#  BEGIN WORKGROUP SHARES SECTION
#  These files are 'owned' by
#  specific workgroups, and access
#  is limited.
#  Security must be maintained here!
#########


[home]
	comment = Backup Drive
	path = /home
	browsable = no
	writeable = no
	write list = @grp-it
	read only = yes
	
	veto files = /.recycle/
	vfs object = recycle
	        recycle:keeptree=True
                recycle:versions=True
                recycle:touch=True
        hide dot files = yes

        force directory mode = 0770
        force create mode = 0660
        force group = grp-it

        valid users = @grp-it
        invalid users =

[it]

        comment = IT Drive
        path = /home/0-samba/it
        browseable = no
        writeable = yes
        write list = @grp-it
        read only = no

        veto files = /.recycle/
        vfs object = recycle
                recycle:keeptree=True
                recycle:versions=True
                recycle:touch=True
        hide dot files = yes

        force directory mode = 0770
        force create mode = 0660
        force group = grp-it

        valid users = @grp-it
        invalid users =


[woodbridge]

        comment = WOODBRIDGE
        path = /home/0-samba/woodbridge
        browseable = yes
        writeable = yes
        write list = @grp-woodbridge
        read only = no

        veto files = /.recycle/
        vfs object = recycle
                recycle:keeptree=True
                recycle:versions=True
                recycle:touch=True
        hide dot files = yes

        force directory mode = 0770
        force create mode = 0660
        force group = grp-woodbridge


        valid users = @grp-woodbridge
        invalid users =




[public]

        comment = Public
        path = /home/0-samba/public
        browseable = yes
        writeable = yes
        write list = @grp-users
        read only = no

        veto files = /.recycle/
        vfs object = recycle
                recycle:keeptree=True
                recycle:versions=True
                recycle:touch=True
        hide dot files = yes

        force directory mode = 0770
        force create mode = 0660
        force group = grp-users

        valid users = @grp-users
        invalid users = wins support = no
```

---


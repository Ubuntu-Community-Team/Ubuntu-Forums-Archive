---
title: "cannot see self in nautilus-network"
date: 2010-01-17
forum: General Help
---

### Post by ultratek on 2010-01-17
i cannot see myself in nautilus-network using same pc/ubuntu but i can see others
i have included wins in the nsswitch.conf and enabled wins support in smb.conf so i may see these pcs and myself evertime my pc see starts

```
[global]
   workgroup = LXHOME
   netbios name = razertek
   server string = Samba Server
   wins support = yes
   dns proxy = no
   name resolve order = wins lmhosts hosts bcast
   interfaces = eth0
   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   domain logons = yes
   logon path = \\%N\profiles\%U
   logon path = \\%N\%U\profile
   logon drive = H:
   logon home = \\%N\%U
   add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
   add group script = /usr/sbin/addgroup --force-badname %g
   load printers = yes
   printing = bsd
   printcap name = /etc/printcap
   printing = cups
   printcap name = cups
   domain master = auto
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash
   winbind enum groups = yes
   winbind enum users = yes
   usershare max shares = 100
   usershare allow guests = yes
[Documents]
   comment = Documents Directories
   path = /home/razertek/Documents
   browseable = yes
   read only = no
   guest ok = yes
   force user = razertek
[Pictures]
   comment = Pictures Directories
   path = /home/razertek/Pictures
   browseable = yes
   read only = no
   guest ok = yes
   force user = razertek
[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
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
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = root, @lpadmin

```

---


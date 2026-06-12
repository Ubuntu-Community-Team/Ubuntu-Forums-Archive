---
title: "Sharing music with windows computers -- anonymous access"
date: 2006-04-23
forum: General Help
---

### Post by justinjstark on 2006-04-23
I currently have a shared folder set up for my music on my ubuntu machine and am able to access it on my windows machine (with my username and password).  But I would like anonymous read-only access to my music directory.  How do I go about this?

---

### Post by Nikusan on 2006-04-23
[QUOTE=blaksaga]I currently have a shared folder set up for my music on my ubuntu machine and am able to access it on my windows machine (with my username and password).  But I would like anonymous read-only access to my music directory.  How do I go about this?[/QUOTE]

Try editing your smb.conf file to look like this:

```
sudo gedit /etc/samba/smb.conf
```

```
[global]
security = share
workgroup = foo
netbios name = bar

[music]
path = /path/to/music
available = yes
browseable = yes
public = yes
guest ok = yes
writable = no
```

The important lines are security = share and guest ok = yes. Hope this helps.

---

### Post by justinjstark on 2006-04-23
Thanks, that works great.

But what are all of these extra lines in the samba config which ones do I need to keep?

```
[global]
  workgroup = MSHOME
  server string = %h (Ubuntu/Justin)
  log file = /var/log/samba/log.%m
  max log size = 1000
  syslog = 0
  panic action = /usr/share/samba/panic-action %d
  security = share
  username map = /etc/samba/smbusers
  encrypt passwords = true
  passdb backend = tdbsam guest
  obey pam restrictions = yes
  invalid users = root
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
  load printers = yes
  socket options = TCP_NODELAY
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

[homes]
comment = Home Directories
browseable = no
writable = no
create mask = 0700
directory mask = 0700

[Music]
path = /home/blaksaga/Media/Music
available = yes
browseable = yes
public = yes
guest ok = yes
writable = no
```

---


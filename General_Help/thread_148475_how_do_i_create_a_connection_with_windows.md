---
title: "how do i create a connection with windows"
date: 2006-03-22
forum: General Help
---

### Post by sebweb on 2006-03-22
i have looked at the samba tutorials and they are not working so can someone just tell me instead of linking me to a tutorial

---

### Post by NewWithoutClue on 2006-03-22
if what i think you want to do is correct.. i would do this...
```
#apt-get install smbfs
# mount -t smbfs //192.168.123.456/NetworkShareName /mount/point
```
Depending on your share set up on teh widnows side.. you will be aksed for a password.. I can just use any password ( i know i know, UNSAFE ).. after that.. you can read/write to the mount point.. i hope you understand mount atleast.

p01n7

---

### Post by gibson on 2006-03-22
are you tring to connect to windows you you can access shares from ubuntu or do you want your windows machine to access shares hosted on ubuntu.

Be more specfic

have you added the line to your smb.conf?

```
allow hosts = 192.168.1. 127.0.0.1
```

but tailored for your network obviously

here is my samba conf... i use it so share videos with my media center..

```
[global]


   workgroup = WORKGROUP

  allow hosts = 192.168.1. 127.0.0.1

   dns proxy = no

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   security = share

   encrypt passwords = true

   passdb backend = tdbsam guest

   obey pam restrictions = yes

   invalid users = root

   socket options = TCP_NODELAY


wins support = no


[videos]
path = /media/videos
available = yes
browseable = yes
guest ok = yes
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
```

---


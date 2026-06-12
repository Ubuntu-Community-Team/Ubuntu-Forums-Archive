---
title: "help with samba shares"
date: 2009-10-17
forum: General Help
---

### Post by artik1024 on 2009-10-17
Hi ! I need little help ;)

I got 2 PCs, a normal PC with ubuntu (login : **artik**), and the other : a debian server with samba installed on it.

I created a share, and when I list the folder :

```
drwxrwxr-- 2 artik samba     4096 Oct 17 00:34 alt.binaries.movies.zeromovies
drwxrwxr-- 2 artik samba     4096 Oct 17 00:34 alt.binaries.x
drwxrwxr-- 2 artik samba     4096 Oct 17 00:58 done
drwxrwxr-- 8 artik samba     4096 Oct 17 00:29 nzb
```

Here is my smb.conf:

```
#======================= Global Settings =======================

[global]


   workgroup = BANQUISE
   server string = %h server (Samba %v)
   log file = /var/log/samba/log.%m
   log level = 1
   max log size = 1000
   syslog = 0
   security = user
   encrypt passwords = true
   panic action = /usr/share/samba/panic-action %d

   socket options = TCP_NODELAY SO_RCVBUF=16384 SO_SNDBUF=16384

local master = yes
os level = 80
domain master = no
preferred master = auto

wins support = yes
dns proxy = no

obey pam restrictions = yes


#======================= Share Definitions =======================

[homes]
   comment = Exposezvous
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.

[artik-server]
        comment =
        path = /home/artik
        security = user
        public = yes
        create mask = 0770
        directory mask = 0770
        force user = artik
        force group = samba
        writeable = yes
```

From my ubuntu Pc, I can browse the shared folder, but impossible to mount or automount it. Here is my fstab :

```
//192.168.0.1/artik-server  /home/artik/samba/home-artik    cifs    username=artik,password=mangoo,workgroup=BANQUISE,uid=artik,auto    0       0

```

when I try to mount it :

```
root@artik-desktop:/home/artik# mount //192.168.0.1/artik-server
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
root@artik-desktop:/home/artik# 

```

Someone to help me ?

---

### Post by AmsterdamMack on 2009-10-17
Hi,

I'm a very new to this, but I think you gave the answer yourself in the smb.conf:

> # By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask _**is set to 0700 for security reasons**_. If you want to
# create files with group=rw permissions, _**set next parameter to 0775**_.

# Directory creation mask **is set to 0700 for security reasons**. If you want to
# create dirs. with group=rw permissions, _**set next parameter to 0775.**_

[artik-server]
        comment =
        path = /home/artik
        security = user
        public = yes
        create mask = 0770
        directory mask = 0770
        force user = artik
        force group = samba
        writeable = yes
Hope that helps,

M

---

### Post by artik1024 on 2009-10-17
Oh AmsterdamMack ! You helped me a lot, thx !!
Something, when you read too much things to solve your problem, you forget the most simple things =)
I can delete / create / list ... now

Everything seems to work ;)

---


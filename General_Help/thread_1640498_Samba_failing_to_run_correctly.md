---
title: "Samba failing to run correctly"
date: 2010-12-07
forum: General Help
---

### Post by Alpaca? on 2010-12-07
Hey guys, been pulling my hair out over this one.


I've been following this samba tutorial: 

[http://www.linux.com/learn/tutorials/305771-quick-and-dirty-samba-setup](http://www.linux.com/learn/tutorials/305771-quick-and-dirty-samba-setup)

Whenever I run testparm, I get this:

```
Traceback (most recent call last):
  File "/usr/bin/testparm", line 43, in <module>
    import samba
  File "/usr/lib/python2.6/dist-packages/samba/__init__.py", line 45, in <module>
    from samba._ldb import Ldb as _Ldb
ImportError: /usr/lib/libgensec.so.0: undefined symbol: _dcerpc_binding_handle_data
```Here's what my smb.conf looks like:

```

# Global parameters
[global]
       workgroup = WORKGROUP
       netbios name = luke-baseplate
       server string = Samba Server %v
       map to guest = Bad User
       log file = /var/log/samba/log.%m
       max log size = 50
       socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
       preferred master = No
       local master = No
       dns proxy = No
       security = User

# Share
[Data]
       path = /media/data
       valid users = luke
       read only = No
       create mask = 0777
       directory mask = 0777

```I'm trying to connect my linux box to my windows 7 machine, if that changes anything.

Thanks!

EDIT:

Also, when I run "samba" I get this:

```

Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
[Tue Dec  7 22:12:07 2010 EST, 0 ../smbd/server.c:374:binary_smbd_main()]
samba version 4.0.0alpha12-GIT-UNKNOWN started.
Copyright Andrew Tridgell and the Samba Team 1992-2010

```

---


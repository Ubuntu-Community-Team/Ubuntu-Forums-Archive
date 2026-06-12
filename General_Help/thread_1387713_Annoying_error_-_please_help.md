---
title: "Annoying error - please help"
date: 2010-01-22
forum: General Help
---

### Post by SpriteSODA on 2010-01-22
Hi guys,
It's becoming pretty frequent that I get this error when I attempt to launch any gnome application:
```
GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
```

The bizarre thing is that it doesn't happen straight away, only after a few hours using the OS.

Any thoughts?

Thanks.

---

### Post by pwnst*r on 2010-01-22
One thought is that you'd be better off posting here:  [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by Daisuke_Aramaki on 2010-01-22
You trying to launch a gui app as root by any chance?

---

### Post by SpriteSODA on 2010-01-22
nope, not doing anything as root

---

### Post by ibuclaw on 2010-01-22
Moved to General Help.

---

### Post by ibuclaw on 2010-01-22
Two things you can try:

Firstly,
```
rm -rf ~/.dbus/session-bus
```
and Logout/Login.

If that doesn't work, try
```
sudo touch /forcefsck
```
and Reboot.

Regards
Iain

---

### Post by SpriteSODA on 2010-01-25
none seems to do the trick, any more ideas?

---

### Post by SpriteSODA on 2010-02-02
bump

---


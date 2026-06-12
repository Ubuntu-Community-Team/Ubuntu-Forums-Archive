---
title: "gedit error"
date: 2010-05-09
forum: General Help
---

### Post by andrewjs18 on 2010-05-09
getting this error when I try to use gedit to open and edit a file through terminal:

(gedit:4423): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed 

I'm using ubuntu 10.04.

---

### Post by LoneWolfJack on 2010-05-09
whats the exact command you are using in terminal?

---

### Post by andrewjs18 on 2010-05-09
> **LoneWolfJack said:**
> whats the exact command you are using in terminal?

first I browse to this directory:
cd /home/var/www then I do:
sudo gedit index.html


and it's throwing the error, but it opens the file and allows me to edit it and do whatever.

---

### Post by LoneWolfJack on 2010-05-09
my first guess was that you are trying to edit a file on a network device, but this obviously isn't the case.

I did a quick search on google and it appears that this is a well known bug that pops up with several applications and has been fixed time and again.

I'd say lucid introduced a new bug (at least for you) and I would tend towards just ignoring it.

---

### Post by andrewjs18 on 2010-05-09
> **LoneWolfJack said:**
> my first guess was that you are trying to edit a file on a network device, but this obviously isn't the case.

I did a quick search on google and it appears that this is a well known bug that pops up with several applications and has been fixed time and again.

I'd say lucid introduced a new bug (at least for you) and I would tend towards just ignoring it.

it wasn't a huge deal to me, but I wanted to make sure I didn't screw something up.  aside from that, I forgot about nano, so I'll probably just use it from here on out...thanks!

---

### Post by alphacrucis2 on 2010-05-09
> **andrewjs18 said:**
> it wasn't a huge deal to me, but I wanted to make sure I didn't screw something up.  aside from that, I forgot about nano, so I'll probably just use it from here on out...thanks!

One thing is that you should not use sudo to run gnome applications. The proper way to do it is:

```
gksu gedit
```

---


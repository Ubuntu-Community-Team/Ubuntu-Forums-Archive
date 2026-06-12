---
title: "Unable TO Connect To Ubuntu IRC Channels"
date: 2010-05-21
forum: General Help
---

### Post by Vitamin-Carrot on 2010-05-21
Hey Guys,

For some strange reason when I try to access the #ubuntu channel on irc.freenode.net using the default settings within Xchat I receive the following -

* Looking up irc.freenode.net
* Connecting to irc.freenode.net (32.1.20.24) port 6667...
* Connection failed. Error: Connection timed out

I can connect to other servers and channels fine just not this one

:confused:

Oh and is there a way to get DockbarX working within Avant Window Navigator 0.4.0?

Cheers in advance

---

### Post by Iowan on 2010-05-21
> **Vitamin-Carrot said:**
> Hey Guys,

For some strange reason when I try to access the #ubuntu channel on irc.freenode.net using the default settings within Xchat I receive the following -

* Looking up irc.freenode.net
* Connecting to irc.freenode.net (32.1.20.24) [COLOR="Red"]port 6667[/COLOR]...
* Connection failed. Error: Connection timed out

I can connect to other servers and channels fine just not this one

:confused:
Try it using port 8001
Under XChat>Network List, Highlight "Ubuntu Server" and click Edit. Mine has > irc.ubuntu.com/8001While there, you can add which channels you'd like to join. Have you registered your nickname?

---

### Post by robvas on 2010-05-21
Have you tried the web client for Freenode?

[http://webchat.freenode.net/](http://webchat.freenode.net/)

---

### Post by Vitamin-Carrot on 2010-05-22
DNS was resolving irc.freenode.net incorrectly
restarting it fixed the issue

/me kicks silly Dlink modem

---


---
title: "Use remmina to connect to a windows server"
date: 2012-04-29
forum: General Help
---

### Post by jlane01 on 2012-04-29
Any ideas how to use remmina to connect to a windows server 2008 that uses terminal services with NLA security?  From windows vista & windows 7 I would just open the RDP client and type in rdp.address.com and would then be directed to enter in my username and password.  I have been unable to find any good instructions on using remmina & freerdp.  I read enough to know that freerdp should be able to help me, but I need some further assistance to get this worked out.  

I can install vista using virtualbox and do it that way, but there has to be a way to do this with linux I would think.

---

### Post by nothingspecial on 2012-04-30
Question moved to it's own thread

---

### Post by CharlesA on 2012-04-30
IIRC, you cannot use NLA and connect from an RDP client that doesn't support it.

You would have to have it set to "Allow connections from computers running any version of Remote Desktop (less secure)" in order to connect from XP or A *nix box.

EDIT: nothingspecial you beat me to it. ;)

---

### Post by jlane01 on 2012-05-01
I thought that newer versions of freerdp are working on NLA support?

---

### Post by CharlesA on 2012-05-01
> **jlane01 said:**
> I thought that newer versions of freerdp are working on NLA support?
Looks like it does.
[http://sourceforge.net/mailarchive/message.php?msg_id=26957118](http://sourceforge.net/mailarchive/message.php?msg_id=26957118)

[http://www.freerdp.com/](http://www.freerdp.com/)

---

### Post by Mugatu on 2012-09-12
[http://askubuntu.com/q/86148/18665](http://askubuntu.com/q/86148/18665)

---


---
title: "Problem running custom reboot command"
date: 2009-08-19
forum: General Help
---

### Post by ectospasm on 2009-08-19
If I want a command ("date >> /var/log/uptime") to run right before I reboot or halt, how do I get this to work?  I tried adding the command to do_stop () in both /etc/init.d/reboot and /etc/init.d/halt, but when I went to the GNOME session menu and chose "Restart...", /var/log/uptime had not been created once I rebooted (I have not tested the halt functionality).  

How do I get this working?  I guess all I would need to do is ensure the /etc/init.d scripts run when I click <user>/Restart... (or Shutdown...), but I've searched through gconf-editor and I don't see anything that mentions reboot or restart.  Any ideas?

---

### Post by P4man on 2009-08-21
If you dont mind a longish read, it could be worth spending a bit of time reading this:

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

---

### Post by ectospasm on 2009-08-21
> **P4man said:**
> If you dont mind a longish read, it could be worth spending a bit of time reading this:

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

Yep, that's what people have told me to do.  Of course, that is really useful if I wanted to start a daemon on shutdown, but I've adapted it so there are /etc/rc{0,6}.d/S80uptime links.  I have yet to test it because of another issue.  That and I like my uptime.

---


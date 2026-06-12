---
title: "Where the @#$% has gdm.conf gone?"
date: 2011-01-26
forum: General Help
---

### Post by styne on 2011-01-26
Hi,

I'm running Ubuntu 10.10 with GDM 2.30. I'm trying to setup x11vnc and xrdp so that I can connect to a new or existing session from Windows.

The guide I'm following is [http://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdp]("http://ubuntuforums.org/showthread.php?t=1168264&highlight=xrdp").

I'm trying to get x11vnc to start on boot before there is a session. To do this I tried following [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager").

Now I'm trying to set KillInitClients=false in the [daemon] section of /etc/X11/gdm/gdm.conf (or /etc/gdm/gdm.conf, etc.) to try and avoid a potential problem.

Where the heck is gdm.conf? Has this file moved?

Please help me find where I can set this property.

Thanks :)

---

### Post by kerry_s on 2011-01-26
/etc/dbus-1/system.d/gdm.conf

/etc/init/gdm.conf

---

### Post by cipherboy_loc on 2011-01-26
From an Ubuntu 10.04 LTS LiveCD:

> ubuntu@ubuntu:/etc/gdm$ locate gdm.conf
/etc/dbus-1/system.d/gdm.conf
/etc/init/gdm.conf
/var/lib/dpkg/info/gdm.conffiles
/var/lib/dpkg/info/gdm.config


Edit: Never mind about this part.
Cipherboy

---

### Post by styne on 2011-01-27
Thanks everyone for your feedback. /etc/init/gdm.conf looks like the most relevant one although it looks quite different to the old one. E.g. no [daemon] section. Hmmm...

---

### Post by krunge on 2011-01-27
> **styne said:**
> Thanks everyone for your feedback. /etc/init/gdm.conf looks like the most relevant one although it looks quite different to the old one. E.g. no [daemon] section. Hmmm...
BTW, if you x11vnc version is 0.9.9 or later, it tries to avoid being killed by gdm and so you don't need KillInitClients=false (which gdm has removed.)

[INDENT][http://www.karlrunge.com/x11vnc/index.html#beta-test](http://www.karlrunge.com/x11vnc/index.html#beta-test)
[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

---


---
title: "(LTSP) Serial Mouse Support?"
date: 2006-05-30
forum: General Help
---

### Post by mr.diogo.schneider on 2006-05-30
Does LTSP support serial mouses? I'm running it, but only with PS/2 clients. When I try to connect from a serial-mouse client I get no mouse at all. Is there a way to support serial mouses with LTSP? I did the standard installation, according to [http://wiki.ubuntu.com/ThinClientHowto](http://wiki.ubuntu.com/ThinClientHowto)

Thanks!

---

### Post by Joxy on 2007-11-05
I have the same problem. Does anyone have a solution?

---

### Post by ernierasta on 2008-01-17
This is for ubuntu 7.10:
(for older ltsp releases it will be /opt/ltsp/i386/etc/lts.conf)
You have to create:
/var/lib/tftpboot/ltsp/i386/lts.conf

and there put something like:
# Mouse configuration
X_MOUSE_DEVICE          = /dev/ttyS0
X_MOUSE_PROTOCOL        = Microsoft
X_MOUSE_EMULATE3BTN     = True
X_MOUSE_ZAXISMAPPING    = 4 5 6 7

Sometimes mouse resolution had to be changed (not in my case):
X_MOUSE_RESOLUTION      = 60

restart client machine

I hope it will help someone.

Leszek

---


---
title: "Need help removing Xgl"
date: 2006-04-04
forum: General Help
---

### Post by Zeroangel on 2006-04-04
Xgl has been causing a myriad of X restarts, CPU spikes, and movie playing problems ever since I installed it, So I tried removing it using the following:

- Removing /usr/bin/thefuture from gnome sessions
- Removing the flags "AllowGLXwithComposite" and "RenderAccel" from /usr/X11/xorg.conf
- Uninstalling the package xserver-xgl using apt-get

But now X complains that it can't start because it can no longer find the package Xgl (and then I have to finish startup using 'startx'). Can anyone help me finish uninstalling it so I can get back to my stable desktop experience?

---

### Post by Seq on 2006-04-04
I'd think it was in your /etc/gdm/gdm.conf-custom [servers] section

---

### Post by Zeroangel on 2006-04-04
That's what did it. Thanks :KS

It's good to be back to the familiarity and stability of Metacity.

---


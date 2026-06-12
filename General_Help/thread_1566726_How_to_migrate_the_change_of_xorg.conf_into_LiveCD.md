---
title: "How to migrate the change of xorg.conf into LiveCD"
date: 2010-09-02
forum: General Help
---

### Post by chang5562 on 2010-09-02
I disabled the Ctrl-Alt-Fn combination keystrokes from changing virtual terminals.  I added option "DontVTSwitch" to the /etc/X11/xorg.conf. However, it only changed the local version (on harddrive) after reboot.  After I used the remastersys to create a LiveCD, xorg.conf of LiveCD rollbacked to the original format (i.e without DontVTSwitch).  How can I migrate the change of xorg.conf to the LiveCD permanently?

---


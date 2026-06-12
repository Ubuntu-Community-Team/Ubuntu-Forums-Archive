---
title: "launching firefox over ssh"
date: 2009-12-08
forum: General Help
---

### Post by danode on 2009-12-08
hi all, im trying to start firefox over ssh like this:

firefox --display=:0.0 &

It works, i see firefox on the screen, but also a dialog window containing this error 5 times over:

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Not running within active session)

i read about a possible solution here: 
[http://ubuntuforums.org/showthread.php?t=1144756](http://ubuntuforums.org/showthread.php?t=1144756)

but it did not work for me.

Im running ubuntu 9.04

best regards
Daniel

---

### Post by gradinaruvasile on 2009-12-08
Have you tried just firefox? (connect with "ssh -X user@ip").

Also, firefox (and openoffice) is really heavy on remote launching even over LAN. Consider using a lighter browser such as Chromium or Midori.

---


---
title: "Sux doesn't work"
date: 2011-02-05
forum: General Help
---

### Post by janarene on 2011-02-05
For the last few Ubuntu versions, the utility 'sux' hasn't worked under any desktop that I've tried.  I type sux, and yes I'm root.  But when I try to run QT or GTK apps it fails.  Here are error messages I get under KDE calling Kate and then Gedit:

root@Cleo:/home/janarene# kate /etc/fstab
kate(20442): Session bus not found 

KCrash: Application 'kate' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/root/.kde/socket-Cleo/kdeinit4__0
Warning: connect() failed: : No such file or directory
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi directly
drkonqi(20443): Session bus not found 

>>insert hmmmm here<<<

root@Cleo:/home/janarene# gedit /etc/fstab
Xlib:  extension "RANDR" missing on display ":0.0".
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.1/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted
root@Cleo:/home/janarene#

Does anyone know the fix to this?  sux used to be one of my favorite utilities - used to work GREAT when ssh'd into a remote machine.

TIA!!

---

### Post by janarene on 2011-02-07
bump

---


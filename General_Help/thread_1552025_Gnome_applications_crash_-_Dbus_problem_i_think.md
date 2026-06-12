---
title: "Gnome applications crash - Dbus problem i think"
date: 2010-08-13
forum: General Help
---

### Post by sciff90 on 2010-08-13
Everything has been running fine lately but suddenly every now and then applications freeze. These are usually gnome based apps like rhythymbox totem etc. Also teh volume control from my keyboard stops working. This happens after being logged on for a short time. All the applications still run fine. 

Error message when i try to debug totem with totem --debug is

GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

all the errors I get seem to be related to dbus

any help would be appreciated thanks...

---

### Post by Peter09 on 2010-08-13
Hi,
what version of Ubuntu are you using?

---

### Post by sciff90 on 2010-08-13
I'm using 9.10

---

### Post by Peter09 on 2010-08-13
This appears to be a known bug, some reports suggest its been fixed, there are lots of variations on it so its difficult to tell exactly what the current situation is.

I would suggest that you enable 'backports' in your repository and see if there are any upstream changes here. Also some people seem to suggest that its a conflict in gstreamer plugins, might be worth checking that all the gstreamer plugins are installed.

---

### Post by sciff90 on 2010-08-13
here is the same problem i think..

[https://bbs.archlinux.org/viewtopic.php?pid=672675](https://bbs.archlinux.org/viewtopic.php?pid=672675)

---


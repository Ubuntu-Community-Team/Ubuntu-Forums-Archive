---
title: "where do I find *these* log files?"
date: 2011-10-20
forum: General Help
---

### Post by eltonw on 2011-10-20
Have things so drastically changed in Ocelot (11.10)? I've looked in /var/logs and I  *_CANNOT_ find*:
**dbus-monitor** and the **empathy-auth-client** log files...
:confused::confused::confused::confused:
I am having a problem connecting to the AIM client with Empathy 3.2.0. 
A bug report has been filed, but I need to find these log files.
SEE: [https://bugzilla.gnome.org/show_bug.cgi?id=662231](https://bugzilla.gnome.org/show_bug.cgi?id=662231)

---

### Post by mcduck on 2011-10-20
At least for Empathy, the log would definitely be somewhere in your home directory. As Empathy runs under your own user account, it wouldn't have write access anywhere else.

edit: this might help you: [http://live.gnome.org/Empathy/Debugging]("http://live.gnome.org/Empathy/Debugging")

---

### Post by btindie on 2011-10-20
Try with
```
$ sudo lsof | grep 'dbus-monitor'
```
If that doesn't return anything then the file isn't open.

---


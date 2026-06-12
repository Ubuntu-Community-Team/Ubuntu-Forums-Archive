---
title: "python and tasque over dbus"
date: 2010-01-02
forum: General Help
---

### Post by daspooky on 2010-01-02
hello folks,

I wrote a python script that connects to tasque over dbus, retrieves the number of tasks due today, and displays a notify-osd popup. It works fine, but the following issue is driving me crazy.

When the python script connects to dbus, and tasque is not yet running, it opens and shows the tasque window. I would prefer the script to do nothing if tasque is not running. This is the code I use to connect to dbus:

[B]try:
[INDENT]bus = dbus.SessionBus()[/INDENT]
[INDENT]obj = bus.get_object("org.gnome.Tasque", "/org/gnome/Tasque/RemoteControl")[/INDENT]
[INDENT]tasque = dbus.Interface(obj, "org.gnome.Tasque.RemoteControl")[/INDENT]
except dbus.exceptions.DBusException, e:
[INDENT]print "Could not connect to dbus"[/INDENT][/B]

Tasque gets opened by the part obj = bus.get_object.

Is there a way to check for the presence of a org.gnome.Tasque service on dbus, before actually getting the object?

---


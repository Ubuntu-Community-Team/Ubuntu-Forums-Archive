---
title: "gnome-do keeps crashing: dbus error?"
date: 2010-03-27
forum: General Help
---

### Post by jon.reeve on 2010-03-27
Gnome-do crashes every half hour or so. I get this message when I run it from a terminal: 

Unhandled Exception: System.Exception: Message body length mismatch: 15968 of expected 17135
at NDesk.DBus.Connection.ReadMessage () <0x00677>
at NDesk.DBus.Connection.Iterate () <0x0001c>
at NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x00031>
at (wrapper native-to-managed) NDesk.DBus.BusG/<Init>c__AnonStorey0.<>m__0 (intptr,NDesk.GLib.IOCondition,intptr) <0x0004d>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x0000a>
at Do.Do.Main (string[]) <0x0021e>

Anyone know what I can do to fix this? Or at least some kind of script that will auto-restart Do so I don't have to keep doing it myself?

---

### Post by jon.reeve on 2010-03-30
Commented on a bug report which sounds a lot like this issue: 

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/283573](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/283573)

although no one seems to be working on this bug. Should I revert to an older version of Do? An older version of DBus? Would reverting to an older version of Dbus mess up my system? 

Would love some advice on this, since restarting Do every fifteen minutes is really annoying, and I use Do heavily. 

What "message body length" is the output talking about?

---


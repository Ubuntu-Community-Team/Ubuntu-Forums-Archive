---
title: "dbus + gdm issue"
date: 2010-01-02
forum: General Help
---

### Post by rolandixor on 2010-01-02
I get this if I try to edit my gdm theme by doing sudo -u gdm gnome-appearance-properties

(gnome-control-center:24848): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Failed to connect to socket /tmp/dbus-jnT2fm0Mmt: Connection refused

(gnome-control-center:24848): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.

any idea how to fix it?

---

### Post by Ildanach on 2010-01-02
I had the same problem myself earlier. What I ended up doing was going back into the GUI (assuming you were in a virtual console) and did a run application command and typed in gnome-control-center. While I'm not totally certain that the two are one and the same, I'm pretty sure that's what you intended to open up. If you're changing your theme though, I'm not too certain how much it will help you, I'm trying the same thing and am at a dead end right now. Hope this helps.

---


---
title: "Questions About Running Firefox from My Terminal"
date: 2011-10-26
forum: General Help
---

### Post by w201 on 2011-10-26
When I run the command ***firefox*** my terminal stops working until I close firefox by using the mouse or pressing crtl+c (I discovered that one by accident) on the keyboard. Just wanting to know if that's normal or is there a command that I can issue to regain control of the terminal without having to close firefox.

Also, I don't know if this is of any significance but there are these same error codes every time I run the firefox command:

```
(firefox:2660): IBUS-WARNING **: Connect to  unix:abstract=/tmp/dbus-6R1PvGKKiX,guid=cef5bf35bf95cd83417e3a06000000b3  failed: Failed to connect to socket /tmp/dbus-6R1PvGKKiX: Connection  refused.

(firefox:2660): GLib-GObject-WARNING **:  /build/buildd/glib2.0-2.26.1/gobject/gsignal.c:1149: unable to lookup  signal "text-insert" for non instantiatable type `AtkText'
```

Thanks in advance for any suggestions.

---

### Post by nothingspecial on 2011-10-26
```
firefox &
```

---

### Post by philinux on 2011-10-26
Use.

firefox &

---

### Post by w201 on 2011-10-26
bangin' :guitar:

---


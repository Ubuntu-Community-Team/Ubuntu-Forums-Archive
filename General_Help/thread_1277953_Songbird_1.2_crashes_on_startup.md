---
title: "Songbird 1.2 crashes on startup"
date: 2009-09-28
forum: General Help
---

### Post by Brandma on 2009-09-28
Songbird refuses to start up for me.  Here's the result from trying to start it in terminal:
matt@brandma:~$ songbird
matt@brandma:~$ 
(crashreporter:18963): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

The only solution I could find on the web was 
```
[SIZE=3]sudo apt-get remove libvisual-0.4-plugins[/SIZE]
```...but I don't even have those plugins.

---


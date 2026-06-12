---
title: "System Config Printer Applet does not start (pynotify problem)...."
date: 2011-03-29
forum: General Help
---

### Post by Flukey on 2011-03-29
Hi all,

I'm running Maverick Meercat.

Whenever I try to run the Printers applet in System > Administration > Printing, it never actually initialises.

I did some digging around:

The applet is stored here: /usr/share/system-config-printer/applet.py

The command is here:  /usr/bin/system-config-printer-applet

When I execute this command, I get the following:
```

Traceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 53, in <module>
    pynotify.init('System Config Printer Notification')
AttributeError: 'module' object has no attribute 'init'
```

This also happens when I try to run the 'Guake' terminal application.

I have no idea what is causing this and I've been stuck on it for quite some time now. Any help is appreciated.

Thanks guys!

---


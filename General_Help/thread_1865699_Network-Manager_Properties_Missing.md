---
title: "Network-Manager Properties Missing"
date: 2011-10-20
forum: General Help
---

### Post by Wooodl on 2011-10-20
Hello

I'm using Ubuntu 10.04 netbook.
since a few days I have the following problem:

I can't start the window where I can change the properties of my network connections. But my netwokmanager is working. The applet is there and i have internet access. Just the properties window doesn't start. 

I already have un- and reinstalled networkmanager made a dist-upgrade , but nothing worked. What can I do?


Thanks a lot.

Woodl

---

### Post by crdlb on 2011-10-20
Try running ```
nm-connection-editor
``` in a terminal.

---

### Post by Wooodl on 2011-10-20
Thanks for the reply. If I do this I get:```
** (nm-connection-editor:1796): WARNING **: Icon nm-device-wired missing: Fehler beim Öffnen der Datei: Zu viele Ebenen aus symbolischen Links

** (nm-connection-editor:1796): WARNING **: Failed to initialize the UI, exiting...

```

"Fehler beim Öffnen der Datei: Zu viele Ebenen aus symbolischen Links" means: 
**Error during opening the file: To many levels of symbolic links.**

Don't know whether you speak german or not.

---

### Post by crdlb on 2011-10-20
It seems you have a recursive symlink in one of your icon theme directories. Are you using a custom icon theme? What happens if you use the 'GNOME' icon theme?

If it still happens in the GNOME theme, try this: ```

#!/usr/bin/env python

import gtk

theme = gtk.icon_theme_get_default()

window = gtk.Window()
window.set_default_size(100, 100)
pixbuf = theme.load_icon("nm-device-wired", 16, 0)
window.add(gtk.image_new_from_pixbuf(pixbuf))
window.show_all()

gtk.main()
```

It should fail just like nm-connection-editor. If so, run ```
strace python icontest.py 2>&1 | grep -v ENOENT | grep icons
``` It should be obvious where it is recursing (the path will be very long and repetitive).

---

### Post by Wooodl on 2011-10-21
Changing the Icons to Gnome fixed it. **Thank you!**

I was using the faenza icon-packeage before (they really look nice). Is there a way to use them anyway?

---


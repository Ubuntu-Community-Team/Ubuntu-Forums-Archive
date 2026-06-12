---
title: "Google Earth Doesn't Load Data"
date: 2010-02-28
forum: General Help
---

### Post by ld.4lpha on 2010-02-28
Jaunty on AMD64

This is going to freak me out:

I installed Google Earth from the repos a few months ago, and it has worked perfectly ever since...until today.  After firing it up today, the app comes up, but it won't load any data (see screenshot).

I ran it from terminal and the output follows:
```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

```I believe I remember seeing this same terminal output before also (when GE worked).  I did a little research on the ELF CLASS errors, but haven't found anything meaningful in terms of possible fixes for this problem.

I have completely removed and reinstalled the package from the repos to no avail.

Anybody have suggestions on what might be going on?

Muchas gracias,
LD

---

### Post by ld.4lpha on 2010-03-05
Deleted ~.config/Google and restarted GE.  Worked like a charm.

Not sure why ```
 sudo apt-get purge googleearth 
``` didn't take care of this.

:-k

---


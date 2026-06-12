---
title: "Another /usr/lib/libconf2/gconf-sanity-check exited with status 256"
date: 2009-12-31
forum: General Help
---

### Post by klausner on 2009-12-31
My 9.10 system suddenly refused to boot, as described in [this thread]("http://ubuntuforums.org/showthread.php?t=1366516").

So I got that fixed, but now I can't get Gnome to start! The system boots, and X starts, but no window manager. The error I get is:
> There is a problem with the configuration server
/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256

Tried suggestions to:
```
sudo chmod 755 /etc/gconf/gconf.xml.system
```

and I reinstalled Gnome panel and Gnome panel data.

Also ran
```
sudo chown -Rc 1000 /home/*myname*
```

Note, this last can be dangerous if you have files that are *supposed* to be owned by someone else.

None of this helped.

I've already had to reinstall Ubuntu once a week for the last several weeks to fix problems. Is there a more specific way to fix this?

---


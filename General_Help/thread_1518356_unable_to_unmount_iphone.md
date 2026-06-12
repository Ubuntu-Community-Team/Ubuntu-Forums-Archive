---
title: "unable to unmount iphone"
date: 2010-06-26
forum: General Help
---

### Post by miko5054 on 2010-06-26
DBus error org.freedesktop.DBus.Error.UnknownMethod: Method "Unmount" with signature "sou" on interface "org.gtk.vfs.Mount" doesn't exist


whats the problem ??

---

### Post by arobinson on 2010-12-09
I just experienced this in trying to unmount a sftp mounted directory in nautilus. Looks like the nautilus code is using deprecated/removed API in the DBus for the mount library.

I filed a bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/687697]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/687697")

---


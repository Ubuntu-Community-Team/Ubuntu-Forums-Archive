---
title: "HOWTO: mail-notification-evolution in Natty"
date: 2011-06-27
forum: General Help
---

### Post by frogotronic on 2011-06-27
Hello,

   Mail-Notification and Mail-Notification-Evolution does not work if installed from the Natty repos.

   There is a patch from Debian located here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617771](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617771)

   I've patched the Ubuntu debs (re-rolled) them on i386 Natty.  Please find them attached.  Uninstall the official debs and install these, and no I haven't solved the wrong applet background colour on dark themes.  That issue is the use of the eggtrayicon as opposed to the GTKTrayIcon code.

Cheers,
CH

---


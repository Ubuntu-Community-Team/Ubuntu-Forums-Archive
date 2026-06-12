---
title: "Package gdk-imlib missing from Karmic"
date: 2010-01-03
forum: General Help
---

### Post by Zill on 2010-01-03
I have a "binary" application (no deb or source code) that requires gdk-imlib.

Although this package has previously been available in Ubuntu, it appears to have been dropped from Karmic (9.10).

[http://packages.ubuntu.com/search?suite=all&arch=any&searchon=names&keywords=gdk-imlib]("http://packages.ubuntu.com/search?suite=all&arch=any&searchon=names&keywords=gdk-imlib")

Does anyone know why this has been dropped or if there are any plans to re-introduce it later?

Any ideas on a workaround in the meantime?

ps.  I have tried to install the Jaunty (9.04) deb but this fails due to unsatisfied dependencies and I don't wish to end up in "dependency hell" ;-)

Any help gratefully received.

---

### Post by Zill on 2010-01-11
I posted this question on Launchpad and show the answer here to help anyone who finds this thread later...
> It was removed due to removal of GTK 1.2 ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522810](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522810)), so it's not going back. Your options are: (1) ask whoever provided you with that application to build a new version which relies on GTK 2.0; (2) go back to a Jaunty system or install Jaunty somewhere (dual-boot, VM, chroot); (3) install necessary libraries on a Karmic system - this will require installing all dependencies (and dependencies of dependencies) of gdk-imlib, which you can take from a Jaunty release.
[https://answers.launchpad.net/ubuntu/+source/imlib/+question/96201]("https://answers.launchpad.net/ubuntu/+source/imlib/+question/96201")

---


---
title: "Update errors"
date: 2012-07-12
forum: General Help
---

### Post by dh04000 on 2012-07-12
The update manager is throwing an error about these packages being non-authenticated. They look like packages from the official ubuntu repo.

aptdaemon aptdaemon-data compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default gir1.2-pango-1.0 libdecoration0 libpango1.0-0 libpango1.0-0:i386 python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-aptdaemon.pkcompat

Thought someone should know.

---

### Post by drs305 on 2012-07-12
I tried "Update Manager" and via "apt-get update" using the *Main Server* repository and am not getting any errors (but perhaps mine are already up-to-date). Perhaps you could try switching repositories.

---

### Post by jfdk34 on 2012-07-12
Same here:

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Details:

aptdaemon aptdaemon-data compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default gir1.2-pango-1.0 libdecoration0 libpango1.0-0 libpango1.0-0:i386 python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-aptdaemon.pkcompat

---

### Post by dino99 on 2012-07-12
> **jfdk34 said:**
> Same here:

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Details:

aptdaemon aptdaemon-data compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default gir1.2-pango-1.0 libdecoration0 libpango1.0-0 libpango1.0-0:i386 python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-aptdaemon.pkcompat

are they genuine ubuntu packages or third party ppa ?
if they are genuine, then its a usual joke from update-manager (so buggy), either use apt-get or synaptic

---

### Post by dh04000 on 2012-07-13
The update issue has resolved itself today. I just updated the package list and it installed no problem.

---


---
title: "Audacity with 11.10"
date: 2011-10-16
forum: General Help
---

### Post by forez84 on 2011-10-16
Hello, I just updated my ubuntu to 11.10 and now when I try to run Audacity I get this:

:~$ audacity 

(Audacity:15052): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible

(Audacity:15052): Gnome-WARNING **: Accessibility: failed to find module 'libgail' which is needed to make this application accessible
**
ERROR:accessible.c:556:spi_accessible_construct: assertion failed: (o)
Aborted

:(

My original installation was ubuntu but then I installed KDE plasma workspace and kdm so not sure if that might be an issue.

...tried to install libgail-gnome-module from:
[http://packages.debian.org/lenny/libgail-gnome-module](http://packages.debian.org/lenny/libgail-gnome-module)
but install fails for dependency issues.

Any help is appreciated, thanks.

---

### Post by Toz on 2011-10-18
Its not a good idea to try to install debian lenny packages into kubuntu 11.10 - as you can see dependency and compatibility problems. If you search the Muon Package Manager, you will find 11.10-specific versions of libgail and libgail-common.

---

### Post by benteveo on 2011-12-26
I had the same problem and found a solution to it.

The spi_accessible_construct assertion failure is caused by an obsolete library: libatspi1.0-0

The way to untangle the mess is:

```

     sudo apt-get remove audacity audacity-data libportsmf0 libgail-common
     sudo apt-get autoremove
     sudo apt-get install audacity

```

The second (autoremove) line removed the offending dependency for me.

After that, installing audacity pulls the correct prereqs and audacity starts-up successfully without hitting the assertion.

HTH

---


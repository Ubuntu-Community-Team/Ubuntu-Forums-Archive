---
title: "Issue with Gimp PPA"
date: 2012-03-10
forum: General Help
---

### Post by cscj01 on 2012-03-10
I recently had a partial update that un-installed Gimp.  I use Matt Walker's PPA (mrw-gimp-svn for matthaeus123) to keep my Gimp as close to the latest as is reasonable.  The problem listed in Update Manager said that the PPA did not support changelogs.  In checking Matt's PPA, he said I needed to install the following sources:```
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu oneiric main

deb http://ppa.launchpad.net/ricotz/testing/ubuntu oneiric main
```

I did that and was able to install Gimp 2.7.5.  Now, every time I get updates (daily) I get two packages from Matt's PPA that are not selectable```
libgimp2.0
libgimp2.0-dev
```Does anyone have any idea why these keep appearing in Update Manager?  If I check Synaptic, it shows that they are installed and upgradable.  Should I remove those two packages or just ignore the appearance of theses two items with each update?

---

### Post by cscj01 on 2012-03-13
bump

---

### Post by mc4man on 2012-03-13
This is probably due to a dual dependency on libglib, one proper - libglib2.0-0 & one improper that shouldn't even be there - libglib2.0

This can be seen in the control file for libgimp - 
> Depends: libc6 (>= 2.11), libcairo2 (>= 1.2.4), libgdk-pixbuf2.0-0 (>= 2.22.0), [COLOR="Blue"]libglib2.0-0[/COLOR] (>= 2.30.2), libgtk2.0-0 (>= 2.24.0), libpango1.0-0 (>= 1.22.0), [COLOR="Red"]libglib2.0 [/COLOR](>= 2.30.2)

I notified the ppa owner the other day, hopefully he'll fix this 
(was caused by a bad entry in the source's debian control file

> Package: libgimp2.0
Architecture: any
Section: libs
Depends: ${shlibs:Depends}, ${misc:Depends}, [COLOR="Red"]libglib2.0[/COLOR] (>= 2.30.2)

---

### Post by cscj01 on 2012-03-16
> **mc4man said:**
> This is probably due to a dual dependency on libglib, one proper - libglib2.0-0 & one improper that shouldn't even be there - libglib2.0

This can be seen in the control file for libgimp - > Depends: libc6 (>= 2.11), libcairo2 (>= 1.2.4), libgdk-pixbuf2.0-0 (>= 2.22.0), Package: libgimp2.0
Architecture: any
Section: libs
Depends: ${shlibsepends}, ${miscepends}, libglib2.0 (>= 2.30.2) libglib2.0-0 (>= 2.30.2), libgtk2.0-0 (>= 2.24.0), libpango1.0-0 (>= 1.22.0), libglib2.0 (>= 2.30.2) 


I notified the ppa owner the other day, hopefully he'll fix this 
(was caused by a bad entry in the source's debian control file> Package: libgimp2.0
Architecture: any
Section: libs
Depends: ${shlibsepends}, ${miscepends}, libglib2.0 (>= 2.30.2) 
Thanks for the reply.  I'll close this.

---


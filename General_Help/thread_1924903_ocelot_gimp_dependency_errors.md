---
title: "ocelot gimp dependency errors"
date: 2012-02-13
forum: General Help
---

### Post by qwertyjjj on 2012-02-13
I get the following when trying to install gimp?
The following packages have unmet dependencies:

gimp: Depends: python-gtk2 (>= 2.8.0) but 2.24.0-2 is to be installed
      Depends: libc6 (>= 2.11) but 2.13-20ubuntu5 is to be installed
      Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
      Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
      Depends: libgs9 (>= 8.61.dfsg.1) but 9.04~dfsg-0ubuntu11.5 is to be installed
      Depends: libgtk2.0-0 (>= 2.24.0) but 2.24.6-0ubuntu5 is to be installed
      Depends: libgudev-1.0-0 (>= 147) but 1:173-0ubuntu4.1 is to be installed
      Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu2 is to be installed
      Depends: librsvg2-2 (>= 2.14.4) but 2.34.1-2 is to be installed
      Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

DO I have to sudo apt-get each of those?

---

### Post by jerrrys on 2012-02-14
What GIMP is this and what version (ubuntu) are you running?

I ask because of this:

[http://ubuntuforums.org/showthread.php?p=11687680#post11687680](http://ubuntuforums.org/showthread.php?p=11687680#post11687680)

---

### Post by qwertyjjj on 2012-02-14
> **jerrrys said:**
> What GIMP is this and what version (ubuntu) are you running?

I ask because of this:

[http://ubuntuforums.org/showthread.php?p=11687680#post11687680](http://ubuntuforums.org/showthread.php?p=11687680#post11687680)

just gimp from tghe repository, not sure which version it is trying to download but it is on Oneiric Ocelot

---

### Post by jerrrys on 2012-02-14
I installed gimp v2.x on oneiric without issue.  Did you update first?  Some have had problems with 64bit install.

---


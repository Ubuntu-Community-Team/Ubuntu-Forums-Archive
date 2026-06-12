---
title: "Gnome-Shell Install Issue"
date: 2011-03-14
forum: General Help
---

### Post by TheMixtureMedia on 2011-03-14
Hi there I am tring to install Gnome-Shell and it comes up with this error can someone help please.

gnome-shell:
 Depends: gir1.2-atk-1.0 (>=1.32) but it is not installable
 Depends: gir1.2-clutter-1.0 (>=1.4) but it is not installable
 Depends: gir1.2-freedesktop (>=0.9) but it is not installable
 Depends: gir1.2-gdkpixbuf-2.0  but it is not installable
 Depends: gir1.2-gtk-3.0  but it is not installable
 Depends: gir1.2-json-glib-1.0  but it is not installable
 Depends: gir1.2-mutter-2.91 but it is not going to be installed
 Depends: gir1.2-pango-1.0  but it is not installable
 Depends: gir1.2-telepathyglib-0.12  but it is not installable
 Depends: libclutter-1.0-0 (>= 1.5.15)
  Depends: libecal1.2-8 (>=2.32.2) but 2.32.1-0ubuntu1~ppa1 is to be installed
  Depends: libedataserver1.2-14 (>=2.32.2) but 2.32.1-0ubuntu1~ppa1 is to be installed
  Depends: libedataserverui1.2-11 (>=2.32.2) but 2.32.1-0ubuntu1~ppa1 is to be installed
 Depends: libgnome-desktop-3-0 but it is not going to be installed
 Depends: libgtk-3-0 (>=3.0.0) but it is not installable
  Depends: libpolkit-agent-1-0 (>=0.99) but 0.96-2ubuntu1 is to be installed
 Depends: mutter but it is not going to be installed
  Depends: gnome-settings-daemon (>=2.91.5.1) but 2.32.0-0ubuntu3.1 is to be installed
 Depends: gir1.2-gconf-2.0  but it is not installable
 Depends: gir1.2-gkbd-3.0 but it is not going to be installed
 Depends: gir1.2-polkit-1.0  but it is not installable
 Depends: gir1.2-upowerglib-1.0  but it is not installable

---

### Post by andrewthomas on 2011-03-14
As you found out it is not installable from the repo's.  The last I knew, the PPA was no good either.  I have been building it in my home directory with jhbuild.  See this post

[http://ubuntuforums.org/showthread.php?t=1603874](http://ubuntuforums.org/showthread.php?t=1603874)

---


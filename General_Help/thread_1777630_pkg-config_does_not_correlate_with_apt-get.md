---
title: "pkg-config does not correlate with apt-get"
date: 2011-06-08
forum: General Help
---

### Post by cmdematos on 2011-06-08
I have installed boo. There is nothing else to do, it is installed and visible in synaptic and apt, I can run in from bash.

However, pkg-config does not see it. When I --list-all | grep boo all I get is monodevelop-boo and no boo standalone.

boo is installed in /usr/lib/boo. I have tried setting PKG_CONFIG_PATH to /usr/lib and to /usr/lib/boo.

How does pkg-config work? Where does it get its list of packages from? and why do packages in apt not correlate with pkg-config?

---

### Post by cmdematos on 2011-06-08
Got it - pkgconfig reads package metadafiles (*.pc) in /usr/lib/pkfconfig. These files point out libraries, which normally require the development packages of a system-package installed (hence, boo-dev, not boo itself).

---


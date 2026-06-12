---
title: "Any way to get -devel packages installed automatically?"
date: 2006-04-03
forum: General Help
---

### Post by Nobber on 2006-04-03
Was just wondering: is there any way to ensure that whenever I install a package, any corresponding -devel package gets installed alongside it too, automatically?

This would be a bit of a timesaver for folks who like to build the odd package from source now and then. For example, if A depends on B, and I know I already have B installed, I could just go ahead and build A from source without worrying whether I have the B-devel package already installed.

---

### Post by az on 2006-04-03
sudo apt-get build-dep <package>
You need to have your deb-src repositories enabled.

---

### Post by Nobber on 2006-04-03
So if I wanted to build A from source, I would do

sudo apt-get build-dep A

first, and that would install all the -devel (and presumably the associated binary) packages required to build A?

Not automatic, but definitely handy - thanks for the tip!

---

### Post by Nobber on 2006-04-03
Now I'm wondering whether apt could be configured to run "apt-get build-dep A" on each package to be installed; it's already configured to run "dpkg-preconfigure" thanks to the line

**DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};**

in /etc/apt/apt.conf.d/70debconf, so why not? Hmm...

---


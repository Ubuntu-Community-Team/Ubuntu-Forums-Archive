---
title: "Building wine"
date: 2010-11-03
forum: General Help
---

### Post by xtheunknown0 on 2010-11-03
Hello!

I'm trying to build and install wine 1.1.41 on Karmic. I'm having trouble because I get this output:

configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.

near the end of an attempt to build wine.

When I typed

sudo apt-get install Xl

and pressed tab, I got no tab-completion!

So, what should I do to get past this error?

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2010-11-05
bump

---

### Post by xtheunknown0 on 2010-11-05
bump

---

### Post by mc4man on 2010-11-05
likely libx11-dev
(you could also run sudo apt-get build-dep wine1.2 to ck. on most of the  basic deps

Or use the team wine ppa for more recent versions
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---


---
title: "lekhonee-gnome won't install"
date: 2011-04-29
forum: General Help
---

### Post by MishMich on 2011-04-29
10.10 Maverick Meerkat

This won't install via Software Manager.  If I try in Synaptic, I get that it depends on:

python-gtkhtml2

Which is not available.  Looking in the packages, it looks like libGtkHTML3 is installed - but there is no python-gtkhtml available as 2 or 3.

The KDE version installs.

---

### Post by casbahdk on 2011-09-24
I have this problem in 11.04 Xubuntu. Did you ever get the problem sorted?```
The following packages have unmet dependencies:

lekhonee-gnome: Depends: python (>= 2.5) but 2.7.1-0ubuntu5 is to be installed
                Depends: python-gtkhtml2 but it is not going to be installed
```

---

### Post by Tekippie on 2011-10-09
I'm on Ubuntu 11.04 and the version in the repos refused to install. I  downloaded the tar with the newest version and tried to compile.  Naturally I had build-essential installed, but also after installing the  packages that ./configure found missing it wouldn't go. I got stuck on  the webkit package. Hit 21 brought me on a page with the solution:

sudo apt-get install libxml2-dev libsoup2.4-dev libgtksourceview2.0-dev libwebkit-dev libgtkspell-dev libgee-dev

Then it compiled fine :)

---


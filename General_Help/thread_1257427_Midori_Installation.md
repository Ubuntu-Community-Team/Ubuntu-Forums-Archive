---
title: "Midori Installation"
date: 2009-09-03
forum: General Help
---

### Post by ahop on 2009-09-03
I am trying to reinstall Midori on my laptop (running 9.04).  I get the below error:

```

Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

midori:
  Depends: libsoup2.4-1 (>=2.27.2) but 2.26.0-0ubuntu3 is to be installed
 Depends: libwebkit-1.0-2 (>=1.1.6) but it is not installable

```

Any thoughts on how to get this resolved?

---

### Post by DFlame on 2009-09-03
Tried [this](http://unixlab.blogspot.com/2009/07/installing-midori-on-ubuntu-jaunty.html)?

---

### Post by ad_267 on 2009-09-03
How are you installing Midori? From the PPA? If so, you also need the WebKit PPA: [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

---

### Post by ahop on 2009-09-03
I did have my sources.list updated.  I guess the missing step was step two of the linked document:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1

```

Works now.  Thanks!

---


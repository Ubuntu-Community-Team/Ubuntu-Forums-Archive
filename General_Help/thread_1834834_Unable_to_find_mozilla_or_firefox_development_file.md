---
title: "Unable to find mozilla or firefox development files"
date: 2011-08-28
forum: General Help
---

### Post by marcisim on 2011-08-28
Hi everybody!

I'm trying to install mplayerplug-in for firefox. After downloading the package [(http://mplayerplug-in.sourceforge.net/install.php]("http://mplayerplug-in.sourceforge.net/install.php")), and typed ./configure I get:


```
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
configure: Determining mozilla/firefox packages to build against
checking for pkg-config... /usr/bin/pkg-config
checking for mozilla-plugin mozilla-xpcom... configure: WARNING: mozilla-plugin not found
checking for firefox-plugin firefox-xpcom... configure: WARNING: firefox-plugin not found
checking for seamonkey-plugin seamonkey-xpcom... configure: WARNING: seamonkey-plugin not found
checking for xulrunner-plugin xulrunner-xpcom... configure: WARNING: xulrunner-plugin not found
checking for libxul... configure: WARNING: libxul not found
checking for iceape-plugin iceape-xpcom... configure: WARNING: iceape-plugin not found
configure: error: Unable to find mozilla or firefox development files


```Then I installed firefox-dev from synaptic, but I still get on getting the same error. Any suggestion?

Thank you!

---

### Post by ajgreeny on 2011-08-28
I would forget abut doing all that and simply install the gecko-mediaplayer from the repos.

---


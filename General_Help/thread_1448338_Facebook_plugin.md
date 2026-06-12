---
title: "Facebook plugin"
date: 2010-04-06
forum: General Help
---

### Post by louis.roux on 2010-04-06
Im trying to install a facebook plugin.  I downloaded file and it is on my desktop as "FacebookPlugin-1.0.3.tar.gz.  What do I do next???

---

### Post by jrider on 2010-04-06
Extract it. Cd into the directory. Make sure you have the Pidgin headers installed (you might need a devel package for your platform).  Run *make* to build the plugins for all platforms, *make libfacebook.dll* to build the plugin for Windows, *make libfacebook.so* to build the plugin for 32-bit Linux, *make libfacebook64.so* to build the plugin for 64-bit Linux, *make libfacebookarm.so* to build the plugin for ARM Linux (Nokia etc).  Run *make install* to install the plugin to the right directory.

[http://code.google.com/p/pidgin-facebookchat/wiki/How_To_Install](http://code.google.com/p/pidgin-facebookchat/wiki/How_To_Install)

---


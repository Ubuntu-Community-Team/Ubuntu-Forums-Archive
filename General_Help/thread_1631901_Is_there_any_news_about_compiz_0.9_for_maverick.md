---
title: "Is there any news about compiz 0.9 for maverick?"
date: 2010-11-27
forum: General Help
---

### Post by aviramof on 2010-11-27
When can we expect a new compiz 0.9 for maverick? it's been quite a long time since maverick was released and there are no updates in this ppa:
[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

Thanks in advance.

---

### Post by andrewthomas on 2010-11-27
Either install 0.9.2.1 from the natty repo (which only contains the main plugins) or compile from source [http://releases.compiz.org/0.9.2.1/](http://releases.compiz.org/0.9.2.1/)

```
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libboost-dev libboost-serialization1.42.0 cmake
```To compile from the source tarballs, extract each tarball and execute the following in each package directory:

While building with:
```
mkdir build && cd build
cmake .. 
# see note below about edit of CMakeCache.txt
make
sudo checkinstall
```After the cmake .. step you need to go into the build directory and edit the CMakeCache.txt file 
and change 
```
//Install path prefix, prepended onto install directories.
CMAKE_INSTALL_PREFIX:PATH=/usr/local
``` to ```
CMAKE_INSTALL_PREFIX:PATH=/usr
``` so ccsm can find the plugins. 

[http://wiki.compiz.org/Installation/Development](http://wiki.compiz.org/Installation/Development)

---

### Post by Decatf on 2010-11-27
There's a script right in the compiz git repo to compile and install it. See this post and the one right after it. [http://forum.compiz.org/viewtopic.php?t=12565#p77557](http://forum.compiz.org/viewtopic.php?t=12565#p77557)

---


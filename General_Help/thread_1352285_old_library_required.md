---
title: "old library required"
date: 2009-12-11
forum: General Help
---

### Post by H4F on 2009-12-11
I have I third party application (rumus2 -Forex)
to run this application I need the library libqt3-mt_3.3.8b-5+b1_i386.deb 
the current version of this library in ubuntu is XX which is greater.
Every time I add/update I have an error "Broken packages" which is giving me lots of trouble.

is there a way to keep both libraries ? like place them in diff directories and force the application use the old one ?

---

### Post by xifer on 2009-12-11
after extracting the library files from the package - copy them to a new location. e.g.
mkdir /lib/libqt3-mt_3
cp <your_libraries> /lib/libqt3-mt_3

in the startup script for your application set up environment variable

LD_LIBRARY_PATH=/lib/libqt3-mt_3:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH

oh yeah - and then make sure it doesn't get lost when you fix/revert/install/reinstall the latest version

---

### Post by H4F on 2009-12-11
I have libqt*.deb its a package which I have to install.
from the manual :
dpkg --instdir /old_libqt3
dpkg -i --instdir /home/*/.rumus/LD_Library --force-architecture

then
LD_LIBRARY_PATH=/lib/libqt3-mt_3:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH

right ?

---

### Post by xifer on 2009-12-14
> **H4F said:**
> I have libqt*.deb its a package which I have to install.
from the manual :
dpkg --instdir /old_libqt3
dpkg -i --instdir /home/*/.rumus/LD_Library --force-architecture

then
LD_LIBRARY_PATH=/lib/libqt3-mt_3:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH

right ?

Nearly - but there's a chance that the oldinstall will be removed after installing the new.

so to be sure
#assuming these are the old versions
dpkg --instdir /old_libqt3 
mkdir /lib/old_libqt3
cp /old_libqt3/* /lib/old_libqt3
# and these are the new packages- dont think you need instdir or force here - can use the default package name to install and no flags
dpkg -i /.rumus


then in your app startup script
LD_LIBRARY_PATH=/lib/old_libqt3:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH

---


---
title: "Installing 32 bit gtk2.0-0 on Ubuntu 12.04 64 bit"
date: 2012-09-30
forum: General Help
---

### Post by uilt on 2012-09-30
I've been trying to run Dwarf Fortress for Linux on my Ubuntu 12.04 64 bit machine. Unfortunately only a 32 bit binary exists. When I ran it, it threw:
```
./libs/Dwarf_Fortress: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
]
```I assumed I needed to install the 32 bit gtk 2 libraries, so I ran (since ia-32libs is now deprecated):
```
sudo apt-get install libgtk2.0-0:i386
```which returns:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libatk-wrapper-java-jni : Depends: libatk-wrapper-java (>= 0.30.4-0ubuntu2) but it is not going to be installed
 libgtk2.0-0 : Recommends: libgtk2.0-bin
               Breaks: libgtk2.0-0:i386 (!= 2.24.10-1oneiric6~ppa) but 2.24.10-0ubuntu6 is to be installed
 libgtk2.0-0:i386 : Depends: libpango1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Recommends: libgtk2.0-bin:i386
                    Breaks: libgtk2.0-0 (!= 2.24.10-0ubuntu6) but 2.24.10-1oneiric6~ppa is to be installed

```When using Synaptic, Synaptic asks me to remove all my programs that use gtk 2. It seems like this means I can't install 32 bit gtk2 and 64 bit gtk2 at the same time. So is there any way to get 32 bit gtk working without removing all my 64 bit gtk2 dependent programs, or is multiarch support too broken on precise to do so?

---


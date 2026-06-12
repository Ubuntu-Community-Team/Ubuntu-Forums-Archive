---
title: "GoogleEarth 6.2 crashes on Lucid"
date: 2012-03-12
forum: General Help
---

### Post by ofnuts on 2012-03-12
Just tried to upgrade from GE 5.x (from medibuntu) to GE 6.2. Uninstalled GE5. Downloaded the 32-bit .DEB from [http://www.google.com/earth/download/](http://www.google.com/earth/download/) and installed via kpackagekit
The new version doesn't work. When started from a terminal session:
```

Google Earth has caught signal 11.
We apologize for the inconvenience, but Google Earth has crashed.

```That point to a crash log text file which contains:
```

Major Version 6                                                                                                                        
Minor Version 2                                                                                                                        
Build Number 0001
Build Date Feb  3 2012
Build Time 15:28:07
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 32
OS Patch Version 0
Crash Signal 11
Crash Time 1331542207
Up Time 0.01657

Stacktrace from glibc:
./libgoogleearth_free.so(+0xc1583)[0xb76b9583]
./libgoogleearth_free.so(+0xc1703)[0xb76b9703]
[0xb7730400]
./libbase.so(_ZN5earth15GfxCardInfoUnixC1Ev+0x4a)[0xb500061a]
./libbase.so(_ZN5earth11GfxCardInfo12GetSingletonEv+0x44)[0xb5000664]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x2e)[0xb76c705e]
./libgoogleearth_free.so(+0xc005b)[0xb76b805b]
./libgoogleearth_free.so(earthmain+0x249)[0xb76b91b9]
./googleearth-bin[0x804878b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb5203bd6]
./googleearth-bin[0x80486d1]

```Has anyone been successful running GE6 on Lucid? Any ideas on how to fix this or at least where to look? Googling for the problem I've seen many recommendation to install lsb-core but this package is installed.

---

### Post by JaseP on 2012-03-31
I found this on an Italian website...

It will run, but there are polygon artifacts on my GMA 3100 graphics chipset...

sudo cd /opt/google/earth/free
sudo wget [http://librarian.launchpad.net/7037027/libGL.so.1](http://librarian.launchpad.net/7037027/libGL.so.1)
sudo chmod a+x libGL.so.1

---

### Post by ofnuts on 2012-03-31
> **JaseP said:**
> I found this on an Italian website...

It will run, but there are polygon artifacts on my GMA 3100 graphics chipset...

sudo cd /opt/google/earth/free
sudo wget [http://librarian.launchpad.net/7037027/libGL.so.1](http://librarian.launchpad.net/7037027/libGL.so.1)
sudo chmod a+x libGL.so.1
It indeed works... doesn't look rock-solid, but still usable. Thanks for the tip.

---


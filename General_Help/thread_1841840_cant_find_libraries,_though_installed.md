---
title: "cant find libraries, though installed"
date: 2011-09-10
forum: General Help
---

### Post by Chiel92 on 2011-09-10
Hello, 
I am trying to install amuc. Only the source code is available as far as I know, so I downloaded the source code and tried to run 
```
./configure
```

It says:
```

library x11 ... no
library alsa ... no
library xft ... no
library cairo ... no
library jack ... no
Some libraries are missing, exit.

```

I am sure though that I have installed all those libraries.
:confused: :confused: :confused:

Any help appreciated.

---

### Post by Toz on 2011-09-10
If you're talking about the Amsterdam Music Composer ([http://members.chello.nl/w.boeke/amuc/]("http://members.chello.nl/w.boeke/amuc/")), there is a Debian package available to download. You can install it (easier than building from source). You'll need to make sure that you have the following dependencies installed: **libgcc1, libc6, libasound2, libcairo2, libjack0**
(search for them in the software centre) or install them from a terminal window via:
```
sudo apt-get install libgcc1 libc6 libasound2 libcairo2 libjack0
```

Then you can install the application deb file itself by double-clicking it, or from the terminal window via:
```
sudo dpkg -i amuc_1.7-1_i386.deb
```

Installing the deb file is easier than building from source, plus its easier to uninstall it if needed (sudo dpkg -r amuc).

---

### Post by Chiel92 on 2011-09-10
Thanks or your help!
This worked.:P

---


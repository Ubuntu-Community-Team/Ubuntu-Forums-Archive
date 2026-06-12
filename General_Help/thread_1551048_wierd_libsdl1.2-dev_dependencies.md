---
title: "wierd libsdl1.2-dev dependencies"
date: 2010-08-11
forum: General Help
---

### Post by DangerOnTheRanger on 2010-08-11
I tried to install libsdl1.2-dev:

```

sudo apt-get install libsdl-dev

```And this is what happened:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libsdl1.2-dev instead of libsdl-dev
The following packages were automatically installed and are no longer required:
  libboost-regex1.40.0 mercurial-common libboost-date-time1.40.0 gpp
  libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libaa1-dev libasound2-dev libaudio-dev libcaca-dev libdrm-dev
  libgl1-mesa-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev
  libncurses5-dev libpulse-dev libsdl1.2-dev libsdl1.2debian
  libsdl1.2debian-alsa libslang2-dev mesa-common-dev
Suggested packages:
  libasound2-doc
The following packages will be REMOVED:
  libsdl1.2debian-pulseaudio ubuntu-desktop
The following NEW packages will be installed:
  libaa1-dev libasound2-dev libaudio-dev libcaca-dev libdrm-dev
  libgl1-mesa-dev libglu1-mesa-dev libncurses5-dev libpulse-dev libsdl1.2-dev
  libsdl1.2debian-alsa libslang2-dev mesa-common-dev
The following packages will be upgraded:
  libgl1-mesa-glx libglu1-mesa libsdl1.2debian
3 upgraded, 13 newly installed, 2 to remove and 266 not upgraded.
Need to get 8,557kB of archives.
After this operation, 24.8MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```I shouldn't have to remove/change all those packages just to install the SDL dev libraries!

What is going on?

Thanks,

DangerOnTheRanger

---

### Post by DangerOnTheRanger on 2010-08-11
Bump!

---


---
title: "Xvfb + CutyCapt problem. Doen't recognizr chinese symbols"
date: 2011-05-16
forum: General Help
---

### Post by j.desevg on 2011-05-16
Hello people,

I use Linux * 2.6.18-164.10.1.el5.028stab067.4ent #1 SMP Fri Jan 15 03:06:15 MSK 2010 i686 build
to configurate xvfb + cutycapt, I need it to convert html to image.

The package that I have already installed:

build-essential
xvfb
xfonts-100dpi xfonts-75dpi xfonts-scalable xfonts-cyrillic
libgl1-mesa-dri
libqt4-webkit libqt4-dev g++
x11-xkb-utils
xserver-xorg-core

It seems like it works, but there is one problem. It misses chinese symbols when converts html to image.
I thought that it is encoding issue and rechecked all my conf related that and set default encoding up to es_US.UTF8, but it didn't help


LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=


I'm testing these on the 2 computer. local and my vds. They both have Ubuntu 10.04
On the local machine all works fine, but on the vds it doesn't take chinese symbols..

Do you have any idea where can I find the difference between machines configurations?

I suspect it depends with X server configuration.

Thanks!

---

### Post by j.desevg on 2011-05-16
I resolved the problem. The solution is mess, but effective ) I set KDE(kubuntu-desktop) on the vds. It installed ~100 libs on my machine, I think libs that really needed 2-3, but I don't have time to find out which ones. If somebody find out it, please, share with all.

Thanks!

---


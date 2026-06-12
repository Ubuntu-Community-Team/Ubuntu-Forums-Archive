---
title: "Python-dev"
date: 2009-11-14
forum: General Help
---

### Post by golfie on 2009-11-14
Hi all,

I need to install python-dev package. But is some dependency broken. 

After apt-get install python-dev it wants to remove 

  libsm-dev python-excelerator libgnuradio-omnithread python-opengl
  libqt4-opengl libice-dev libatlas3gf-base libatlas-headers libqt4-assistant
  x11proto-xext-dev libfftw3-dev libaudio-dev libgsl0-dev x11proto-kb-dev
  libglib2.0-dev libblas-dev x11proto-xinerama-dev comerr-dev libgfortran3
  g++-4.4 libqt4-test libwxgtk2.8-0 libqt4-sql-mysql libqt4-dbus
  x11proto-render-dev python-antlr libqwt5-qt4 libqt4-qt3support libxi-dev
  libxmu-headers libxrender-dev libqt4-opengl-dev libstdc++6-4.4-dev
  libfftw3-3 mesa-common-dev libatlas-base-dev libkadm5srv6 libxdmcp-dev
  libkrb5-dev g++ libglu1-xorg-dev libpng12-dev libsqlite0-dev libgssrpc4
  libfontconfig1-dev xtrans-dev libqt4-xmlpatterns libqt4-dev
  x11proto-core-dev libxcursor-dev libqt4-help python-numpy blt libusb-dev
  python-tk libqt4-webkit python-tz libglu1-mesa-dev python-matplotlib-data
  libqtcore4 libqwtplot3d-qt4-dev x11proto-randr-dev libssl-dev qt4-qmake
  libxt-dev libxmu-dev libxext-dev libwxbase2.8-0 swig libjpeg62-dev
  zlib1g-dev x11proto-input-dev libqt4-sql libfreetype6-dev libqt4-svg
  x11proto-fixes-dev python-dateutil libpthread-stubs0-dev xlibmesa-gl-dev
  libxau-dev libpthread-stubs0 libqt4-xml libblas3gf tcl8.5 python-wxversion
  libasound2-dev libqt4-network python-pyparsing libamd2.2.0 libqt4-designer
  libgl1-mesa-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev libqtgui4
  tk8.5 libqt4-phonon python-matplotlib libxft-dev libx11-dev libkdb5-4
  python-scipy python-wxgtk2.8 libumfpack5.4.0 libxfixes-dev libqt4-script
  libgnuradio-omnithread-dev libmng-dev libxcb1-dev libqt4-scripttools
  libaudio2 libxinerama-dev libqwtplot3d-qt4 freeglut3

and only install python-dev and python2.6-dev.

Removing g++ for installing python-dev, can't be right?

What to do?

---

### Post by lovemylady on 2009-11-14
I got some package dependency problems too..
perhaps use KpackageKit to get it!
and if there stands blablabla dependency 
try
sudo apt-get -f install and/or sudo apt-get update             (in console ofc)

should fix everything atleast aht worked by me :p

---

### Post by golfie on 2009-11-15
Thanks, is there any suggestion to do this without KDE. 

Will it work, if I install and remove dependency packages. And afterwards run 

apt-get install -f

I'm a little afraid that I need to manually install all the removed packages..

Ronald

---


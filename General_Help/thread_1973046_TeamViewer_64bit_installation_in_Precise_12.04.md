---
title: "TeamViewer 64bit installation in Precise 12.04"
date: 2012-05-04
forum: General Help
---

### Post by lucazade on 2012-05-04
When I try to install TeamViewer 64bit in Precise 12.04 I have to install 218 packages as dependecies... the 32bit version instead doens't ask for any deps.
What's wrong with multiarch? How to install it without all those dependencies?

```
sudo gdebi teamviewer_linux_x64.deb 

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 

Richiede l'installazione dei seguenti pacchetti: 
bluez-alsa:i386  esound-common  glib-networking:i386  gstreamer0.10-fluendo-mp3:i386  gstreamer0.10-plugins-base:i386  gstreamer0.10-plugins-good:i386  gstreamer0.10-x:i386  gtk2-engines-murrine:i386  gtk2-engines-oxygen:i386  gtk2-engines-pixbuf:i386  gtk2-engines:i386  gvfs-libs:i386  gvfs:i386  ia32-libs  ia32-libs-multiarch:i386  ibus-gtk:i386  lib32asound2  lib32z1  libaa1:i386  libacl1:i386  libaio1:i386  libao-common  libao4:i386  libasn1-8-heimdal:i386  libasound2-plugins:i386  libasound2:i386  libasyncns0:i386  libatk1.0-0:i386  libattr1:i386  libaudio2:i386  libaudiofile1:i386  libavahi-client3:i386  libavahi-common-data:i386  libavahi-common3:i386  libavc1394-0:i386  libbz2-1.0:i386  libc6-i386  libcaca0:i386  libcairo-gobject2:i386  libcairo2:i386  libcanberra-gtk-module:i386  libcanberra-gtk0:i386  libcanberra0:i386  libcap2:i386  libcapi20-3:i386  libcdparanoia0:i386  libcomerr2:i386  libcroco3:i386  libcups2:i386  libcupsimage2:i386  libcurl3:i386  libdatrie1:i386  libdb5.1:i386  libdbus-1-3:i386  libdbus-glib-1-2:i386  libdv4:i386  libelf1:i386  libesd0:i386  libexif12:i386  libflac8:i386  libfontconfig1:i386  libfreetype6:i386  libgail-common:i386  libgail18:i386  libgconf-2-4:i386  libgcrypt11:i386  libgd2-xpm:i386  libgdbm3:i386  libgdk-pixbuf2.0-0:i386  libgettextpo0:i386  libglib2.0-0:i386  libglu1-mesa:i386  libgnome-keyring0:i386  libgnutls26:i386  libgomp1:i386  libgpg-error0:i386  libgphoto2-2:i386  libgphoto2-port0:i386  libgpm2:i386  libgssapi-krb5-2:i386  libgssapi3-heimdal:i386  libgstreamer-plugins-base0.10-0:i386  libgstreamer0.10-0:i386  libgtk2.0-0:i386  libgudev-1.0-0:i386  libhcrypto4-heimdal:i386  libheimbase1-heimdal:i386  libheimntlm0-heimdal:i386  libhx509-5-heimdal:i386  libibus-1.0-0:i386  libice6:i386  libidn11:i386  libiec61883-0:i386  libieee1284-3:i386  libjack-jackd2-0:i386  libjasper1:i386  libjpeg-turbo8:i386  libjpeg8:i386  libjson0:i386  libk5crypto3:i386  libkeyutils1:i386  libkrb5-26-heimdal:i386  libkrb5-3:i386  libkrb5support0:i386  liblcms1:i386  libldap-2.4-2:i386  libltdl7:i386  libmad0:i386  libmikmod2:i386  libmng1:i386  libmpg123-0:i386  libmysqlclient18:i386  libncurses5:i386  libncursesw5:i386  libnspr4:i386  libnss3:i386  libodbc1:i386  libogg0:i386  liboil0.3:i386  libopenal1:i386  liborc-0.4-0:i386  libp11-kit0:i386  libpango1.0-0:i386  libpcre3:i386  libpixman-1-0:i386  libpng12-0:i386  libproxy1:i386  libpulse-mainloop-glib0:i386  libpulse0:i386  libpulsedsp:i386  libqt4-dbus:i386  libqt4-declarative:i386  libqt4-designer:i386  libqt4-network:i386  libqt4-opengl:i386  libqt4-qt3support:i386  libqt4-script:i386  libqt4-scripttools:i386  libqt4-sql-mysql:i386  libqt4-sql:i386  libqt4-svg:i386  libqt4-test:i386  libqt4-xml:i386  libqt4-xmlpatterns:i386  libqtcore4:i386  libqtgui4:i386  libqtwebkit4:i386  libraw1394-11:i386  libroken18-heimdal:i386  librsvg2-2:i386  librsvg2-common:i386  librtmp0:i386  libsamplerate0:i386  libsane:i386  libsasl2-2:i386  libsasl2-modules:i386  libsdl-image1.2:i386  libsdl-mixer1.2:i386  libsdl-net1.2:i386  libsdl-ttf2.0-0:i386  libsdl1.2debian:i386  libselinux1:i386  libshout3:i386  libslang2:i386  libsm6:i386  libsndfile1:i386  libsoup-gnome2.4-1:i386  libsoup2.4-1:i386  libspeex1:i386  libspeexdsp1:i386  libsqlite3-0:i386  libssl0.9.8:i386  libssl1.0.0:i386  libstdc++5:i386  libtag1-vanilla:i386  libtag1c2a:i386  libtasn1-3:i386  libtdb1:i386  libthai0:i386  libtheora0:i386  libtiff4:i386  libtinfo5:i386  libudev0:i386  libunistring0:i386  libusb-0.1-4:i386  libuuid1:i386  libv4l-0:i386  libv4lconvert0:i386  libvisual-0.4-0:i386  libvisual-0.4-plugins:i386  libvorbis0a:i386  libvorbisenc2:i386  libvorbisfile3:i386  libwavpack1:i386  libwind0-heimdal:i386  libwrap0:i386  libxaw7:i386  libxcb-render0:i386  libxcb-shm0:i386  libxcomposite1:i386  libxcursor1:i386  libxft2:i386  libxi6:i386  libxinerama1:i386  libxml2:i386  libxmu6:i386  libxp6:i386  libxpm4:i386  libxrandr2:i386  libxrender1:i386  libxslt1.1:i386  libxss1:i386  libxt6:i386  libxtst6:i386  odbcinst  odbcinst1debian2  odbcinst1debian2:i386  xaw3dg:i386 
TeamViewer (Remote Control Application)
 TeamViewer is a remote control application. TeamViewer provides easy, fast and secure remote access to Linux, Windows PCs, and Macs.
 .
 TeamViewer is free for personal use. You can use TeamViewer completely free of charge to access your private computers or to help your friends with their computer problems.
 .
 To buy a license for commercial use, please visit http://www.teamviewer.com
Installare il pacchetto software? [s/N]:n

```

tried with software-center, gdebi and dpkg.. same odd result.

---

### Post by lucazade on 2012-05-04
it should be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/971761)

---

### Post by lucazade on 2012-05-09
bump

---


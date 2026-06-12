---
title: "Getting Crazy Installing Google-Earth in KDE"
date: 2012-09-01
forum: General Help
---

### Post by JCM_Pico on 2012-09-01
Hi there....

Installing Google-Earth in Kubuntu is driving me crazy....

I've downloaded the .deb packaged from their site and run

```
sudo dpkg -i google-earth-stable_current_amd64.deb
```

And the problems started

```
Selecting previously unselected package google-earth-stable.
(Reading database ... 297230 files and directories currently installed.)
Unpacking google-earth-stable (from google-earth-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on lsb-core (>= 3.2); however:
  Package lsb-core is not installed.
 google-earth-stable depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing google-earth-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 google-earth-stable
```

But ok... I tried to install the unmet dependencies 

```
sudo apt-get -f install
```

And it is a huge list with things like gnome-keyring and some other gnome stuff

```
sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ia32-libs ia32-libs-multiarch:i386 ibus-gtk:i386 lib32z1 libaa1:i386 libaio1:i386 libao-common
  libao4:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libaudiofile1:i386 libavc1394-0:i386 libcaca0:i386
  libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcroco3:i386 libcupsimage2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libdv4:i386 libesd0:i386 libexif12:i386 libflac8:i386 libgail-common:i386 libgail18:i386
  libgconf-2-4:i386 libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libglu1-mesa:i386 libgnome-keyring0:i386 libgomp1:i386 libgphoto2-2:i386
  libgphoto2-port0:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libibus-1.0-0:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libjasper1:i386 libjson0:i386 libkrb5-26-heimdal:i386 libldap-2.4-2:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmpg123-0:i386 libnspr4:i386 libnss3:i386
  libodbc1:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libpango1.0-0:i386 libpixman-1-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulse0:i386
  libpulsedsp:i386 libqt4-designer:i386 libqt4-qt3support:i386 libqt4-scripttools:i386 libqt4-svg:i386 libqt4-test:i386 libqtwebkit4:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libshout3:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
  libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386 libstdc++5:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtdb1:i386 libtheora0:i386
  libunistring0:i386 libusb-0.1-4:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvorbisfile3:i386 libwavpack1:i386 libwind0-heimdal:i386 libwrap0:i386 libxaw7:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386
  libxft2:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386 libxslt1.1:i386 libxss1:i386 libxtst6:i386 libxv1:i386 lsb-core
  ncurses-term odbcinst1debian2:i386 pax xaw3dg:i386
Suggested packages:
  murrine-themes:i386 kde-config-gtk-style:i386 gvfs-backends:i386 libpam-ldap:i386 libpam-winbind:i386 libnss-ldap:i386 libroar1:i386 libsndio0:i386 roaraudio-server:i386
  libasound2-python:i386 libcanberra-pulse:i386 libdv-bin:i386 pulseaudio-esound-compat:i386 libgd-tools:i386 gnome-keyring:i386 gphoto2:i386 gtkam:i386
  gstreamer-codec-install:i386 gnome-codec-install:i386 gstreamer0.10-tools:i386 jackd2:i386 libjasper-runtime:i386 libmyodbc:i386 odbc-postgresql:i386 tdsodbc:i386
  unixodbc-bin:i386 ttf-baekmuk:i386 ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386 libraw1394-doc:i386
  librsvg2-bin:i386 hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386 libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386 libsasl2-modules-sql:i386
  libsasl2-modules-gssapi-mit:i386 libsasl2-modules-gssapi-heimdal:i386 speex:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ia32-libs ia32-libs-multiarch:i386 ibus-gtk:i386 lib32z1 libaa1:i386 libaio1:i386 libao-common
  libao4:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libaudiofile1:i386 libavc1394-0:i386 libcaca0:i386
  libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcroco3:i386 libcupsimage2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libdv4:i386 libesd0:i386 libexif12:i386 libflac8:i386 libgail-common:i386 libgail18:i386
  libgconf-2-4:i386 libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libglu1-mesa:i386 libgnome-keyring0:i386 libgomp1:i386 libgphoto2-2:i386
  libgphoto2-port0:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libibus-1.0-0:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libjasper1:i386 libjson0:i386 libkrb5-26-heimdal:i386 libldap-2.4-2:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmpg123-0:i386 libnspr4:i386 libnss3:i386
  libodbc1:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libpango1.0-0:i386 libpixman-1-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulse0:i386
  libpulsedsp:i386 libqt4-designer:i386 libqt4-qt3support:i386 libqt4-scripttools:i386 libqt4-svg:i386 libqt4-test:i386 libqtwebkit4:i386 libraw1394-11:i386
  libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libshout3:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
  libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386 libstdc++5:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtdb1:i386 libtheora0:i386
  libunistring0:i386 libusb-0.1-4:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvorbisfile3:i386 libwavpack1:i386 libwind0-heimdal:i386 libwrap0:i386 libxaw7:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386
  libxft2:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386 libxslt1.1:i386 libxss1:i386 libxtst6:i386 libxv1:i386 lsb-core
  ncurses-term odbcinst1debian2:i386 pax xaw3dg:i386
0 upgraded, 156 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2,858 kB/43.0 MB of archives.
After this operation, 134 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

This is a lot of unwanted packages and has I remembered KDE does not used to need all those things....

Is there anybody who can explain what's happening here?

---

### Post by JCM_Pico on 2012-09-06
Bump !!!

I've experienced the same with Skype

---


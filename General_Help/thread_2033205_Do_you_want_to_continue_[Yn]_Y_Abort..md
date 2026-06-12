---
title: "Do you want to continue [Y/n]? Y Abort."
date: 2012-07-25
forum: General Help
---

### Post by cyanide911 on 2012-07-25
I'm trying to follow this guide to setup hybrid AMD/Intel graphics on my system:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

But I'm stuck on this command 


```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386

```

I get this if I execute the above command:
```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bluez-alsa:i386 esound-common gcc-4.6-base:i386 glib-networking
  glib-networking:i386 glib-networking-common glib-networking-services
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base:i386
  gstreamer0.10-plugins-good:i386 gstreamer0.10-x gstreamer0.10-x:i386
  gtk2-engines:i386 gtk2-engines-murrine:i386 gtk2-engines-oxygen:i386
  gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ia32-libs-multiarch:i386
  ibus-gtk:i386 libaa1:i386 libacl1:i386 libaio1:i386 libao-common libao4:i386
  libasn1-8-heimdal:i386 libasound2 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2:i386
  libaudiofile1:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libavc1394-0:i386 libbz2-1.0:i386 libc6:i386
  libcaca0:i386 libcairo-gobject2 libcairo-gobject2:i386 libcairo2
  libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386
  libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcomerr2:i386 libcroco3:i386 libcups2 libcups2:i386 libcupsimage2
  libcupsimage2:i386 libcurl3:i386 libdatrie1:i386 libdb5.1:i386
  libdbus-1-3:i386 libdbus-glib-1-2:i386 libdrm-intel1:i386
  libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386 libdv4:i386
  libesd0:i386 libexif12 libexif12:i386 libexpat1:i386 libffi6:i386
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgail-common:i386
  libgail18:i386 libgcc1:i386 libgconf-2-4:i386 libgcrypt11 libgcrypt11:i386
  libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libglib2.0-0 libglib2.0-0:i386
  libglib2.0-bin libglu1-mesa libglu1-mesa:i386 libgnome-keyring0:i386
  libgnutls26 libgnutls26:i386 libgomp1:i386 libgpg-error0:i386
  libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgssapi-krb5-2
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libibus-1.0-0:i386 libice6:i386 libidn11:i386
  libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjasper1:i386
  libjpeg-turbo8 libjpeg-turbo8:i386 libjpeg8:i386 libjson0:i386 libk5crypto3
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3
  libkrb5-3:i386 libkrb5support0 libkrb5support0:i386 liblcms1:i386
  libldap-2.4-2:i386 libllvm3.0:i386 libltdl7:i386 libmad0:i386
  libmikmod2:i386 libmng1:i386 libmpg123-0:i386 libmysqlclient18:i386
  libncurses5:i386 libncursesw5:i386 libnspr4:i386 libnss3:i386 libodbc1:i386
  libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386
  libpango1.0-0 libpango1.0-0:i386 libpciaccess0:i386 libpcre3:i386
  libpixman-1-0:i386 libpng12-0:i386 libproxy1:i386 libpulse-mainloop-glib0
  libpulse-mainloop-glib0:i386 libpulse0 libpulse0:i386 libpulsedsp
  libpulsedsp:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-designer:i386 libqt4-network:i386 libqt4-opengl:i386
  libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386
  libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386
  libqtwebkit4:i386 libraw1394-11:i386 libroken18-heimdal:i386 librsvg2-2:i386
  librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386
  libsasl2-2 libsasl2-2:i386 libsasl2-modules libsasl2-modules:i386
  libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386
  libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libselinux1:i386 libshout3:i386
  libslang2:i386 libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386
  libsoup2.4-1:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386
  libssl0.9.8:i386 libssl1.0.0 libssl1.0.0:i386 libstdc++5:i386
  libstdc++6:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtasn1-3
  libtasn1-3:i386 libtdb1:i386 libthai0:i386 libtheora0:i386 libtiff4
  libtiff4:i386 libtinfo5:i386 libudev0:i386 libunistring0:i386
  libusb-0.1-4:i386 libuuid1:i386 libv4l-0 libv4l-0:i386 libv4lconvert0
  libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386
  libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libwavpack1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxaw7:i386 libxcb-glx0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxft2:i386
  libxi6:i386 libxinerama1:i386 libxml2 libxml2:i386 libxmu6:i386 libxp6:i386
  libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxss1:i386
  libxt6:i386 libxtst6:i386 libxv1:i386 libxxf86vm1:i386 mysql-common odbcinst
  odbcinst1debian2 odbcinst1debian2:i386 oss-compat xaw3dg:i386 zlib1g:i386
Suggested packages:
  murrine-themes:i386 kde-config-gtk-style:i386 libpam-ldap:i386
  libpam-winbind:i386 libnss-ldap:i386 libroar1:i386 libsndio0:i386
  roaraudio-server:i386 libasound2-python libasound2-python:i386 nas:i386
  glibc-doc:i386 locales:i386 libcanberra-pulse:i386 cups-common:i386
  libdv-bin:i386 oss-compat:i386 pulseaudio-esound-compat:i386 rng-tools
  rng-tools:i386 libgd-tools:i386 libglide3 libglide3:i386 gnome-keyring:i386
  gnutls-bin gnutls-bin:i386 gphoto2:i386 gtkam:i386 gpm:i386 krb5-doc
  krb5-user krb5-doc:i386 krb5-user:i386 gstreamer-codec-install:i386
  gnome-codec-install:i386 gstreamer0.10-tools:i386 jackd2:i386
  libjasper-runtime:i386 liblcms-utils:i386 libmyodbc:i386
  odbc-postgresql:i386 tdsodbc:i386 unixodbc-bin:i386 ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp ttf-baekmuk:i386 ttf-arphic-gbsn00lp:i386
  ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386
  libqt4-declarative-folderlistmodel:i386 libqt4-declarative-gestures:i386
  libqt4-declarative-particles:i386 libqt4-declarative-shaders:i386
  qt4-qmlviewer:i386 libqt4-dev:i386 qt4-qtconfig:i386 libraw1394-doc:i386
  librsvg2-bin:i386 hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
  libsasl2-modules-otp libsasl2-modules-ldap libsasl2-modules-sql
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal
  libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386 speex:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed:
  bluez-alsa:i386 esound-common gcc-4.6-base:i386 glib-networking:i386
  gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386
  gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386
  ia32-libs ia32-libs-multiarch:i386 ibus-gtk:i386 lib32gcc1 libaa1:i386
  libacl1:i386 libaio1:i386 libao-common libao4:i386 libasn1-8-heimdal:i386
  libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386
  libattr1:i386 libaudio2:i386 libaudiofile1:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386
  libbz2-1.0:i386 libc6:i386 libc6-i386 libcaca0:i386 libcairo-gobject2:i386
  libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386
  libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386
  libcomerr2:i386 libcroco3:i386 libcups2:i386 libcupsimage2:i386
  libcurl3:i386 libdatrie1:i386 libdb5.1:i386 libdbus-1-3:i386
  libdbus-glib-1-2:i386 libdrm-intel1:i386 libdrm-nouveau1a:i386
  libdrm-radeon1:i386 libdrm2:i386 libdv4:i386 libesd0:i386 libexif12:i386
  libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgail-common:i386 libgail18:i386 libgcc1:i386
  libgconf-2-4:i386 libgcrypt11:i386 libgd2-xpm:i386 libgdbm3:i386
  libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnome-keyring0:i386 libgnutls26:i386 libgomp1:i386 libgpg-error0:i386
  libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libibus-1.0-0:i386 libice6:i386 libidn11:i386
  libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjasper1:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libjson0:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libllvm3.0:i386
  libltdl7:i386 libmad0:i386 libmikmod2:i386 libmng1:i386 libmpg123-0:i386
  libmysqlclient18:i386 libncurses5:i386 libncursesw5:i386 libnspr4:i386
  libnss3:i386 libodbc1:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386
  libp11-kit0:i386 libpango1.0-0:i386 libpciaccess0:i386 libpcre3:i386
  libpixman-1-0:i386 libpng12-0:i386 libproxy1:i386
  libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386
  libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386
  libqt4-network:i386 libqt4-opengl:i386 libqt4-qt3support:i386
  libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386
  libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386
  libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386
  libraw1394-11:i386 libroken18-heimdal:i386 librsvg2-2:i386
  librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386
  libsasl2-2:i386 libsasl2-modules:i386 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386
  libsdl1.2debian:i386 libselinux1:i386 libshout3:i386 libslang2:i386
  libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386
  libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386
  libssl1.0.0:i386 libstdc++5:i386 libstdc++6:i386 libtag1-vanilla:i386
  libtag1c2a:i386 libtasn1-3:i386 libtdb1:i386 libthai0:i386 libtheora0:i386
  libtiff4:i386 libtinfo5:i386 libudev0:i386 libunistring0:i386
  libusb-0.1-4:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386
  libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386
  libvorbisenc2:i386 libvorbisfile3:i386 libwavpack1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxaw7:i386 libxcb-glx0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxft2:i386
  libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386
  libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxss1:i386
  libxt6:i386 libxtst6:i386 libxv1:i386 libxxf86vm1:i386 mysql-common odbcinst
  odbcinst1debian2 odbcinst1debian2:i386 oss-compat xaw3dg:i386 zlib1g:i386
The following packages will be upgraded:
  glib-networking glib-networking-common glib-networking-services
  gstreamer0.10-plugins-base gstreamer0.10-x libasound2 libcairo-gobject2
  libcairo2 libcups2 libcupsimage2 libexif12 libgcrypt11 libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libglib2.0-0 libglib2.0-bin libglu1-mesa
  libgnutls26 libgssapi-krb5-2 libgstreamer-plugins-base0.10-0 libjpeg-turbo8
  libk5crypto3 libkrb5-3 libkrb5support0 libpango1.0-0 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libsasl2-2 libsasl2-modules libssl1.0.0 libtasn1-3
  libtiff4 libv4l-0 libv4lconvert0 libxml2
37 upgraded, 243 newly installed, 0 to remove and 265 not upgraded.
Need to get 87.1 MB/91.0 MB of archives.
After this operation, 254 MB of additional disk space will be used.
[B]Do you want to continue [Y/n]? Y
Abort.[/B]

```

This doesn't make sense. How do I tackle this? It gives no error message or anything. Uppercase Y, Lowercase Y, simply pressing enter doesn't work.


EDIT: After restarting the Terminal 4-5 times it now works. I'd still like to know why this was happening, it might happen again.

---

### Post by richpri on 2012-07-25
Take a look at 

/var/log/apt/history.log

and see if you got any error messages.

You may have to go back to an archived file. 
They are in the same directory.

---


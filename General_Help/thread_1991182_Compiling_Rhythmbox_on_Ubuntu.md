---
title: "Compiling Rhythmbox on Ubuntu?"
date: 2012-05-30
forum: General Help
---

### Post by melrokz on 2012-05-30
I applied a patch for Rhythmbox am trying to compile it, but configure gives me too many errors. How to rectify this and is it worth the trouble? I'm trying to fix an aesthetic issue with descender letters in the song title.

```

configure: error: Package requirements (		  gobject-introspection-1.0 >= 0.10.0 		  gtk+-3.0 >= 3.2.0			  gdk-pixbuf-2.0 >= 2.18.0			  glib-2.0 >= 2.28.0				  gio-2.0 >= 2.28.0				  gio-unix-2.0 >= 2.28.0				  libsoup-2.4 >= 2.26.0				  libsoup-gnome-2.4 >= 2.26.0			  libpeas-1.0 >= 0.7.3				  libpeas-gtk-1.0 >= 0.7.3			  tdb >= 1.2.6) were not met:

No package 'gtk+-3.0' found
No package 'gdk-pixbuf-2.0' found
No package 'libsoup-2.4' found
No package 'libsoup-gnome-2.4' found
No package 'libpeas-1.0' found
No package 'libpeas-gtk-1.0' found
No package 'tdb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

---

### Post by Cheesemill on 2012-05-30
Have you got all of the necessary build dependencies installed?
```
sudo apt-get build-dep rhythmbox
```

---

### Post by melrokz on 2012-05-30
Thanks, I'll try that. Btw, where is the thanks button? :)

---

### Post by Cheesemill on 2012-05-30
> **melrokz said:**
> Thanks, I'll try that. Btw, where is the thanks button? :)
There isn't one, but you're welcome :)

---

### Post by melrokz on 2012-05-30
Too many packages. Will installing all this break my system? Maybe later, because this is an office system. Btw, Do you recommend compiling software in a Virtualbox Ubuntu?

```
autopoint cdbs debhelper dh-apparmor dh-autoreconf dh-translations docbook docbook-dsssl docbook-to-man docbook-utils docbook-xsl
  gir1.2-brasero-3.0 gir1.2-gconf-2.0 gir1.2-json-1.0 git git-man gnome-common gnome-doc-utils gnome-pkg-tools gstreamer0.10-doc
  gstreamer0.10-plugins-base-doc gtk-doc-tools html2text intltool-debian jade jadetex libarchive-dev libatk1.0-dev libavahi-client-dev
  libavahi-common-dev libavahi-glib-dev libbrasero-media3-dev libcairo-script-interpreter2 libcairo2-dev libdbus-1-dev libdiscid0-dev
  libdmapsharing-3.0-dev liberror-perl libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev libgdk-pixbuf2.0-dev
  libgdk-pixbuf2.0-doc libglib2.0-doc libgmime-2.6-dev libgnome-keyring-dev libgpod-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev
  libgtk-3-dev libgtk-3-doc libgtk2.0-dev libgudev-1.0-dev libice-dev libimobiledevice-dev libjavascriptcoregtk-3.0-dev libjson-glib-dev
  liblaunchpad-integration-3.0-dev liblircclient-dev libmtp-dev libmusicbrainz3-dev libneon27 libneon27-dev libnotify-dev libpango1.0-dev
  libpango1.0-doc libpeas-dev libpixman-1-dev libplist-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libquvi-dev libsgmls-perl
  libsm-dev libsoup-gnome2.4-dev libsoup2.4-dev libsp1c2 libtdb-dev libtool libtotem-plparser-dev libudev-dev libusb-1.0-0-dev libusbmuxd-dev
  libwebkitgtk-3.0-dev libx11-dev libxau-dev libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxml2-doc libxml2-utils libxrandr-dev
  libxrender-dev libxt-dev luatex lynx lynx-cur po-debconf python-dev python-gi-dev python-gobject-2-dev python-gobject-dev python-gst0.10-dev
  python-scour python2.7-dev sgmlspl sp tex-common texlive-base texlive-binaries texlive-common texlive-doc-base texlive-fonts-recommended
  texlive-latex-base texlive-latex-recommended tipa x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xorg-sgml-doctools
  xsltproc xtrans-dev

```

---

### Post by Cheesemill on 2012-05-30
It might be a lot of packages but you do need all of them to compile Rhythmbox. Installing them won't break your system they will just take up disk space, you can always keep a note of the packages installed and simply un-install them when you're done compiling.

You could use a VM for compiling but I'm not going suggest which is better as I never compile software myself.

---

### Post by raja.genupula on 2012-05-30
by using ```
sudo apt-get autoremove
``` you can remove all the pkg's which are no need for your system . so after doing the process of yours just run the above command . it will take care of the pkg's which are no need for your PC .

hope that helps . :)

---


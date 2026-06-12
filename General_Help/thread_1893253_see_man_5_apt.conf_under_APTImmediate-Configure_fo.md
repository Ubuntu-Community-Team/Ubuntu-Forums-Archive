---
title: "see man 5 apt.conf under APT::Immediate-Configure for details."
date: 2011-12-09
forum: General Help
---

### Post by NerdSupreme on 2011-12-09
I was wondering what this means:

apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  mono-2.0-gac normalize-audio libplist1 libxfcegui4-4 xorg-docs-core
  libgnomekbd7 libpanel-applet-4-0 libical0 libwildmidi1 libmono2.0-cil
  libgtkmm-3.0-1 libzbar0 libcanberra-gtk-module gstreamer0.10-x libarchive1
  libhttp-daemon-perl libmono-data-tds2.0-cil libflite1 libgio-cil
  libraptor2-0 libfile-listing-perl libpackagekit-glib2-14 xfonts-scalable
  libmono-system-data2.0-cil usbmuxd libsensors4 libcanberra-gtk3-0
  libwww-robotrules-perl mobile-broadband-provider-info libindicator3
  libglib2.0-cil libiec61883-0 libdjvulibre21 librdf0 libicu48 libotf0
  libdbus-glib1.0-cil gnome-desktop3-data libbluray1 libgconf2.0-cil
  libdbusmenu-glib3 libsilc-1.1-2 librsvg2-2.18-cil liblua5.1-filesystem0
  libgfortran3 libresid-builder0c2a cli-common libburn4 libibus2
  libgstfarsight0.10-0 ibus-gtk python-libxml2 libxmlrpc-core-c3
  libhttp-date-perl libtagc0 liblwp-mediatypes-perl libfont-afm-perl
  libmailtools-perl smbfs xserver-common libopenspc0 gvfs-libs libupower-glib1
  librpmio1 rpm-common system-config-printer-udev libsqlite0 libfftw3-3
  libslv2-9 python-pyorbit libnotify4 python-gconf libass4
  libpulse-mainloop-glib0 gvfs-common libndesk-dbus1.0-cil librasqal3
  libgnome-menu2 gstreamer0.10-plugins-good libgeoclue0 libgadu3 libgd2-noxpm
  liblvm2app2.2 libmono-cairo2.0-cil suckless-tools xfce-keyboard-shortcuts
  libgnomekbd-common libido-0.1-0 libnice10 libelf1 libmono-messaging2.0-cil
  libgssdp-1.0-2 libmono-addins0.2-cil libmusicbrainz4c2a python-numpy
  libsidutils0 libmono-system-messaging2.0-cil libmono-posix2.0-cil libexempi3
  libmono-security2.0-cil libsoundtouch0 libio-stty-perl libgnome2-vfs-perl
  libdbusmenu-gtk3 libgtk2.0-cil mono-gac icedax libgme0
  libwebservice-musicbrainz-perl libmono-system-data-linq2.0-cil libpython2.6
  libgail-3-0 libcanberra-gtk0 libimobiledevice2 libmono-sqlite2.0-cil
  python-pysqlite2 libjson-glib-1.0-0 libmono-system-web2.0-cil
  libwnck2.20-cil libdv4 libmono-sharpzip2.84-cil libmono-corlib2.0-cil
  gstreamer0.10-plugins-bad libsoup-gnome2.4-1 libblas3gf tcl8.4 libkate1
  gstreamer0.10-nice libcdaudio1 libhtml-form-perl libmimic0 libusbmuxd1
  mono-runtime liblapack3gf libcddb-get-perl libcanberra0
  libhttp-negotiate-perl libsidplay2 libhtml-format-perl cups-pk-helper
  libio-pty-perl libgupnp-1.0-3 libencode-locale-perl libunistring0 cifs-utils
  libxcb-dri2-0 libxklavier16 libyajl1 libmeanwhile1 libsilcclient-1.1-3
  libndesk-dbus-glib1.0-cil libzephyr4 libquadmath0 libgnome-keyring1.0-cil
  libjte1 libwebkitgtk-1.0-common x11-xkb-utils libcelt0-0 libdbus1.0-cil
  libwww-perl libgnome-desktop-2-17 libisofs6 libwebkitgtk-1.0-0 xfconf
  libjavascriptcoregtk-1.0-0 libvisual-0.4-0 libhttp-cookies-perl
  libxfconf-0-2 python-cupshelpers libhttp-message-perl libgnome-vfs2.0-cil
  libdjvulibre-text gstreamer0.10-plugins-base libzeitgeist-1.0-1 libaudit0
  gnote libgtkglext1 libnet-http-perl libetpan15 libmono-wcf3.0-cil keyutils
  libgupnp-igd-1.0-3 libmono-system2.0-cil libgnome2-canvas-perl libofa0
  libgdiplus libexpect-perl libnotify0.4-cil libvisual-0.4-plugins
  libgnomedesktop2.20-cil hwdata busybox
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  busybox-initramfs ifupdown initramfs-tools initramfs-tools-bin initscripts
  libacl1 libnih-dbus1 libnih1 libplymouth2 libpulse0 libudev0 mountall
  plymouth pulseaudio pulseaudio-utils udev upstart
Suggested packages:
  rdnssd pavumeter paman paprefs pulseaudio-module-raop avahi-daemon watershed
  graphviz
Recommended packages:
  plymouth-theme-ubuntu-text plymouth-theme pulseaudio-module-x11
  gstreamer0.10-pulseaudio pulseaudio-esound-compat rtkit
The following packages will be REMOVED:
  libpython2.7 sysvinit
The following NEW packages will be installed:
  busybox-initramfs initramfs-tools initramfs-tools-bin libnih-dbus1 libnih1
  libplymouth2 mountall plymouth pulseaudio pulseaudio-utils udev upstart
The following packages will be upgraded:
  ifupdown initscripts libacl1 libpulse0 libudev0
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  sysvinit
5 upgraded, 12 newly installed, 2 to remove and 891 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,609 kB of archives.
After this operation, 5,550 kB of additional disk space will be used.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Yes, do as I say!
E: Could not perform immediate configuration on 'initramfs-tools'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

I'm running a hp 2133 with 120 GB, 2 gb ram :confused:

---

### Post by jerrrys on 2011-12-11
Next to last line

Could not perform immediate configuration on 'initramfs-tools'.

I got this once and just went ahead with the install without problem.  But then, I have backup in place and I risk nothing if it would of went bad.

I do not remember the "Yes, do as I say!" response.  It was an earlier version, may of been different.

---


---
title: "Upgrade problems in terminal"
date: 2006-04-30
forum: General Help
---

### Post by Lomz on 2006-04-30
> lomz@Nero:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu13 is installed
  ubuntu-base: Depends: ubuntu-minimal but it is not installed
               Depends: ubuntu-standard but it is not installed
E: Unmet dependencies. Try using -f.
lomz@Nero:~$

Can some one please explain me this?
I cant run upgrade, dist-upgrade or install without having this error-message

---

### Post by Ramses de Norre on 2006-04-30
Have you tried sudo apt-get -f install yet?

---

### Post by Lomz on 2006-04-30
This is what happens then:
(I guess the most valueable informastion in this "quote" is the last line)
> lomz@Nero:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  alacarte apt apt-utils aptitude aspell at-spi binutils-static bluez-cups
  bluez-pcmcia-support bluez-pin bluez-utils brltty bsh ca-certificates
  cupsys-driver-gutenprint dictionaries-common dmidecode evince
  example-content fastjar festival festlex-cmu festlex-poslex
  festvox-kallpc16k firefox firefox-gnome-support foo2zjs
  foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters-ppds gcc-4.0-base
  gcj-4.1-base gconf2 gconf2-common gij-4.1 gimp-print
  gnome-accessibility-themes gnome-keyring gnome-mag gnome-screensaver
  gnopernicus gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-tools gtk2-engines-highcontrast gtkhtml3.8 hotkey-setup hpijs
  hplip hplip-data hplip-ppds ijsgutenprint inputattach irssi irssi-text
  iso-codes java-common java-gcj-compat language-selector
  language-selector-common launchpad-integration libaa1 libasound2 libaspell15
  libatspi1.0-0 libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-glib1 libavc1394-0 libbluetooth1 libbonobo2-0 libbonobo2-common
  libbrlapi1 libc6 libc6-dev libc6-i686 libcairo2 libcdio6 libcompfaceg1
  libcupsys2 libcupsys2-gnutls10 libdb4.3 libdbus-1-2 libdbus-glib-1-2
  libdjvulibre15 libdrm2 libecal1.2-3 libedataserver1.2-7 libegroupwise1.2-9
  libestools1.2 libexchange-storage1.2-1 libexif12 libflac7 libfontconfig1
  libfreetype6 libgail-gnome-module libgcc1 libgcj-common libgcj7 libgcj7-jar
  libgconf2-4 libgcrypt11 libgdl-1-0 libgdl-1-common libglib2.0-0
  libglib2.0-data libgnome-keyring0 libgnome-mag2 libgnome-menu2
  libgnome-speech3 libgnomecanvas2-0 libgnomecanvas2-common libgnomeprint2.2-0
  libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgnutls12
  libgpg-error0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtop2-7
  libgutenprint2 libgutenprintui2-1 libhal-storage1 libhal1 libhsqldb-java
  libicu34 libjaxp1.2-java libjessie-java libjline-java libkpathsea4 libkrb53
  liblaunchpad-integration0 liblpint-bonobo0 libmdbtools libnautilus-burn3
  libnautilus-extension1 libncurses5 libncursesw5 libneon25 libnotify1
  libnspr4 libnss3 libogg0 liboil0.3 libopal-2.2.0 libopencdk8
  libpam-foreground libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libperl5.8 libpoppler1 libpoppler1-glib libportaudio0 libpt-1.10.0
  libpt-plugins-v4l libscim8c2a libservlet2.3-java libsexy2 libsigc++-2.0-0c2a
  libslang2 libsndfile1 libsnmp-base libsnmp9 libsoup2.2-8 libssl0.9.8
  libstdc++6 libsysfs2 libtasn1-2 libtotem-plparser1 libusb-0.1-4 libvorbis0a
  libvorbisenc2 libvte-common libvte4 libwpd8c2a libxalan2-java
  libxerces2-java libxml2 libxmlsec1 libxmlsec1-nss libxmlsec1-openssl
  libxt-java linux-image-2.6.15-21-386 linux-image-386 linux-kernel-headers
  linux-restricted-modules-2.6.15-21-386 linux-restricted-modules-386
  linux-restricted-modules-common lsb-base min12xxw module-init-tools
  mozilla-firefox mozilla-firefox-locale-en-gb openssl pcmciautils perl
  perl-base perl-modules pmount python-apt python-gst0.10 python-vte
  python-xdg python2.4-apt python2.4-cairo python2.4-glade2 python2.4-gobject
  python2.4-gtk2 scim scim-gtk2-immodule scim-modules-socket synaptic
  tangerine-icon-theme tango-icon-theme ttf-arphic-ukai ttf-arphic-uming
  ttf-dejavu ttf-lao ttf-mgopen ttf-thai-tlwg ubuntu-standard usplash
  xscreensaver-data xserver-xorg-driver-neomagic
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-voodoo
  xserver-xorg-input-kbd xserver-xorg-input-mouse
Suggested packages:
  apt-doc libparse-debianchangelog-perl tasksel debtags aspell-doc spellutils
  python2.2 bluez-firmware libbrlapi1-dev brltty-flite brltty-x11 bsh-doc
  gutenprint-doc gutenprint-locales ispell emacsen-common jed-extra
  latex-xft-fonts libthai0 psutils gcj-4.1 libgcj7-awt kdeprint gtklp xpp
  python-qt3 irssi-scripts equivs libasound2-plugins glibc-doc manpages-dev
  libfreetype6-dev lib32gcj7-dbg rng-tools gnutls-bin gstreamer0.10-plugins
  libhsqldb-java-doc libjline-java-doc krb5-doc krb5-user libopal-dev
  ttf-thryomanes libxalan2-java-doc libbsf-java libxsltc-java
  libxerces2-java-doc lilo linux-doc-2.6.15 linux-source-2.6.15 nvidia-glx
  nvidia-glx-legacy avm-fritz-firmware-2.6.15-21 xprt-xprintorg
  libterm-readline-gnu-perl libterm-readline-perl-perl cryptsetup scim-uim
  scim-pinyin scim-hangul scim-chewing scim-m17n scim-prime scim-anthy
  scim-skk scim-canna scim-tables-additional scim-tables-ja scim-tables-ko
  scim-tables-zh dwww kdelibs-data xdelta
Recommended packages:
  aptitude-doc-en aptitude-doc gstreamer0.10-x libgcj7-src dbus gcc c-compiler
  notification-daemon libtasn1-2-bin perl-doc im-switch m17n-env deborphan
The following packages will be REMOVED:
  aspell-bin initrd-tools linux-image-2.6.10-5-386 linux-image-2.6.10-6-386
  linux-restricted-modules-2.6.10-6-386 lsb mozilla-firefox-gnome-support
  openoffice.org openoffice.org-bin openoffice.org-debian-files
  openoffice.org-gtk-gnome openoffice.org-help-en
  openoffice.org-hyphenation-en-gb openoffice.org-hyphenation-en-us
  openoffice.org-l10n-en ubuntu-base ubuntu-desktop
The following NEW packages will be installed:
  alacarte at-spi binutils-static bluez-cups bluez-pcmcia-support bluez-pin
  bluez-utils brltty bsh ca-certificates cupsys-driver-gutenprint evince
  example-content fastjar festival festlex-cmu festlex-poslex
  festvox-kallpc16k firefox firefox-gnome-support foo2zjs
  foomatic-db-gutenprint gcc-4.0-base gcj-4.1-base gconf2-common gij-4.1
  gimp-print gnome-accessibility-themes gnome-mag gnome-screensaver
  gnopernicus gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-tools gtk2-engines-highcontrast gtkhtml3.8 hotkey-setup hplip
  hplip-data hplip-ppds ijsgutenprint inputattach irssi iso-codes java-common
  java-gcj-compat language-selector language-selector-common
  launchpad-integration libaa1 libatspi1.0-0 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libbluetooth1
  libbrlapi1 libcairo2 libcdio6 libcompfaceg1 libcupsys2 libdbus-1-2
  libdbus-glib-1-2 libdjvulibre15 libdrm2 libecal1.2-3 libedataserver1.2-7
  libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libexif12 libflac7
  libgail-gnome-module libgcj-common libgcj7 libgcj7-jar libgdl-1-0
  libgdl-1-common libgnome-mag2 libgnome-menu2 libgnome-speech3
  libgnomevfs2-bin libgnomevfs2-extra libgnucrypto-java libgnutls12
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtkhtml2-0
  libgtkhtml3.8-15 libgtop2-7 libgutenprint2 libgutenprintui2-1
  libhal-storage1 libhal1 libhsqldb-java libicu34 libjaxp1.2-java
  libjessie-java libjline-java libkpathsea4 liblaunchpad-integration0
  liblpint-bonobo0 libmdbtools libnautilus-burn3 libneon25 libnotify1
  liboil0.3 libopal-2.2.0 libpam-foreground libpoppler1 libpoppler1-glib
  libportaudio0 libpt-1.10.0 libpt-plugins-v4l libscim8c2a libservlet2.3-java
  libsexy2 libsigc++-2.0-0c2a libslang2 libsndfile1 libsnmp-base libsnmp9
  libsoup2.2-8 libssl0.9.8 libstdc++6 libsysfs2 libtotem-plparser1 libwpd8c2a
  libxalan2-java libxerces2-java libxmlsec1 libxmlsec1-nss libxmlsec1-openssl
  libxt-java linux-image-2.6.15-21-386 linux-restricted-modules-2.6.15-21-386
  linux-restricted-modules-common min12xxw openssl pcmciautils python-gst0.10
  python-vte python2.4-apt python2.4-cairo python2.4-gobject scim
  scim-gtk2-immodule scim-modules-socket tangerine-icon-theme tango-icon-theme
  ttf-arphic-ukai ttf-arphic-uming ttf-dejavu ttf-lao ttf-mgopen ttf-thai-tlwg
  ubuntu-standard usplash xscreensaver-data xserver-xorg-driver-neomagic
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-voodoo
  xserver-xorg-input-kbd xserver-xorg-input-mouse
The following packages will be upgraded:
  apt apt-utils aptitude aspell dictionaries-common dmidecode
  foomatic-db-hpijs foomatic-filters-ppds gconf2 gnome-keyring hpijs
  irssi-text libasound2 libaspell15 libavc1394-0 libbonobo2-0
  libbonobo2-common libc6 libc6-dev libc6-i686 libcupsys2-gnutls10 libdb4.3
  libfontconfig1 libfreetype6 libgcc1 libgconf2-4 libgcrypt11 libglib2.0-0
  libglib2.0-data libgnome-keyring0 libgnomecanvas2-0 libgnomecanvas2-common
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgpg-error0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libkrb53 libnautilus-extension1 libncurses5 libncursesw5 libnspr4 libnss3
  libogg0 libopencdk8 libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libperl5.8 libtasn1-2 libusb-0.1-4 libvorbis0a libvorbisenc2 libvte-common
  libvte4 libxml2 linux-image-386 linux-kernel-headers
  linux-restricted-modules-386 lsb-base module-init-tools mozilla-firefox
  mozilla-firefox-locale-en-gb perl perl-base perl-modules pmount python-apt
  python-xdg python2.4-glade2 python2.4-gtk2 synaptic
79 upgraded, 167 newly installed, 17 to remove and 648 not upgraded.
7 not fully installed or removed.
Need to get 122kB/195MB of archives.
After unpacking 162MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main python-apt 0.6.16.2ubuntu5 [15.0kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main python2.4-apt 0.6.16.2ubuntu5 [71.2kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main pcmciautils 012-1ubuntu4 [28.7kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main inputattach 1.23-0ubuntu1 [7420B]
Fetched 122kB in 15s (7681B/s)
E: Internal Error, Could not perform immediate configuration (2) on libc6
lomz@Nero:~$


---

### Post by Ramses de Norre on 2006-04-30
Maybe this works:```
sudo rm /var/cache/apt/archives/libc6_2.3.5-1ubuntu12_i386.deb
sudo apt-get install -reinstall libc6
```

---


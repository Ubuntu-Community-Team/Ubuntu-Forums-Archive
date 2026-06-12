---
title: "Udgrading to dapper will remove alot of packages"
date: 2006-03-25
forum: General Help
---

### Post by daller on 2006-03-25
Hi there,

On all the computers I've tried to upgrade to dapper, it says:

---

The following packages will be removed:

adept akode akregator amarok amarok-gstreamer amarok-xine ark artsbuilder
  atlantik base-config busybox-cvs-initramfs camorama
  cupsys-driver-gimpprint-data dbus digikam gnome-sudoku gnomemeeting
  gtk2-engines-gtk-qt gwenview hal hotplug hplip-base ivman k3b k3b-mp3
  k3blibs kaddressbook kaffeine kaffeine-gstreamer kaffeine-xine kamera
  kappfinder karm kasteroids katapult kate katomic kaudiocreator kbackgammon
  kbattleship kblackbox kbounce kcontrol kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-dev
  kdebase-kio-plugins kdebluetooth kdegames kdegraphics-kfile-plugins
  kdelibs-bin kdelibs4-dev kdelibs4c2 kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources
  kdepim-wizards kdeprint kdesktop kdetv kdm kenolaba kfind kfouleggs
  kghostview kgoldrunner khelpcenter kicker kio-apt kio-locate kjumpingcube
  klaptopdaemon klickety klines klipper kmahjongg kmail kmenuedit kmilo kmines
  kmix knetworkconf knotes koffice-data koffice-libs kolf konq-plugins
  konqueror konqueror-nsplugins konquest konserve konsole kontact konversation
  kooka kopete korganizer kpat kpdf kpf kpoker kppp krdc kreversi krfb krita
  ksame kscd kscreensaver kshisen ksirtet ksmiletris ksmserver ksnake
  ksnapshot ksokoban kspaceduel ksplash ksplash-engine-moodin ksvg ksysguard
  ksystemlog ktron ktuberling kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager
  kwin kwin4 language-support-en libarts1c2 libbonoboui2-0 libcamel1.2-6
  libclan2-gui libclan2-jpeg libclan2-mikmod libclan2-png libclan2-sound
  libclan2-vorbis libclanlib2c2 libebook1.2-5 libedataserver1.2-4
  libegroupwise1.2-8 libgksu1.2-0 libgksuui1.0-0 libgnome2-0 libgnomeui-0
  libid3-3.8.3c2 libjack0.80.0-0 libkcal2b libkcddb1 libkdegames1 libkdepim1a
  libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 libmusicbrainz4c2
  libmyth-0.18.1 libopenexr2c2 libpanel-applet2-0 libsmpeg0c2 libtag1c2
  libtunepimp2c2 libwpd8c2 lskat netcdfg3 openoffice.org2 openoffice.org2-base
  openoffice.org2-calc openoffice.org2-common openoffice.org2-core
  openoffice.org2-draw openoffice.org2-help-en-us openoffice.org2-impress
  openoffice.org2-kde openoffice.org2-l10n-en-us openoffice.org2-math
  openoffice.org2-writer python-gnome2 python-gnome2-extras python-kde3
  python-uno python2.4-gnome2 python2.4-gnome2-extras python2.4-kde3
  sanekonsole x-common xmkmf xorg-common xorg-driver-synaptics xserver-common

...And therefore I haven't tried to go on!

It'll ruin my system, right?

---

### Post by DoeRayMe on 2006-03-25
Thats strange, does it try to install anything?

---

### Post by Barrakketh on 2006-03-25
Post your sources.list and the output of dist-upgrade.

---

### Post by daller on 2006-03-25
My sources.list:

```
deb http://wine.sourceforge.net/apt/ binary/
deb http://kubuntu.org/packages/kde351 breezy main
deb http://kubuntu.org/packages/amarok-1.3.8 breezy main
#deb http://blognux.free.fr/debian unstable main

## Uncomment the following two lines to fetch updated software from the network
deb http://dk.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://dk.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

And running dist-upgrade:

```

nikoline@ubuntu:~$ sudo apt-get dist-upgrade
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ... Færdig
Beregner opgraderingen... Færdig
Følgende pakker vil blive AFINSTALLERET: (REMOVED)
  adept akode akregator amarok amarok-gstreamer amarok-xine ark artsbuilder atlantik base-config busybox-cvs-initramfs camorama cupsys-driver-gimpprint-data dbus digikam gnome-sudoku gnomemeeting
  gtk2-engines-gtk-qt gwenview hal hotplug hplip-base ivman k3b k3b-mp3 k3blibs kaddressbook kaffeine kaffeine-gstreamer kaffeine-xine kamera kappfinder karm kasteroids katapult kate katomic
  kaudiocreator kbackgammon kbattleship kblackbox kbounce kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-dev kdebase-kio-plugins
  kdebluetooth kdegames kdegraphics-kfile-plugins kdelibs-bin kdelibs4-dev kdelibs4c2 kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdetv kdm kenolaba kfind kfouleggs kghostview kgoldrunner khelpcenter kicker kio-apt
  kio-locate kjumpingcube klaptopdaemon klickety klines klipper kmahjongg kmail kmenuedit kmilo kmines kmix knetworkconf knotes koffice-data koffice-libs kolf konq-plugins konqueror
  konqueror-nsplugins konquest konserve konsole kontact konversation kooka kopete korganizer kpat kpdf kpf kpoker kppp krdc kreversi krfb krita ksame kscd kscreensaver kshisen ksirtet ksmiletris
  ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktron ktuberling kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin kwin4 language-support-en libarts1c2 libbonoboui2-0 libcamel1.2-6 libclan2-gui libclan2-jpeg libclan2-mikmod libclan2-png
  libclan2-sound libclan2-vorbis libclanlib2c2 libebook1.2-5 libedataserver1.2-4 libegroupwise1.2-8 libgksu1.2-0 libgksuui1.0-0 libgnome2-0 libgnomeui-0 libid3-3.8.3c2 libjack0.80.0-0 libkcal2b
  libkcddb1 libkdegames1 libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 libmusicbrainz4c2 libmyth-0.18.1
  libopenexr2c2 libpanel-applet2-0 libsmpeg0c2 libtag1c2 libtunepimp2c2 libwpd8c2 lskat netcdfg3 openoffice.org2 openoffice.org2-base openoffice.org2-calc openoffice.org2-common
  openoffice.org2-core openoffice.org2-draw openoffice.org2-help-en-us openoffice.org2-impress openoffice.org2-kde openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer
  python-gnome2 python-gnome2-extras python-kde3 python-uno python2.4-gnome2 python2.4-gnome2-extras python2.4-kde3 sanekonsole x-common xmkmf xorg-common xorg-driver-synaptics xserver-common
Følgende NYE pakker vil blive installeret:
  app-install-data belocs-locales-bin busybox-initramfs ca-certificates cdrdao cupsys-driver-gutenprint docker example-content foo2zjs foomatic-db-gutenprint gcj-4.0-base gcj-4.1-base gconf2-common
  gettext gettext-kde gij-4.1 gsfonts-x11 hplip ijsgutenprint imlib-base imlib11 inputattach irssi kdesdk-scripts ladcca2 laptop-mode-tools libaldmb1 liballegro4.2 libarts1c2a libcamel1.2-8
  libclan2c2a-gui libclan2c2a-jpeg libclan2c2a-mikmod libclan2c2a-png libclan2c2a-sound libclan2c2a-vorbis libclanlib2c2a libcroco3 libcupsys2 libcurl3-gnutls libdbus-1-2 libdbus-1-dev
  libdbus-glib-1-2 libdmx1 libdns21 libdrm2 libdumb1 libedataserver1.2-7 libegroupwise1.2-9 libfaac0 libfluidsynth1 libgcj7 libgcj7-jar libgksu1.2-1 libgksuui1.0-1 libgmp3c2 libgnutls12
  libgsf-1-113 libgsf-1-common libgutenprint2 libicu34 libid3-3.8.3c2a libisc11 libjack0.100.0-0 libjline-java liblwres9 libmagick9 libmp4v2-0 libmusicbrainz4c2a libmysqlclient15 libmyth-0.18.1c2a
  libneon25 libnetcdf3 libopenexr2c2a libpam-foreground libparted1.6-13 libpcrecpp0 libpoppler1 libpoppler1-qt libpopt-dev librsvg2-2 librsvg2-common librsync1 libscim8c2a libsepol1
  libsigc++-2.0-0c2a libsmpeg0 libsnmp9 libssl0.9.8 libsysfs2 libtag1c2a libtunepimp2c2a libuniconf4.2 libwavpack0 libwpd8c2a libwvstreams4.2-base libwvstreams4.2-extras libwxgtk2.6-0 libxdmcp-dev
  libxerces27 libxfont1 libxine-extracodecs libxine-main1 libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxplc0.3.13 libxvmc1 linux-image-2.6.15-19-k7 mcpp mdetect mesa-common-dev min12xxw mplayer
  mplayer-skins mysql-client-5.0 mysql-server-5.0 openoffice.org-l10n-common pcmciautils pykdeextensions python2.4-gobject python2.4-soappy radeontool rdiff-backup readline-common scim-qtimm
  smartdimmer sox ttf-arphic-ukai ttf-arphic-uming vim-runtime x11-common xserver-xorg-driver-all xserver-xorg-driver-sisusb xserver-xorg-driver-voodoo xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
Følgende pakker er blevet holdt tilbage:
  enigma libavahi-client-dev libavahi-common-dev libavahi-qt3-dev libgnomevfs2-0 libgnomevfs2-common libpt-plugins-alsa libpt-plugins-v4l
Følgende pakker vil blive opgraderet: (UPGRADED)
  acpi-support acpid adduser alsa-base alsa-utils amsn apache2 apache2-common apache2-mpm-prefork apache2-utils appres apt apt-utils aptitude arts aspell at base-files base-passwd bash bc
  beforelight bicyclerepair bind9-host binutils binutils-static bitmap bluez-cups bluez-pcmcia-support bluez-utils bogofilter bogofilter-bdb bogofilter-common bsdmainutils bsdutils bsh bzip2
  cdrecord chromium console-common console-data console-tools coreutils cpio cpp cpp-3.4 cpp-4.0 cron cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint dash dc debconf debconf-i18n
  debianutils debtags dhcp3-client dhcp3-common dictionaries-common diff discover1 discover1-data dmidecode dmsetup dnsutils doc-debian dpkg dpkg-dev dselect dvd+rw-tools dvdbackup editres eject
  enigma-data esound-common ethtool evms evms-ncurses fastjar fdutils fetchmail file findutils finger firefox flashplugin-nonfree flobopuyo fontconfig foomatic-db foomatic-db-engine
  foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod fortunes-min freeglut3 fstobdf ftp g++ g++-4.0 gaim gaim-data gamin gcc gcc-3.3-base gcc-3.4
  gcc-3.4-base gcc-4.0 gcc-4.0-base gconf2 gettext-base gij gij-4.0 gimp gimp-data gksu gnome-keyring gnupg grep grepmap groff-base grub gs-common gs-esp gstreamer0.8-alsa gstreamer0.8-audiofile
  gstreamer0.8-cdparanoia gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-flac gstreamer0.8-gsm gstreamer0.8-hermes gstreamer0.8-jpeg gstreamer0.8-mad gstreamer0.8-misc gstreamer0.8-musepack
  gstreamer0.8-oss gstreamer0.8-plugin-apps gstreamer0.8-sdl gstreamer0.8-speex gstreamer0.8-theora gstreamer0.8-tools gstreamer0.8-vorbis gstreamer0.8-x gzip hdparm hermes1 hicolor-icon-theme
  hostname hotkey-setup hpijs hplip-data hplip-ppds hspell hwdata iceauth ico ifrename ifupdown ijsgimpprint imagemagick imake info initramfs-tools initscripts installation-report iproute iptables
  iputils-arping iputils-ping iputils-tracepath irssi-text iso-codes jackd java-gcj-compat kdebase-data kdegames-card-data kdelibs-data ketm ketm-data klibc-utils klogd ksysguardd
  kubuntu-artwork-usplash language-pack-da language-pack-da-base language-pack-en language-pack-en-base language-pack-kde-da language-pack-kde-da-base language-pack-kde-en language-pack-kde-en-base
  launchpad-integration less lftp libaa1 libacl1 libacl1-dev libadns1 liballegro4.1 libao2 libapache2-mod-php4 libapr0 libarts1-dev libartsc0 libartsc0-dev libasound2 libasound2-dev libaspell-dev
  libaspell15 libatk1.0-0 libattr1 libattr1-dev libaudio-dev libaudio2 libavc1394-0 libbind9-0 libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-common libbz2-1.0 libbz2-dev libc6 libc6-dev
  libc6-i686 libcairo2 libconsole libcupsimage2 libcupsys2-dev libcupsys2-gnutls10 libcurl3 libdb1-compat libdb3 libdb4.2 libdb4.3 libdbd-mysql-perl libdbi-perl libdbus-qt-1-1c2 libdevmapper1.01
  libdirectfb-0.9-22 libdiscover1 libdv4 libdvdread3 libedit2 libelfg0 libesd0 libesd0-dev libevms-2.5 libfaad2-0 libflac++5c2 libflac7 libfontconfig1 libfontconfig1-dev libfontenc1 libfreetype6
  libfreetype6-dev libfribidi0 libfs6 libg2c0 libgadu3 libgail-common libgail17 libgamin-dev libgamin0 libgc1c2 libgcc1 libgcj-common libgcj6 libgconf2-4 libgcrypt11 libgcrypt11-dev libgd2-noxpm
  libgda2-3 libgda2-common libgeoip1 libggi2 libgii0 libgii0-target-x libgimp2.0 libgl1-mesa libgl1-mesa-dev libgl1-mesa-dri libglade2-0 libglib2.0-0 libglib2.0-dev libglu1-mesa libglu1-mesa-dev
  libgnokii2 libgnome-keyring0 libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common
  libgnomeui-common libgnucrypto-java libgnujaxp-java libgnujaxp-jni libgnutls11 libgnutls11-dev libgpg-error-dev libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgsl0
  libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgstreamer0.8-0 libgtk1.2 libgtk1.2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtksourceview-common
  libgtksourceview1.0-0 libgtkspell0 libhal-storage1 libhal1 libhsqldb-java libice-dev libice6 libid3tag0 libidl0 libidn11 libidn11-dev libijs-0.35 libimlib2 libisccc0 libisccfg1 libiw28
  libjessie-java libjpeg-progs libjpeg62 libjpeg62-dev libkadm55 libklibc libkrb5-dev libkrb53 liblaunchpad-integration0 libldap2 liblircclient0 liblockdev1 liblockfile1 libltdl3 liblua50
  liblua50-dev liblualib50 liblualib50-dev liblzo1 libmagic1 libmdbtools libmimelib1c2a libmodplug0c2 libmpcdec3 libmpeg2-4 libmyspell3c2 libmysqlclient14 libncurses5 libncursesw5 libneon24
  libnetpbm10 libnspr4 libnss3 libogg-dev libogg0 liboggflac3 liboil0.3 libopenal0 libopencdk8 libopencdk8-dev libopenexr-dev liborbit2 libpam-modules libpam-runtime libpam0g libpango1.0-0
  libpango1.0-common libpcap0.8 libpcre3 libpcre3-dev libperl5.8 libphysfs-1.0-0 libpisock8 libpng12-0 libpng12-dev libportaudio0 libpq4 libpythonize0 libqt3-headers libqt3-mt libqt3-mt-dev
  libqt3-mt-mysql libraptor1 librasqal0 librdf0 libreadline4 libreadline5 librecode0 libreiserfs0.3-0 libruby1.8 libsamplerate0 libsane libsasl2 libsasl2-dev libsasl2-modules libscrollkeeper0
  libsdl-net1.2 libsdl-ttf2.0-0 libsdl1.2debian libsdl1.2debian-oss libselinux1 libsensors3 libservlet2.3-java libshout3 libslang2 libslp1 libsm-dev libsm6 libsmbclient libsndfile1 libsnmp-base
  libsoup2.2-8 libspeex1 libsqlite3-0 libssl-dev libssl0.9.7 libstartup-notification0 libstdc++5 libstdc++6 libstdc++6-4.0-dev libtasn1-2 libtasn1-2-dev libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libtheora0 libtiff4 libtiff4-dev libtiffxx0c2 libungif4g libunicode-string-perl libusb-0.1-4 libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3 libwmf0.2-7
  libwnck-common libwnck18 libwrap0 libwxgtk2.4-1 libx11-6 libx11-dev libxalan2-java libxau-dev libxau6 libxaw7 libxcomposite1 libxcursor-dev libxcursor1 libxdamage1 libxdmcp6 libxerces2-java
  libxext-dev libxext6 libxfixes3 libxft-dev libxft2 libxi-dev libxi6 libxine1c2 libxinerama-dev libxinerama1 libxkbfile1 libxml2 libxml2-dev libxml2-utils libxmu-dev libxmu-headers libxmu6
  libxmuu1 libxosd2 libxp6 libxpm4 libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxslt1-dev libxslt1.1 libxss1 libxt-dev libxt-java libxt6 libxtrap6 libxtst6 libxv1 libxvidcore4
  libxxf86dga1 libxxf86misc1 libxxf86vm1 liby2-14 libzvbi-common libzvbi0 linux-image-k7 linux-kernel-headers linux-restricted-modules-common linux-sound-base listres locales login logrotate
  lsb-base lsb-release lshw lshw-common lsof lua50 lvm-common lvm2 mailx make makedepend makedev manpages mawk mdadm memtest86+ menu-xdg mime-support mkisofs module-init-tools mount
  mozilla-firefox-locale-en-gb mozilla-mplayer mplayer-386 myspell-en-gb myspell-en-us mysql-client mysql-common mysql-server mythtv mythtv-backend mythtv-common mythtv-database mythtv-frontend
  nano ncurses-base ncurses-bin net-tools netbase netcat netpbm ntpdate nvidia-glx-legacy nvidia-kernel-common oclock odbcinst1debian1 openssh-client openssl parted passwd pciutils pcmcia-cs perl
  perl-base perl-modules perl-suid php4 php4-common php4-mysql phpmyadmin pingus pingus-data pkg-config planetpenguin-racer planetpenguin-racer-data pmount popularity-contest poster postfix
  powermanagement-interface powermgmt-base powernowd ppp pppconfig procps psmisc psutils python python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-geoip python-glade2 python-gtk2
  python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-minimal python-mysqldb python-netcdf python-numeric python-opengl
  python-osd python-pam python-parted python-pexpect python-pgsql python-pisock python-pygame python-pylibacl python-pyopenssl python-pyorbit python-pyxattr python-reportlab python-simpletal
  python-soappy python-sqlite python-syck python-tk python-unit python-xdg python-xml python2.4 python2.4-adns python2.4-apt python2.4-cairo python2.4-clientcookie python2.4-crypto python2.4-dbus
  python2.4-dev python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-glade2 python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging
  python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-minimal python2.4-mysqldb python2.4-numeric
  python2.4-numeric-ext python2.4-opengl python2.4-osd python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pygame python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit
  python2.4-pyxattr python2.4-qt3 python2.4-reportlab python2.4-simpletal python2.4-sip4-qt3 python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml qca-tls qobex qt3-dev-tools
  rafkill rafkill-data readahead reiser4progs reportbug rsync ruby1.8 samba-common sane-utils scorched3d scorched3d-data screen scrollkeeper scummvm searchandrescue searchandrescue-common sed
  sessreg shared-mime-info slocate smbclient smproxy speedcrunch ssl-cert sudo supertux supertux-data sysklogd sysv-rc sysvinit tar tcl8.4 tcpd tcpdump telnet tk8.4 toshset ttf-arabeyes
  ttf-arphic-bkai00mp ttf-bengali-fonts ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-malayalam-fonts ttf-mgopen ttf-opensymbol
  ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ubuntu-minimal ubuntu-standard ucf udev unzip usbutils usplash util-linux vbetool viewres vim vim-common vorbis-tools w3m
  wamerican wbritish wget wine wireless-tools wvdial x-dev x-ttcidfont-conf x-window-system-core x11perf x11proto-core-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xauth xbase-clients xbiff xcalc xclipboard xclock xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-100dpi
  xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils xfontsel xfsprogs xgamma xgc xhost xinit xkbutils xkeyboard-config xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman xmessage xmms
  xmodmap xmore xpdf-common xpdf-utils xpmutils xprop xrandr xrdb xrefresh xresprobe xrgb xserver-xorg xserver-xorg-core xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati
  xserver-xorg-driver-chips xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix xserver-xorg-driver-dummy xserver-xorg-driver-fbdev xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt xserver-xorg-driver-mga xserver-xorg-driver-neomagic xserver-xorg-driver-newport xserver-xorg-driver-nsc
  xserver-xorg-driver-nv xserver-xorg-driver-rendition xserver-xorg-driver-s3 xserver-xorg-driver-s3virge xserver-xorg-driver-savage xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga
  xserver-xorg-driver-via xserver-xorg-driver-vmware xserver-xorg-input-acecad xserver-xorg-input-aiptek xserver-xorg-input-calcomp xserver-xorg-input-citron xserver-xorg-input-digitaledge
  xserver-xorg-input-dmc xserver-xorg-input-dynapro xserver-xorg-input-elographics xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd xserver-xorg-input-magellan
  xserver-xorg-input-microtouch xserver-xorg-input-mouse xserver-xorg-input-mutouch xserver-xorg-input-palmax xserver-xorg-input-penmount xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xset xsetmode xsetpointer xsetroot xsm xstdcmap xterm xtrap xutils xvidtune xvinfo xwd xwininfo xwud zenity zlib1g zlib1g-dev
919 opgraderes, 138 nyinstalleres, 211 afinstalleres og 8 opgraderes ikke.
554MB/567MB skal hentes fra arkiverne.
Efter udpakning vil 293MB diskplads blive frigjort.


```

---

### Post by Barrakketh on 2006-03-25
Comment out these two lines:
```
deb http://kubuntu.org/packages/kde351 breezy main
deb http://kubuntu.org/packages/amarok-1.3.8 breezy main
```
update then dist-upgrade.  amaroK 1.3.8 and KDE 3.5.1 are already in Dapper and those packages are for Breezy.  You'll need to reboot after the upgrade as some low level things like udev have been upgraded.

---

### Post by daller on 2006-03-25
Tried that, just after posting... - Didn't work!

---

### Post by daller on 2006-03-25
Commenting everything else than:

deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) dapper main restricted

...Didn't work either!

---

### Post by Barrakketh on 2006-03-25
One more thing to try...you probably should've posted this in the forum for Dapper :)

```
sudo apt-get clean
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo touch /etc/apt/sources.list
sudo apt-get update
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```
Again, if that doesn't work try asking in the Dapper forums.

Just for reference purposes, this is the sources.list I had when I dist-upgraded to dapper:
```
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu dapper universe
 deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#Package entries for multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper multiverse
```

The only differences I see between mine and yours is that you're using the Dapper Backports repository (aside from the mirror we're using), and the wine repository.

---

### Post by JamesNorris on 2006-03-25
I dont speak Dutch, but I am quite sure that that's normal...

It removes packages that have changed their names or that need removing for dependencies to be upgraded, then reinstalls them afterwards.

Say, for example, your installed version of x requires a version of y between versions 1 and 1.3, but upgrading to dapper upgrades y to version 1.5, x will no longer work. As a result, apt removes both x and y to install updated versions of them with the correct dependencies.

Sorry if I didn't make much sence, I have dyselxia and have a hard time making things like this make sence to anyone other than me.

---

### Post by daller on 2006-03-25
I posted it here because I see it as a breezy-issue, not (or at least not much) a dapper-issue...

btw: what does "touch" do?

---

### Post by daller on 2006-03-25
[QUOTE=JamesNorris]
Say, for example, your installed version of x requires a version of y between versions 1 and 1.3, but upgrading to dapper upgrades y to version 1.5, x will no longer work. As a result, apt removes both x and y to install updated versions of them with the correct dependencies.[/QUOTE]

Well, it just seems that the packages are not going to be installed afterwards... (according to the output!)

Shouldn't I be worried?

---

### Post by Barrakketh on 2006-03-25
Do you have kubuntu-desktop package installed?
```
dpkg -l kubuntu-desktop | grep '^ii'
```
> btw: what does "touch" do?
It updates the timestamp on a file, and if the file doesn't exist, creates it.

---

### Post by daller on 2006-03-26
nikoline@ubuntu:~$ dpkg -l kubuntu-desktop | grep '^ii'
ii  kubuntu-desktop 0.55           Kubuntu desktop system
nikoline@ubuntu:~$

---

Trying to install kubuntu-desktop:

Følgende pakker har uopfyldte afhængigheder: (BROKEN DEPENDENCIES)
  kubuntu-desktop: Afhængigheder: kdnssd men den bliver ikke installeret
                   Afhængigheder: keep men den bliver ikke installeret
                   Afhængigheder: libarts1-akode men den bliver ikke installeret
                   Afhængigheder: openoffice.org-kde men den bliver ikke installeret
                   Afhængigheder: skim men den bliver ikke installeret
E: Ødelagte pakker (BROKEN PACKAGES)

---

### Post by Barrakketh on 2006-03-26
What's "men den bliver ikke installeret"?

---

### Post by lupine_nickt on 2006-03-26
I *think* it's saying "package x is required, but cannot be installed" -- intertran says the bit you asked about means:  "however the proves no installed", lol. 

So it can't install kubuntu-desktop because it can't meet the following dependencies:- kdnssd, keep, libarts1-akode, openoffice.org-kde and skim -- which is strange, because they're all available. 

That's my best guess, anyway. I don't have kubuntu-desktop installed; my upgrade to dapper went off with only one hitch (which I bugreported, and which has now been repaired. Fast :) ). 

xF,

...Nick

---

### Post by patrixl on 2006-03-26
I had the same thing... All I did after the upgrade was re-install kubuntu-desktop  (and ubuntu-desktop , sin ceI have both gnome and kde), and that fixed it all. 

Notice that only KDE packages and openoffice are being removed.

My system is fine and healthy, had no problem.

And of course, remember that Dapper is not yet out of beta stage, so upgrade/use at your own risk! ;)

---

### Post by daller on 2006-03-26
Guess I'll just wait a few days!

...What date is the release planed for?

You are right about the translation-thing :D

Danish sucks! - Back to good ol' babylon! :D

---

### Post by arcanistherogue on 2006-03-26
Heh, I'm a kubuntu user so I'll look out for these errors and post similar problems when I upgrade in about 10 minutes.  

i would also like to know the official release, I have to order myself some more CDs :-D

---

### Post by Barrakketh on 2006-03-26
In June.

---

### Post by daller on 2006-03-27
[QUOTE=Barrakketh]In June.[/QUOTE]

June???

That would be 6.06 :D

I mean, what day in April?

---

### Post by PsyberOneZero on 2006-03-27
[QUOTE=daller]June???

That would be 6.06 :D

I mean, what day in April?[/QUOTE]

They pushed the release date back 6 weeks for QA and UI Polishing. So yes it will be 6.06 :D

just glancing at your problem, the openoffice2 packages are safe to remove, they re-re-named them back to openoffice.  If you really want to do this use adept and try updating a few packages at a time and see what needs what dependency and what it will install/remove.  Make sure everything is backed up first this could be messy.

---

### Post by patrixl on 2006-03-28
WEll like I said already, I had the same thing, and it wasn't messy at all. Reinstalling kubuntu-desktop and ubuntu-desktop (cause I have both GNOME and KDE) after the upgrade fixed it. I did it from the command line of course.

---


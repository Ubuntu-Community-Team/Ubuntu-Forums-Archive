---
title: "Update error"
date: 2010-11-04
forum: General Help
---

### Post by Jonners59 on 2010-11-04
On my Toshiba, 32-bit Laptop I opened Update Manager and tried to install the new 10.10 update but got the following error message.

Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

The apt.log
[HTML]Log time: 2010-11-04 22:21:59.892597
Log time: 2010-11-04 22:22:01.436396
Log time: 2010-11-04 22:22:19.771927
  Installing libawl-php as Depends of davical
  Installing xserver-xorg-core as Depends of xserver-xorg
    Installing xserver-common as Depends of xserver-xorg-core
    Installing libxfont1 as Depends of xserver-xorg-core
      Installing libdrm-intel1 as Depends of xserver-xorg-video-intel
      Installing libdrm-nouveau1 as Depends of xserver-xorg-video-nouveau
  Installing gconf2 as Depends of ubuntuone-client
    Installing libgconf2-4 as Depends of gconf2
      Installing libglib2.0-0 as Depends of libgconf2-4
        new important dependency: libdconf0
        Installing libdconf0 as Recommends of libglib2.0-0
      Installing gconf2-common as Depends of libgconf2-4
  Installing python-ubuntuone-client as Depends of ubuntuone-client
    Installing python-ubuntuone-storageprotocol as Depends of python-ubuntuone-client
  Installing ubuntu-sso-client as Depends of ubuntuone-client
    Installing dpkg as PreDepends of ubuntu-sso-client
  Installing libappindicator1 as Depends of policykit-1-gnome
    Installing libdbus-glib-1-2 as Depends of libappindicator1
    Installing libdbusmenu-glib1 as Depends of libappindicator1
    Installing libdbusmenu-gtk1 as Depends of libappindicator1
      Installing libgdk-pixbuf2.0-0 as Depends of libdbusmenu-gtk1
    Installing libindicator1 as Depends of libappindicator1
    Installing indicator-application as Recommends of libappindicator1
  Installing libc6 as Depends of mono-2.0-gac
    Installing libc-bin as Depends of libc6
  Installing libmono-corlib2.0-cil as Depends of mono-2.0-gac
    Installing mono-runtime as Depends of libmono-corlib2.0-cil
      Installing mono-gac as Depends of mono-runtime
  Installing libmono-security2.0-cil as Depends of mono-2.0-gac
    Installing libmono-system2.0-cil as Depends of libmono-security2.0-cil
  Installing python-gtk2 as Depends of python-gtk2-dev
    Installing libgtk2.0-0 as Depends of python-gtk2
  Installing libboost-python1.42.0 as Depends of python-tagpy
  Installing libcairo2 as Depends of f-spot
    Installing libpixman-1-0 as Depends of libcairo2
  Installing libglib2.0-cil as Depends of f-spot
  Installing libgtk2.0-cil as Depends of f-spot
  Installing libmono-simd2.0-cil as Depends of f-spot
  Installing libmono-system-data2.0-cil as Depends of f-spot
    Installing libmono-data-tds2.0-cil as Depends of libmono-system-data2.0-cil
    Installing libmono-wcf3.0-cil as Depends of libmono-system-data2.0-cil
      Installing libmono-system-messaging2.0-cil as Depends of libmono-wcf3.0-cil
        Installing libmono-messaging2.0-cil as Depends of libmono-system-messaging2.0-cil
  Installing libsqlite3-0 as Depends of f-spot
  Installing libpopt0 as Depends of libpopt-dev
  Installing libgstreamer0.10-0 as Depends of gstreamer0.10-alsa
  Installing libgstreamer-plugins-base0.10-0 as Depends of gstreamer0.10-alsa
  Installing geoclue as Depends of geoclue-localnet
  Installing libgensec0 as Depends of libdcerpc0
    Installing libndr-standard0 as Depends of libgensec0
      Installing libsamba-util0 as Depends of libndr-standard0
  Installing libregistry0 as Depends of libdcerpc0
  Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing libkrb5support0 as Depends of libkrb5-3
  Installing libgnomekbd-common as Depends of libgnomekbd4
  Installing perl as Depends of libpurple0
    Installing perl-base as Depends of perl
    Installing perl-modules as Depends of perl
  Installing python as Depends of python-twisted-names
    Installing python2.6 as Depends of python
      Installing python2.6-minimal as Depends of python2.6
        Installing libssl0.9.8 as Depends of python2.6-minimal
      Installing libncursesw5 as Depends of python2.6
    Installing python-minimal as Depends of python
  Installing python-twisted-core as Depends of python-twisted-names
    Installing python-twisted-bin as Depends of python-twisted-core
  Installing syslinux-common as Depends of syslinux
    Installing libcrypt-passwdmd5-perl as Recommends of syslinux-common
  Installing libtime-modules-perl as Depends of backuppc
  Installing libboost-filesystem1.42.0 as Depends of pokerth
    Installing libboost-system1.42.0 as Depends of libboost-filesystem1.42.0
  Installing libboost-iostreams1.42.0 as Depends of pokerth
  Installing libboost-regex1.42.0 as Depends of pokerth
  Installing libboost-thread1.42.0 as Depends of pokerth
  Installing libqtcore4 as Depends of pokerth
  Installing pokerth-data as Depends of pokerth
  Installing libavutil50 as Depends of libswscale0
  Installing gcc-4.5-base as Depends of libstdc++6
  Installing language-pack-gnome-it as Depends of language-pack-gnome-it-base
    Installing language-pack-it-base as Depends of language-pack-gnome-it
      Installing language-pack-it as Depends of language-pack-it-base
  Installing libkdecore5 as Depends of kubuntu-debug-installer
    Installing liblzma2 as Depends of libkdecore5
    Installing libqt4-dbus as Depends of libkdecore5
      Installing libqt4-xml as Depends of libqt4-dbus
    Installing libqt4-network as Depends of libkdecore5
  Installing libkdeui5 as Depends of kubuntu-debug-installer
    Installing libdbusmenu-qt2 as Depends of libkdeui5
      Installing libqtgui4 as Depends of libdbusmenu-qt2
        Installing libmng1 as Depends of libqtgui4
    Installing libqt4-svg as Depends of libkdeui5
    Installing kdelibs5-data as Recommends of libkdeui5
  Installing libqapt1 as Depends of kubuntu-debug-installer
    Installing apt as Depends of libqapt1
      new important dependency: gpg
  Installing qapt-batch as Depends of kubuntu-debug-installer
    Installing libqapt-runtime as Depends of qapt-batch
  Installing libappindicator0.1-cil as Depends of tomboy
  Installing libbz2-1.0 as Depends of bzip2
  Installing libnotify1 as Depends of ekiga
  Installing libopal3.6.8 as Depends of ekiga
    Installing libpt2.6.7 as Depends of libopal3.6.8
    Installing libsrtp0 as Depends of libopal3.6.8
  Installing libespeak1 as Depends of espeak
    Installing libportaudio2 as Depends of libespeak1
      Installing libjack-jackd2-0 as Depends of libportaudio2
    Installing espeak-data as Depends of libespeak1
  Installing libnih1 as Depends of libnih-dbus1
  Installing computer-janitor as Depends of computer-janitor-gtk
    Installing python-argparse as Depends of computer-janitor
  Installing openoffice.org-core as Depends of openoffice.org-gnome
    Installing openoffice.org-common as Depends of openoffice.org-core
    Installing libhunspell-1.2-0 as Depends of openoffice.org-core
    Installing libneon27-gnutls as Depends of openoffice.org-core
    Installing ure as Depends of openoffice.org-core
      Installing uno-libs3 as Depends of ure
  Installing libgnomeui-0 as Depends of libgnomeui-dev
  Installing libkio5 as Depends of kmahjongg
    Installing libnepomuk4 as Depends of libkio5
      Installing libsoprano4 as Depends of libnepomuk4
        Installing soprano-daemon as Depends of libsoprano4
    Installing libsolid4 as Depends of libkio5
    Installing kdelibs5-plugins as Recommends of libkio5
      Installing libkatepartinterfaces4 as Depends of kdelibs5-plugins
        Installing libkparts4 as Depends of libkatepartinterfaces4
        Installing libktexteditor4 as Depends of libkatepartinterfaces4
        Installing libkutils4 as Depends of libkatepartinterfaces4
        Installing libqt4-script as Depends of libkatepartinterfaces4
      Installing libkfile4 as Depends of kdelibs5-plugins
      Installing libkhtml5 as Depends of kdelibs5-plugins
        Installing libkjsapi4 as Depends of libkhtml5
        Installing libphonon4 as Depends of libkhtml5
      Installing libkjsembed4 as Depends of kdelibs5-plugins
      Installing libkntlm4 as Depends of kdelibs5-plugins
      Installing libkrosscore4 as Depends of kdelibs5-plugins
      Installing libkrossui4 as Depends of kdelibs5-plugins
      Installing kdoctools as Depends of kdelibs5-plugins
      Installing kdelibs-bin as Depends of kdelibs5-plugins
  Installing kdegames-mahjongg-data as Depends of kmahjongg
  Installing librpm1 as Depends of rpm2cpio
    Installing librpmio1 as Depends of librpm1
    Installing rpm-common as Depends of librpm1
  Installing libedataserverui1.2-8 as Depends of libedataserverui1.2-dev
  Installing libutouch-grail1 as Depends of xserver-xorg-input-evdev
    Installing libmtdev1 as Depends of libutouch-grail1
  Installing libkde3support4 as Depends of cervisia
    Installing libkpty4 as Depends of libkde3support4
      Installing libutempter0 as Depends of libkpty4
    Installing libqt4-qt3support as Depends of libkde3support4
      Installing libqt4-designer as Depends of libqt4-qt3support
      Installing libqt4-sql as Depends of libqt4-qt3support
  Installing libprotobuf6 as Depends of libcompizconfig0
  Installing update-manager-core as Depends of update-manager
  Installing openoffice.org-base-core as Depends of openoffice.org-writer
  Installing libqtassistantclient4 as Depends of libqt4-assistant
  Installing libenet0debian1 as Depends of supertuxkart
  Installing supertuxkart-data as Depends of supertuxkart
  Installing python-gconf as Depends of python-gnome2
  Installing python3 as Depends of python3-all
    Installing python3.1 as Depends of python3
      Installing python3.1-minimal as Depends of python3.1
    Installing python3-minimal as Depends of python3
  Installing gnome-media-common as Depends of gnome-media
  Installing python3.1-dbg as Depends of python3-dbg
  Installing nautilus-data as Depends of nautilus
  Installing libtasn1-3 as Depends of libtasn1-3-dev
  Installing gnome-games-common as Depends of aisleriot
  Installing libgnome2-common as Depends of libgnome2-0
  Installing audacity as Depends of audacity-dbg
    Installing audacity-data as Depends of audacity
    Installing libwxbase2.8-0 as Depends of audacity
    Installing libwxgtk2.8-0 as Depends of audacity
    previously satisfied important dependency on libavcodec52
    Installing libavcodec52 as Recommends of audacity
      Installing libva1 as Depends of libavcodec52
    previously satisfied important dependency on libavformat52
    Installing libavformat52 as Recommends of audacity
  Installing libusb-1.0-0 as Depends of libdc1394-22
  Installing libbind9-60 as Depends of bind9-host
    Installing libdns66 as Depends of libbind9-60
      Installing libgeoip1 as Depends of libdns66
  Installing libisc60 as Depends of bind9-host
  Installing libisccfg60 as Depends of bind9-host
  Installing liblwres60 as Depends of bind9-host
  Installing openoffice.org-draw as Depends of openoffice.org-impress
  Installing librasqal2 as Depends of slv2-jack
  Installing language-pack-en as Depends of language-pack-en-base
  Installing gvfs as Depends of gvfs-fuse
  Installing erlang-base as Depends of erlang-inets
    previously satisfied important dependency on erlang-crypto
    Installing erlang-crypto as Recommends of erlang-base
    previously satisfied important dependency on erlang-syntax-tools
    Installing erlang-syntax-tools as Recommends of erlang-base
  Installing erlang-mnesia as Depends of erlang-inets
  Installing erlang-runtime-tools as Depends of erlang-inets
  Installing erlang-ssl as Depends of erlang-inets
    Installing erlang-public-key as Depends of erlang-ssl
  Installing python-markupsafe as Depends of python-mako
  Installing linux-headers-2.6.35-22-generic as Depends of linux-headers-generic
    Installing linux-headers-2.6.35-22 as Depends of linux-headers-2.6.35-22-generic
  Installing libaspell15 as Depends of aspell
  Installing backintime-common as Depends of backintime-gnome
  Installing dhcp3-common as Depends of dhcp3-client
  Installing libavidemux0 as Depends of avidemux-cli
  Installing wx2.8-headers as Depends of libwxbase2.8-dev
  Installing libgcj-common as Depends of libgcj-bc
  Installing libgcj10 as Depends of libgcj-bc
    Installing gcj-4.4-base as Depends of libgcj10
    previously satisfied important dependency on gcj-4.4-jre-lib
    Installing gcj-4.4-jre-lib as Recommends of libgcj10
  Installing libdirectfb-1.2-9 as Depends of libxine1-x
  Installing libxine1-bin as Depends of libxine1-x
  Installing libsoup2.4-1 as Depends of libsoup2.4-dev
  Installing libsnmp-base as Depends of libsnmp15
  Installing libdjvulibre-text as Depends of libdjvulibre21
  Installing libnb-platform12-java as Depends of libnb-platform-devel-java
    Installing libequinox-osgi-java as Depends of libnb-platform12-java
    Installing libfelix-framework-java as Depends of libnb-platform12-java
    Installing libfelix-main-java as Depends of libnb-platform12-java
  Installing libcobertura-java as Depends of libnb-platform-devel-java
    Installing libasm3-java as Depends of libcobertura-java
  Installing libbindex-java as Depends of libnb-platform-devel-java
  Installing libmagickcore3 as Depends of obex-data-server
    Installing liblqr-1-0 as Depends of libmagickcore3
  Installing libmagickwand3 as Depends of obex-data-server
  Installing libdebconf-kde0 as Depends of kpackagekit
  Installing libpackagekit-qt-14 as Depends of kpackagekit
  Installing libglib2.0-bin as Depends of libglib2.0-dev
  Installing samba-common as Depends of smbclient
  Installing libnewt0.52 as Depends of whiptail
  Installing libvorbis0a as Depends of libvorbisfile3
  Installing plymouth as Depends of plymouth-x11
  Installing libgucharmap7 as Depends of gucharmap
  Installing libatspi1.0-0 as Depends of brltty-x11
  Installing brltty as Depends of brltty-x11
  Installing python-gmenu as Depends of python-gmenu-dbg
  Installing libnm-glib2 as Depends of network-manager
  Installing libnm-util1 as Depends of network-manager
  Installing libavahi-core7 as Depends of avahi-daemon
  Installing openjdk-6-jre as Depends of icedtea6-plugin
    Installing openjdk-6-jre-headless as Depends of openjdk-6-jre
      Installing openjdk-6-jre-lib as Depends of openjdk-6-jre-headless
      previously satisfied important dependency on icedtea-6-jre-cacao
      Installing icedtea-6-jre-cacao as Recommends of openjdk-6-jre-headless
  Installing libebook1.2-9 as Depends of libebook1.2-dev
  Installing libcorosync4 as Depends of libopenais3
  Installing gdebi-core as Depends of gdebi
    Installing python-apt as Depends of gdebi-core
      Installing apt-utils as Depends of python-apt
  Installing libucommon3 as Depends of libsipwitch0
  Installing libimobiledevice1 as Depends of upower
  Installing libupower-glib1 as Depends of upower
  Installing libclutter-1.0-0 as Depends of quadrapassel
  Installing libdbi0 as Depends of rrdtool
  Installing librrd4 as Depends of rrdtool
  Installing multisync as Depends of libmultisync-plugin-irmc
  Installing libgnome-desktop-2-17 as Depends of libgnome-desktop-dev
    new important dependency: hwdata
    Installing hwdata as Recommends of libgnome-desktop-2-17
  Installing xul-ext-ubufox as Depends of ubufox
  Installing libpulse0 as Depends of pulseaudio
  Installing libgnome-bluetooth8 as Depends of gnome-bluetooth
  Installing python-aptdaemon as Depends of python-aptdaemon-gtk
  Installing libpango1.0-0 as Depends of libpango1.0-dev
    Installing libpango1.0-common as Depends of libpango1.0-0
  Installing libgladeui-1-9 as Depends of libgnome-media0
  Installing wesnoth-1.8 as Depends of wesnoth
    Installing wesnoth-1.8-core as Depends of wesnoth-1.8
      Installing wesnoth-1.8-data as Depends of wesnoth-1.8-core
    Installing wesnoth-1.8-httt as Depends of wesnoth-1.8
    Installing wesnoth-1.8-tsg as Depends of wesnoth-1.8
    Installing wesnoth-1.8-trow as Depends of wesnoth-1.8
    Installing wesnoth-1.8-ttb as Depends of wesnoth-1.8
    Installing wesnoth-1.8-ei as Depends of wesnoth-1.8
    Installing wesnoth-1.8-utbs as Depends of wesnoth-1.8
    Installing wesnoth-1.8-did as Depends of wesnoth-1.8
    Installing wesnoth-1.8-nr as Depends of wesnoth-1.8
    Installing wesnoth-1.8-sof as Depends of wesnoth-1.8
    Installing wesnoth-1.8-sotbe as Depends of wesnoth-1.8
    Installing wesnoth-1.8-l as Depends of wesnoth-1.8
    Installing wesnoth-1.8-aoi as Depends of wesnoth-1.8
    Installing wesnoth-1.8-thot as Depends of wesnoth-1.8
    Installing wesnoth-1.8-low as Depends of wesnoth-1.8
    Installing wesnoth-1.8-dm as Depends of wesnoth-1.8
    Installing wesnoth-1.8-music as Recommends of wesnoth-1.8
  Installing gcc-4.4-base as Depends of g++-4.4
  Installing gcc-4.4 as Depends of g++-4.4
    Installing cpp-4.4 as Depends of gcc-4.4
      Installing libmpfr4 as Depends of cpp-4.4
    Installing binutils as Depends of gcc-4.4
    Installing libgcc1 as Depends of gcc-4.4
    Installing libgomp1 as Depends of gcc-4.4
  Installing libstdc++6-4.4-dev as Depends of g++-4.4
  Installing libcamel1.2-14 as Depends of libcamel1.2-dev
  Installing claws-mail as Depends of claws-mail-i18n
  Installing libglibmm-2.4-1c2a as Depends of gparted
  Installing libapache2-mod-php5 as Depends of php5
    Installing php5-common as Depends of libapache2-mod-php5
    new important dependency: php5-cli
    Installing php5-cli as Recommends of libapache2-mod-php5
  Installing totem as Depends of totem-plugins
    Installing libtotem-plparser17 as Depends of totem
    Installing gstreamer0.10-plugins-base as Depends of totem
    Installing totem-common as Depends of totem
    previously satisfied important dependency on totem-mozilla
    Installing totem-mozilla as Recommends of totem
  Installing libgdata7 as Depends of totem-plugins
  Installing libattica0 as Depends of kdebase-runtime
  Installing libkdesu5 as Depends of kdebase-runtime
  Installing libkdnssd4 as Depends of kdebase-runtime
  Installing libkmediaplayer4 as Depends of kdebase-runtime
  Installing libknewstuff3-4 as Depends of kdebase-runtime
  Installing libknotifyconfig4 as Depends of kdebase-runtime
  Installing libnepomukquery4a as Depends of kdebase-runtime
  Installing libplasma3 as Depends of kdebase-runtime
    Installing libkdewebkit5 as Depends of libplasma3
      Installing libqtwebkit4 as Depends of libkdewebkit5
    Installing libthreadweaver4 as Depends of libplasma3
  Installing kdebase-runtime-data as Depends of kdebase-runtime
  Installing plasma-scriptengine-javascript as Depends of kdebase-runtime
  new important dependency: virtuoso-minimal
  Installing virtuoso-minimal as Recommends of kdebase-runtime
    Installing virtuoso-opensource-6.1-bin as Depends of virtuoso-minimal
    Installing libvirtodbc0 as Depends of virtuoso-minimal
      Installing virtuoso-opensource-6.1-common as Depends of libvirtodbc0
  Installing libexchangemapi-1.0-0 as Depends of evolution-mapi
  Installing libecal1.2-7 as Depends of libecal1.2-dev
  Installing linux-image-2.6.35-22-generic as Depends of linux-image-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libgssdp-1.0-2 as Depends of libgstfarsight0.10-0
  Installing libgupnp-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libx264-98 as Depends of gstreamer0.10-plugins-ugly-multiverse
  Installing libmodplug1 as Depends of libxine1-misc-plugins
  Installing libmpcdec6 as Depends of libxine1-misc-plugins
  Installing libgcrypt11 as Depends of libgcrypt11-dev
  Installing libibus2 as Depends of ibus-gtk
  Installing libboost1.42-dev as Depends of libboost-dev
  Installing libkimproxy4 as Depends of kdelibs5
  Installing libknewstuff2-4 as Depends of kdelibs5
  Installing libopenr2-3 as Depends of asterisk
  Installing asterisk-config as Depends of asterisk
  Installing asterisk-sounds-main as Depends of asterisk
  Installing libhpmud0 as Depends of hpijs
  Installing koffice-libs as Depends of kthesaurus
    Installing kchart as Depends of koffice-libs
    Installing kdepim-runtime as Depends of koffice-libs
      Installing kdepimlibs-kio-plugins as Depends of kdepim-runtime
        Installing libkimap4 as Depends of kdepimlibs-kio-plugins
          Installing libkmime4 as Depends of libkimap4
        Installing libkldap4 as Depends of kdepimlibs-kio-plugins
      Installing libakonadi-kabc4 as Depends of kdepim-runtime
      Installing libakonadi-kcal4 as Depends of kdepim-runtime
        Installing libkcal4 as Depends of libakonadi-kcal4
          Installing libkabc4 as Depends of libkcal4
            Installing libkresources4 as Depends of libkabc4
          Installing libkpimutils4 as Depends of libkcal4
      Installing libakonadi-kde4 as Depends of kdepim-runtime
        Installing libakonadiprivate1 as Depends of libakonadi-kde4
          Installing libboost-program-options1.42.0 as Depends of libakonadiprivate1
      Installing libakonadi-kmime4 as Depends of kdepim-runtime
      Installing libmailtransport4 as Depends of kdepim-runtime
      Installing libmicroblog4 as Depends of kdepim-runtime
      Installing akonadi-server as Depends of kdepim-runtime
        Installing mysql-server-core-5.1 as Depends of akonadi-server
        Installing mysql-client-core-5.1 as Depends of akonadi-server
          Installing libmysqlclient16 as Depends of mysql-client-core-5.1
            Installing mysql-common as Depends of libmysqlclient16
    Installing koffice-data as Depends of koffice-libs
  Installing libprotoc6 as Depends of protobuf-compiler
  Installing libapr1 as Depends of apache2.2-bin
  Installing libvncserver0 as Depends of virtualbox-ose
  previously satisfied important dependency on virtualbox-ose-dkms
  Installing virtualbox-ose-dkms as Recommends of virtualbox-ose
  previously satisfied important dependency on virtualbox-ose-qt
  Installing virtualbox-ose-qt as Recommends of virtualbox-ose
  Installing cups-common as Depends of cups-client
  Installing ttf-lyx as Depends of latex-xft-fonts
  Installing libpostproc51 as Depends of mplayer
  Installing libvdpau1 as Depends of mplayer
  Installing language-pack-gnome-en as Depends of language-pack-gnome-en-base
  Installing libgnome-window-settings1 as Depends of gnome-control-center
  Installing capplets-data as Depends of gnome-control-center
  Installing libsasl2-2 as Depends of libsasl2-modules
  Installing libxi6 as Depends of libxi-dev
  Installing libsane-hpaio as Depends of hplip
  Installing hplip-data as Depends of hplip
  Installing hplip-cups as Depends of hplip
  Installing python-imaging as Depends of python-imaging-tk
  Installing libopensync1exp7 as Depends of opensync-plugin-file
    Installing opensync-format-vformat as Recommends of libopensync1exp7
    Installing opensync-format-xmlformat as Recommends of libopensync1exp7
  Installing libxrender1 as Depends of libxrender-dev
  Installing mono-csharp-shell as Depends of gbrainy
    Installing libmono-management2.0-cil as Depends of mono-csharp-shell
    Installing mono-gmcs as Depends of mono-csharp-shell
  Installing foomatic-db-compressed-ppds as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing ubuntu-extras-keyring as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: ibus-pinyin
  Installing ibus-pinyin as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing ibus-pinyin-db-open-phrase as Depends of ibus-pinyin
      Installing pinyin-database as Depends of ibus-pinyin-db-open-phrase
    Installing libopencc1 as Depends of ibus-pinyin
    Installing ibus as Depends of ibus-pinyin
      Installing python-ibus as Depends of ibus
  new important dependency: ibus-pinyin-db-android
  Installing ibus-pinyin-db-android as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: shotwell
  Installing shotwell as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libgee2 as Depends of shotwell
    Installing libgexiv2-0 as Depends of shotwell
  new important dependency: ttf-ubuntu-font-family
  Installing ttf-ubuntu-font-family as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  Installing libaccess-bridge-java as Depends of libaccess-bridge-java-jni
  Installing libept1 as Depends of aptitude
  Installing libqt4-dev as Depends of libqt4-opengl-dev
    Installing libqt4-scripttools as Depends of libqt4-dev
    Installing libqt4-xmlpatterns as Depends of libqt4-dev
    Installing libqt4-help as Depends of libqt4-dev
    Installing libqt4-declarative as Depends of libqt4-dev
    Installing qt4-qmake as Depends of libqt4-dev
    new important dependency: libqtwebkit-dev
    Installing libqtwebkit-dev as Recommends of libqt4-dev
  Installing python2.6-dbg as Depends of python-dbg
  Installing libfolks-telepathy0 as Depends of empathy
    Installing libfolks0 as Depends of libfolks-telepathy0
  Installing libtelepathy-logger1 as Depends of empathy
  Installing empathy-common as Depends of empathy
  Installing gnome-icon-theme as Depends of empathy
  Installing telepathy-logger as Depends of empathy
  Installing libgtkhtml-editor-common as Depends of libgtkhtml-editor0
  Installing libcairo-gobject2 as Depends of libcairo2-dev
  Installing libpixman-1-dev as Depends of libcairo2-dev
  Installing libxcb-shm0-dev as Depends of libcairo2-dev
    Installing libxcb-shm0 as Depends of libxcb-shm0-dev
  Installing python2.6-dev as Depends of python-dev
    Installing libpython2.6 as Depends of python2.6-dev
    Installing libssl-dev as Depends of python2.6-dev
  Installing google-gadgets-gst as Depends of google-gadgets-gtk
  Installing google-gadgets-xul as Depends of google-gadgets-gtk
  Installing libebackend1.2-0 as Depends of libebackend1.2-dev
  Installing gtk2-engines-murrine as Depends of light-themes
  Installing libvte9 as Depends of vinagre
  Installing libsvn1 as Depends of subversion
  Installing billard-gl-data as Depends of billard-gl
  Installing libxdmcp6 as Depends of libxdmcp-dev
  Installing libsysfs2 as Depends of libsysfs-dev
  Installing odbcinst1debian2 as Depends of odbcinst
  Installing libjetty-java as Depends of jetty
  Installing libavutil-extra-50 as Depends of libavcodec-extra-52
  Installing libavahi-client3 as Depends of libavahi-client-dev
  Installing libbluetooth3 as Depends of bluez
  Installing libgtk2.0-dev as Depends of libgail-dev
    Installing libgdk-pixbuf2.0-dev as Depends of libgtk2.0-dev
  Installing libsyncdaemon-1.0-1 as Depends of ubuntuone-client-gnome
  Installing apache2.2-common as Depends of apache2-mpm-prefork
  Installing libgutenprint2 as Depends of cups-driver-gutenprint
  Installing libffi5 as Depends of libffi-dev
  Installing gnome-terminal-data as Depends of gnome-terminal
  Installing e2fslibs as PreDepends of e2fsprogs
  new important dependency: zeitgeist-fts-extension
  Installing zeitgeist-fts-extension as Recommends of zeitgeist
  Installing libpng12-0 as Depends of libpng12-dev
  Installing grub-common as Depends of grub-pc
  previously satisfied important dependency on telepathy-mission-control-5
  Installing telepathy-mission-control-5 as Recommends of libmission-control-plugins0
  Installing libeina-svn-06 as Depends of libeet1
  Installing libeina-svn-05 as Depends of libevas-svn-05-engines-core
  Installing libruby1.8 as Depends of ruby1.8
  Installing baobab as Depends of gnome-utils
    Installing gnome-utils-common as Depends of baobab
  Installing gnome-dictionary as Depends of gnome-utils
  Installing gnome-screenshot as Depends of gnome-utils
  Installing gnome-search-tool as Depends of gnome-utils
  Installing gnome-system-log as Depends of gnome-utils
  Installing libboost-serialization1.42-dev as Depends of libboost-serialization-dev
    Installing libboost-serialization1.42.0 as Depends of libboost-serialization1.42-dev
  Installing aptdaemon as Depends of software-center
  new important dependency: sessioninstaller
  Installing sessioninstaller as Recommends of software-center
  Installing compiz-core as Depends of compiz-plugins
  Installing libxcursor1 as Depends of libxcursor-dev
  Installing libunistring0 as Depends of gettext
  Installing python-sip as Depends of python-qt4
  Installing at-spi as Depends of python-pyatspi
  new important dependency: gpg
  Installing libxmlrpc-core-c3 as Depends of cmake
  Installing default-jre as Depends of default-jdk
    Installing default-jre-headless as Depends of default-jre
  Installing libegroupwise1.2-13 as Depends of libegroupwise1.2-dev
  Installing libbonobo2-0 as Depends of libbonobo2-dev
    Installing libbonobo2-common as Depends of libbonobo2-0
  Installing libbrasero-media1 as Depends of rhythmbox-plugin-cdrecorder
    Installing libburn4 as Depends of libbrasero-media1
    Installing libisofs6 as Depends of libbrasero-media1
  Installing liblinphone3 as Depends of linphone
    Installing libmediastreamer0 as Depends of liblinphone3
      Installing libortp8 as Depends of libmediastreamer0
  Installing linphone-nox as Depends of linphone
    Installing libpoppler7 as Depends of cups
    Installing cups-ppdc as Depends of cups
  Installing libdvbpsi6 as Depends of vlc-nox
  Installing libebml2 as Depends of vlc-nox
  Installing libmatroska2 as Depends of vlc-nox
  Installing libvlc5 as Depends of vlc-nox
    Installing libvlccore4 as Depends of libvlc5
      Installing vlc-data as Depends of libvlccore4
  Installing speech-dispatcher as Depends of python-speechd
  Installing libperl5.10 as Depends of perl-suid
  Installing libgnokii6 as Depends of gnome-phone-manager
    Installing gnokii-common as Depends of libgnokii6
  Installing libdrm-radeon1 as Depends of libdrm-dev
  Installing libkms1 as Depends of libdrm-dev
  Installing libopenscenegraph65 as Depends of flightgear
    Installing libgdal1-1.6.0 as Depends of libopenscenegraph65
      Installing libgeos-c1 as Depends of libgdal1-1.6.0
        Installing libgeos-3.2.0 as Depends of libgeos-c1
      Installing libhdf4-0-alt as Depends of libgdal1-1.6.0
      Installing libhdf5-serial-1.8.4 as Depends of libgdal1-1.6.0
      Installing libnetcdf6 as Depends of libgdal1-1.6.0
      Installing libogdi3.2 as Depends of libgdal1-1.6.0
        Installing libproj0 as Depends of libogdi3.2
          Installing proj-data as Depends of libproj0
      Installing proj-bin as Recommends of libgdal1-1.6.0
    Installing libopenthreads13 as Depends of libopenscenegraph65
  Installing simgear1.9.1 as Depends of flightgear
  Installing usb-creator-common as Depends of usb-creator-gtk
  Installing mail-notification as Depends of mail-notification-evolution
  Installing language-selector-common as Depends of language-selector
  Installing libglewmx1.5 as Depends of libglc0
  Installing tzdata as Depends of tzdata-java
  Installing libgwibber0 as Depends of indicator-me
  Installing libxext6 as Depends of libxext-dev
  Installing libxapian15 as Depends of python-xapian
  Installing libjpeg62 as Depends of libjpeg62-dev
  Installing kvpnc-data as Depends of kvpnc
  Installing libaddresses0 as Depends of agenda.app
  Installing liblouis2 as Depends of python-louis
  Installing ubuntu-restricted-addons as Depends of ubuntu-restricted-extras
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing gstreamer0.10-fluendo-mp3 as Recommends of ubuntu-restricted-addons
    Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  Installing python-cups as Depends of system-config-printer-common
  Installing libxdamage1 as Depends of libxdamage-dev
  Installing libevdocument3 as Depends of evince
    Installing libpoppler-glib5 as Depends of libevdocument3
    Installing libt1-5 as Depends of libevdocument3
  Installing libevview3 as Depends of evince
  Installing evince-common as Depends of evince
  Installing openbve-data as Depends of openbve
  Installing zlib1g as Depends of zlib1g-dev
  Installing libtiff4 as Depends of libtiff4-dev
  Installing libtiffxx0c2 as Depends of libtiff4-dev
  Installing libfreetype6 as Depends of libfreetype6-dev
  Installing libwbclient0 as Depends of samba
  Installing libnb-ide13-java as Depends of netbeans
  Installing libnb-java4-java as Depends of netbeans
    Installing libnb-javaparser-java as Depends of libnb-java4-java
  Installing libnb-apisupport2-java as Depends of netbeans
  Installing librpmbuild1 as Depends of rpm
  Installing libstreams0 as Depends of libstreamanalyzer0
  Installing librtmp0 as Depends of gstreamer0.10-plugins-bad
  Installing libzbar0 as Depends of gstreamer0.10-plugins-bad
  Installing libsox1b as Depends of libsox-fmt-base
  Installing evolution-data-server-common as Depends of evolution-data-server
  Installing libdmapsharing2 as Depends of rhythmbox-plugins
  Installing libvala-0.10-0 as Depends of rhythmbox-plugins
  Installing libpackagekit-glib2-14 as Depends of packagekit
  Installing packagekit-backend-aptcc as Depends of packagekit
  previously satisfied important dependency on indicator-application
  Installing libgimp2.0 as Depends of gimp
    previously satisfied important dependency on gimp-data
    Installing gimp-data as Recommends of libgimp2.0
  Installing libva-x11-1 as Depends of vlc
  Installing libxcb-randr0 as Depends of vlc
  new important dependency: vlc-plugin-notify
  Installing vlc-plugin-notify as Recommends of vlc
  previously satisfied important dependency on vlc-plugin-pulse
  Installing vlc-plugin-pulse as Recommends of vlc
  Installing libgpgme++2 as Depends of kdepimlibs5
  Installing libkblog4 as Depends of kdepimlibs5
    Installing libkxmlrpcclient4 as Depends of libkblog4
    Installing libsyndication4 as Depends of libkblog4
  Installing libkholidays4 as Depends of kdepimlibs5
  Installing libkpimidentities4 as Depends of kdepimlibs5
    Installing libkpimtextedit4 as Depends of libkpimidentities4
  Installing libktnef4 as Depends of kdepimlibs5
  Installing libqgpgme1 as Depends of kdepimlibs5
  Installing libgl1-mesa-glx as Depends of libgl1-mesa-dev
  Installing libgtkhtml3.14-19 as Depends of libgtkhtml3.14-dev
  Installing gsfonts as Depends of ghostscript
  Installing git as Depends of git-core
  new important dependency: libmagickcore3-extra
  Installing libmagickcore3-extra as Recommends of imagemagick
    Installing libcdt4 as Depends of libmagickcore3-extra
    Installing libgraph4 as Depends of libmagickcore3-extra
    Installing libgvc5 as Depends of libmagickcore3-extra
      Installing libpathplan4 as Depends of libgvc5
      Installing libxdot4 as Depends of libgvc5
  new important dependency: netpbm
  Installing netpbm as Recommends of imagemagick
    Installing libnetpbm10 as Depends of netpbm
  Installing liboobs-1-5 as Depends of gnome-system-tools
  Installing nfs-common as Depends of nfs-kernel-server
  new important dependency: sbackup-gtk
  Installing sbackup-gtk as Recommends of sbackup
  new important dependency: brasero-cdrkit
  Installing brasero-cdrkit as Recommends of brasero
  Installing libsrtp0-dev as Depends of libortp-dev
  Installing jackd2 as Depends of jackd
    Installing libjack-jackd2-0 as Depends of jackd2
    Installing jackd2-firewire as Recommends of jackd2
  Installing libcanberra-dev as Depends of libgnome2-dev
  Installing libavahi-common3 as Depends of libavahi-common-dev
  Installing libxinerama1 as Depends of libxinerama-dev
  new important dependency: libgnumail-java-doc
  Installing libgnumail-java-doc as Recommends of libjetty-java-doc
    Installing libgnujaf-java as Recommends of libgnumail-java-doc
    Installing libgnuinet-java as Recommends of libgnumail-java-doc
  new important dependency: libservlet2.5-java-doc
  Installing libservlet2.5-java-doc as Recommends of libjetty-java-doc
  Installing gnome-session-common as Depends of gnome-session
  Installing libcgraph5 as Depends of graphviz
  Installing libgvpr1 as Depends of graphviz
  Installing libboost-signals1.42.0 as Depends of freecad
  Installing libntfs-3g79 as Depends of ntfs-3g
  Installing libkeybinder0 as Depends of python-keybinder
  new important dependency: usb-modeswitch
  Installing usb-modeswitch as Recommends of modemmanager
    Installing usb-modeswitch-data as Depends of usb-modeswitch
  Installing libgirepository1.0-1 as Depends of python-gobject-dbg
  Installing python-gobject as Depends of python-gobject-dbg
    Installing gir1.0-glib-2.0 as Depends of python-gobject
    new important dependency: python-gobject-cairo
    Installing python-gobject-cairo as Recommends of python-gobject
Starting
Starting 2
Investigating libc6
Package libc6 has broken Conflicts on libc6-i686
  Considering libc6-i686 -2 as a solution to libc6 17210
  Added libc6-i686 to the remove list
  Fixing libc6 via remove of libc6-i686
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating libeina-svn-05
Package libeina-svn-05 has broken Conflicts on libeina0
  Considering libeina-svn-06 6 as a solution to libeina-svn-05 51
  Added libeina-svn-06 to the remove list
  Fixing libeina-svn-05 via keep of libeina-svn-06
Investigating libnepomukquery4a
Package libnepomukquery4a has broken Conflicts on kdebase-workspace-libs4+5
  Considering kdebase-workspace-libs4+5 -1 as a solution to libnepomukquery4a 27
  Added kdebase-workspace-libs4+5 to the remove list
  Fixing libnepomukquery4a via remove of kdebase-workspace-libs4+5
Investigating libjack-jackd2-0
Package libjack-jackd2-0 has broken Conflicts on libjack-0.116
  Considering libjack0 0 as a solution to libjack-jackd2-0 26
  Added libjack0 to the remove list
Package libjack-jackd2-0 has broken Conflicts on libjack0
  Considering libjack0 0 as a solution to libjack-jackd2-0 26
  Added libjack0 to the remove list
  Considering libjack0 0 as a solution to libjack-jackd2-0 26
  Fixing libjack-jackd2-0 via keep of libjack0
  Fixing libjack-jackd2-0 via remove of libjack0
Investigating libkresources4
Package libkresources4 has broken Conflicts on kdepimlibs-data
  Considering kdepimlibs-data -1 as a solution to libkresources4 17
  Added kdepimlibs-data to the remove list
  Fixing libkresources4 via remove of kdepimlibs-data
Investigating libeet1
Package libeet1 has broken Depends on libeina-svn-06
  Considering libeina-svn-06 6 as a solution to libeet1 16
  Holding Back libeet1 rather than change libeina-svn-06
Investigating odbcinst1debian2
Package odbcinst1debian2 has broken Conflicts on odbcinst1debian1
  Considering odbcinst1debian1 -1 as a solution to odbcinst1debian2 11
  Added odbcinst1debian1 to the remove list
  Fixing odbcinst1debian2 via remove of odbcinst1debian1
Investigating pm-utils
Package pm-utils has broken Conflicts on pm-utils-powersave-policy
  Considering pm-utils-powersave-policy -1 as a solution to pm-utils 11
  Added pm-utils-powersave-policy to the remove list
  Fixing pm-utils via remove of pm-utils-powersave-policy
Investigating libcdt4
Package libcdt4 has broken Conflicts on libgraphviz4
  Considering libgraphviz4 1 as a solution to libcdt4 10
  Added libgraphviz4 to the remove list
  Fixing libcdt4 via remove of libgraphviz4
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating foomatic-db-compressed-ppds
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db-hpijs
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
Investigating libept0
Package libept0 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 32 as a solution to libept0 3
  Removing libept0 rather than change libapt-pkg-libc6.10-6-4.8
 Try to Re-Instate xserver-xorg-video-tseng
Re-Instated xserver-xorg-video-tseng (27 vs 27)
Investigating jackd2-firewire
Package jackd2-firewire has broken Conflicts on jackd-firewire
  Considering jackd-firewire -1 as a solution to jackd2-firewire 1
  Added jackd-firewire to the remove list
  Considering jackd1-firewire 0 as a solution to jackd2-firewire 1
  Fixing jackd2-firewire via remove of jackd-firewire
Investigating libvlccore2
Package libvlccore2 has broken Depends on vlc-data
  Considering vlc-data 6 as a solution to libvlccore2 1
  Removing libvlccore2 rather than change vlc-data
Investigating libboost-dev
Package libboost-dev has broken Depends on libboost1.42-dev
  Considering libboost1.42-dev 2 as a solution to libboost-dev 0
  Holding Back libboost-dev rather than change libboost1.42-dev
Investigating libboost-serialization1.42-dev
Package libboost-serialization1.42-dev has broken Depends on libboost1.42-dev
  Considering libboost1.42-dev 2 as a solution to libboost-serialization1.42-dev 0
  Holding Back libboost-serialization1.42-dev rather than change libboost1.42-dev
Investigating libboost-serialization-dev
Package libboost-serialization-dev has broken Depends on libboost-serialization1.42-dev
  Considering libboost-serialization1.42-dev 0 as a solution to libboost-serialization-dev 0
  Holding Back libboost-serialization-dev rather than change libboost-serialization1.42-dev
Investigating libelementary-svn-05
Package libelementary-svn-05 has broken Depends on libelementary-data
  Considering libelementary-data 1 as a solution to libelementary-svn-05 0
  Removing libelementary-svn-05 rather than change libelementary-data
Investigating enna
Package enna has broken Depends on libelementary-svn-05
  Considering libelementary-svn-05 0 as a solution to enna 0
  Removing enna rather than change libelementary-svn-05
Investigating wesnoth-httt
Package wesnoth-httt has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-httt -1
  Removing wesnoth-httt rather than change wesnoth-core
Investigating libbrasero-media0
Package libbrasero-media0 has broken Depends on brasero-common
  Considering brasero-common 14 as a solution to libbrasero-media0 -1
  Removing libbrasero-media0 rather than change brasero-common
Investigating libgnokii5
Package libgnokii5 has broken Depends on gnokii-common
  Considering gnokii-common 3 as a solution to libgnokii5 -1
  Removing libgnokii5 rather than change gnokii-common
Investigating libmagickcore2-extra
Package libmagickcore2-extra has broken Depends on libgraphviz4
  Considering libgraphviz4 1 as a solution to libmagickcore2-extra -1
  Removing libmagickcore2-extra rather than change libgraphviz4
Investigating wesnoth-sotbe
Package wesnoth-sotbe has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-sotbe -1
  Removing wesnoth-sotbe rather than change wesnoth-core
Investigating libvlc2
Package libvlc2 has broken Depends on libvlccore2
  Considering libvlccore2 1 as a solution to libvlc2 -1
  Removing libvlc2 rather than change libvlccore2
Investigating wesnoth-thot
Package wesnoth-thot has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-thot -1
  Removing wesnoth-thot rather than change wesnoth-core
Investigating wesnoth-aoi
Package wesnoth-aoi has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-aoi -1
  Removing wesnoth-aoi rather than change wesnoth-core
Investigating wesnoth-did
Package wesnoth-did has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-did -1
  Removing wesnoth-did rather than change wesnoth-core
Investigating libqt4-multimedia
Package libqt4-multimedia has broken Depends on libqtcore4
  Considering libqtcore4 978 as a solution to libqt4-multimedia -1
  Removing libqt4-multimedia rather than change libqtcore4
Investigating wesnoth-trow
Package wesnoth-trow has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-trow -1
  Removing wesnoth-trow rather than change wesnoth-core
Investigating wesnoth-low
Package wesnoth-low has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-low -1
  Removing wesnoth-low rather than change wesnoth-core
Investigating wesnoth-utbs
Package wesnoth-utbs has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-utbs -1
  Removing wesnoth-utbs rather than change wesnoth-core
Investigating wesnoth-sof
Package wesnoth-sof has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-sof -1
  Removing wesnoth-sof rather than change wesnoth-core
Investigating wesnoth-ttb
Package wesnoth-ttb has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-ttb -1
  Removing wesnoth-ttb rather than change wesnoth-core
Investigating wesnoth-tsg
Package wesnoth-tsg has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-tsg -1
  Removing wesnoth-tsg rather than change wesnoth-core
Investigating wesnoth-ei
Package wesnoth-ei has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-ei -1
  Removing wesnoth-ei rather than change wesnoth-core
Investigating wesnoth-nr
Package wesnoth-nr has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-nr -1
  Removing wesnoth-nr rather than change wesnoth-core
Investigating wesnoth-l
Package wesnoth-l has broken Depends on wesnoth-core
  Considering wesnoth-core 56 as a solution to wesnoth-l -1
  Removing wesnoth-l rather than change wesnoth-core
Investigating libpackagekit-glib2-12
Package libpackagekit-glib2-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 32 as a solution to libpackagekit-glib2-12 -2
  Removing libpackagekit-glib2-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating libpackagekit-qt-12
Package libpackagekit-qt-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 32 as a solution to libpackagekit-qt-12 -2
  Removing libpackagekit-qt-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
 Try to Re-Instate libeet1
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
 Try to Re-Instate libboost-dev
 Try to Re-Instate libboost-serialization-dev
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-video-all 5
  Removing xserver-xorg-video-all rather than change xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-core 79
  Holding Back xserver-xorg-core rather than change xserver-xorg-video-6
Investigating xserver-xorg
Package xserver-xorg has broken Depends on xserver-xorg-core
  Considering xserver-xorg-core 79 as a solution to xserver-xorg 46
  Holding Back xserver-xorg rather than change xserver-xorg-core
Investigating xserver-xorg-input-evdev
Package xserver-xorg-input-evdev has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-evdev 7
  Holding Back xserver-xorg-input-evdev rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-rendition 2
  Holding Back xserver-xorg-video-rendition rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3virge 2
  Holding Back xserver-xorg-video-s3virge rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-apm 2
  Holding Back xserver-xorg-video-apm rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ark 2
  Holding Back xserver-xorg-video-ark rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ati 2
  Holding Back xserver-xorg-video-ati rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-tdfx 2
  Holding Back xserver-xorg-video-tdfx rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-trident 2
  Holding Back xserver-xorg-video-trident rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-fbdev 2
  Holding Back xserver-xorg-video-fbdev rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-wacom
Package xserver-xorg-input-wacom has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-wacom 2
  Holding Back xserver-xorg-input-wacom rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mga 2
  Holding Back xserver-xorg-video-mga rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-vmmouse
Package xserver-xorg-input-vmmouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-vmmouse 2
  Holding Back xserver-xorg-input-vmmouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-input-mouse
Package xserver-xorg-input-mouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-mouse 2
  Holding Back xserver-xorg-input-mouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-r128
Package xserver-xorg-video-r128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-r128 2
  Holding Back xserver-xorg-video-r128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-openchrome 2
  Holding Back xserver-xorg-video-openchrome rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vesa 2
  Holding Back xserver-xorg-video-vesa rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-siliconmotion 2
  Holding Back xserver-xorg-video-siliconmotion rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mach64
Package xserver-xorg-video-mach64 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mach64 2
  Holding Back xserver-xorg-video-mach64 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sis 2
  Holding Back xserver-xorg-video-sis rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3 2
  Holding Back xserver-xorg-video-s3 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nv 2
  Holding Back xserver-xorg-video-nv rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-savage 2
  Holding Back xserver-xorg-video-savage rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vmware 2
  Holding Back xserver-xorg-video-vmware rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i128 2
  Holding Back xserver-xorg-video-i128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-neomagic 2
  Holding Back xserver-xorg-video-neomagic rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-chips 2
  Holding Back xserver-xorg-video-chips rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-voodoo 2
  Holding Back xserver-xorg-video-voodoo rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-geode
Package xserver-xorg-video-geode has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-geode 2
  Holding Back xserver-xorg-video-geode rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i740
Package xserver-xorg-video-i740 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i740 2
  Holding Back xserver-xorg-video-i740 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-synaptics
Package xserver-xorg-input-synaptics has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-synaptics 2
  Holding Back xserver-xorg-input-synaptics rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sisusb 2
  Holding Back xserver-xorg-video-sisusb rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-radeon
Package xserver-xorg-video-radeon has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-radeon 2
  Holding Back xserver-xorg-video-radeon rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-cirrus 2
  Holding Back xserver-xorg-video-cirrus rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-intel
Package xserver-xorg-video-intel has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-intel 2
  Holding Back xserver-xorg-video-intel rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-v4l 0
  Holding Back xserver-xorg-video-v4l rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-core
 Try to Re-Instate xserver-xorg
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
 Try to Re-Instate xserver-xorg-input-evdev
 Try to Re-Instate xserver-xorg-video-rendition
 Try to Re-Instate xserver-xorg-video-s3virge
 Try to Re-Instate xserver-xorg-video-apm
 Try to Re-Instate xserver-xorg-video-ark
 Try to Re-Instate xserver-xorg-video-ati
 Try to Re-Instate xserver-xorg-video-tdfx
 Try to Re-Instate xserver-xorg-video-trident
 Try to Re-Instate xserver-xorg-video-fbdev
 Try to Re-Instate xserver-xorg-input-wacom
 Try to Re-Instate xserver-xorg-video-mga
 Try to Re-Instate xserver-xorg-input-vmmouse
 Try to Re-Instate xserver-xorg-input-mouse
 Try to Re-Instate xserver-xorg-video-r128
 Try to Re-Instate xserver-xorg-video-openchrome
 Try to Re-Instate xserver-xorg-video-vesa
 Try to Re-Instate xserver-xorg-video-siliconmotion
 Try to Re-Instate xserver-xorg-video-mach64
 Try to Re-Instate xserver-xorg-video-sis
 Try to Re-Instate xserver-xorg-video-s3
 Try to Re-Instate xserver-xorg-video-nv
 Try to Re-Instate xserver-xorg-video-savage
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-video-vmware
 Try to Re-Instate xserver-xorg-video-i128
 Try to Re-Instate xserver-xorg-video-neomagic
 Try to Re-Instate xserver-xorg-video-chips
 Try to Re-Instate xserver-xorg-video-voodoo
 Try to Re-Instate xserver-xorg-video-geode
 Try to Re-Instate xserver-xorg-video-i740
 Try to Re-Instate xserver-xorg-input-synaptics
 Try to Re-Instate xserver-xorg-video-sisusb
 Try to Re-Instate xserver-xorg-video-radeon
 Try to Re-Instate xserver-xorg-video-cirrus
 Try to Re-Instate xserver-xorg-video-intel
 Try to Re-Instate xserver-xorg-video-v4l
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done
[/HTML]

Main log

[HTML]2010-11-04 22:21:58,511 INFO Using config files '['./DistUpgrade.cfg']'
2010-11-04 22:21:58,511 INFO uname information: 'Linux jonathan-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686'
2010-11-04 22:21:58,512 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-11-04 22:21:58,871 INFO release-upgrader version '0.142.20' started
2010-11-04 22:21:59,065 DEBUG svg pixbuf loader failed (Error displaying image)
2010-11-04 22:21:59,323 DEBUG Using 'DistUpgradeViewGtk' view
2010-11-04 22:21:59,377 DEBUG aufsOptionsAndEnvironmentSetup()
2010-11-04 22:21:59,378 DEBUG using '/tmp/upgrade-rw-6xfEeg' as aufs_rw_dir
2010-11-04 22:21:59,379 DEBUG using '/tmp/upgrade-chroot-swG5S8' as aufs chroot dir
2010-11-04 22:21:59,379 DEBUG enable dpkg --force-overwrite
2010-11-04 22:21:59,446 DEBUG lsb-release: 'lucid'
2010-11-04 22:21:59,464 DEBUG who -m --ips: ''
2010-11-04 22:21:59,466 DEBUG _pythonSymlinkCheck run
2010-11-04 22:21:59,466 DEBUG openCache()
2010-11-04 22:22:00,008 DEBUG /openCache(), new cache size 30430
2010-11-04 22:22:00,009 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-11-04 22:22:00,009 DEBUG checkViewDepends()
2010-11-04 22:22:00,010 DEBUG running doUpdate() (showErrors=False)
2010-11-04 22:22:01,000 ERROR IOError/SystemError in cache.update(): 'W:GPG error: http://download.virtualbox.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139, W:Failed to fetch http://ppa.launchpad.net/http/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.'. Retrying (currentRetry: 0)
2010-11-04 22:22:01,000 ERROR doUpdate() failed completely
2010-11-04 22:22:01,001 DEBUG openCache()
2010-11-04 22:22:01,467 DEBUG /openCache(), new cache size 30430
2010-11-04 22:22:01,467 DEBUG doPostInitialUpdate
2010-11-04 22:22:01,468 DEBUG Plugin modules in ./plugins: deb_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py dpkg_status_plugin.py langpack_manual_plugin.py
2010-11-04 22:22:01,468 DEBUG Loading module ./plugins/deb_plugin.py
2010-11-04 22:22:01,471 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2010-11-04 22:22:01,471 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2010-11-04 22:22:01,473 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2010-11-04 22:22:01,473 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2010-11-04 22:22:01,474 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2010-11-04 22:22:01,474 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2010-11-04 22:22:01,477 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2010-11-04 22:22:01,477 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2010-11-04 22:22:01,478 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2010-11-04 22:22:01,478 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2010-11-04 22:22:01,479 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2010-11-04 22:22:01,479 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2010-11-04 22:22:10,460 DEBUG Foreign: libegroupwise1.2-dev nvidia-173-modaliases libavcodec-extra-52 libedataserverui1.2-8 abrowser-3.6 libdecoration0 nvidia-96-modaliases libtelepathy-farsight0 libdesktopcouch-glib-1.0-2 compiz-core libgtkhtml3.14-dev libmission-control-plugins0 xserver-xorg-video-radeon libebackend1.2-dev evolution-exchange libcamel1.2-dev geoclue libgtkhtml-editor-dev libgupnp-igd-1.0-3 evolution evolution-data-server-common libvpx0 libdvdcss-dev geoclue-localnet xserver-xorg-video-ati telepathy-gabble libedata-cal1.2-dev libavutil-extra-49 evolution-indicator geoclue-manual arkeia compiz libgtksourceview2.0-common telepathy-mission-control-5 libgeoclue0 geoclue-hostip libebook1.2-9 geoclue-yahoo chromium-browser winetricks compiz-gnome wine1.2 libdvdcss2 libedataserver1.2-dev googleearth nvidia-current-modaliases telepathy-haze empathy-common libgdata1.2-1 empathy evolution-data-server w32codecs libcouchdb-glib-1.0-2 libgtksourceview2.0-0 evolution-dev libgtkhtml3.14-19 evolution-data-server-dev libcompizconfig0 mplayer firefox libedataserver1.2-13 evolution-couchdb nautilus-dropbox libebook1.2-dev libebackend1.2-0 nautilus telepathy-salut fglrx-modaliases abrowser adium-theme-ubuntu libedata-book1.2-2 firefox-branding xulrunner-1.9.2 libtelepathy-glib0 libgdata-google1.2-dev libegroupwise1.2-13 nautilus-sendto-empathy nvidia-current evolution-plugins evolution-common intel-gpu-tools prism-google-calendar libgtkhtml-editor0 medibuntu-keyring ttf-symbol-replacement libedataserverui1.2-dev libcamel1.2-14 nautilus-data libgtkhtml-editor-common libevolution libecal1.2-dev gstreamer0.10-nice libgdata1.2-dev skype apport-hooks-medibuntu chromium-codecs-ffmpeg xserver-xorg-video-intel non-free-codecs evolution-dbg acroread libnice0 telepathy-butterfly prism nvidia-settings python-papyon compiz-plugins wisotool chromium-browser-inspector libecal1.2-7 compiz-fusion-plugins-main libgdata-google1.2-1 libnautilus-extension1 python-farsight libgstfarsight0.10-0 libedata-cal1.2-7 prism-facebook firefox-gnome-support libjson-glib-1.0-0 wine
2010-11-04 22:22:10,460 DEBUG Obsolete: ubuntu-tweak crossover-standard-demo googleearth-data
2010-11-04 22:22:10,461 DEBUG updateSourcesList()
2010-11-04 22:22:10,564 DEBUG rewriteSourcesList()
2010-11-04 22:22:10,573 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted'
2010-11-04 22:22:10,573 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2010-11-04 22:22:10,574 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted'
2010-11-04 22:22:10,574 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2010-11-04 22:22:10,574 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2010-11-04 22:22:10,574 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2010-11-04 22:22:10,574 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2010-11-04 22:22:10,574 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2010-11-04 22:22:10,574 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe'
2010-11-04 22:22:10,575 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2010-11-04 22:22:10,575 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe'
2010-11-04 22:22:10,575 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2010-11-04 22:22:10,575 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2010-11-04 22:22:10,575 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2010-11-04 22:22:10,575 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2010-11-04 22:22:10,575 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2010-11-04 22:22:10,576 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse'
2010-11-04 22:22:10,576 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2010-11-04 22:22:10,576 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse'
2010-11-04 22:22:10,576 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2010-11-04 22:22:10,576 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2010-11-04 22:22:10,576 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2010-11-04 22:22:10,576 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2010-11-04 22:22:10,577 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2010-11-04 22:22:10,577 DEBUG examining: 'deb http://archive.canonical.com/ubuntu lucid partner'
2010-11-04 22:22:10,577 DEBUG entry 'deb http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2010-11-04 22:22:10,577 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu lucid partner'
2010-11-04 22:22:10,577 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2010-11-04 22:22:10,577 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted'
2010-11-04 22:22:10,578 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2010-11-04 22:22:10,578 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted'
2010-11-04 22:22:10,578 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2010-11-04 22:22:10,578 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security universe'
2010-11-04 22:22:10,578 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2010-11-04 22:22:10,578 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security universe'
2010-11-04 22:22:10,578 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2010-11-04 22:22:10,578 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse'
2010-11-04 22:22:10,579 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2010-11-04 22:22:10,579 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse'
2010-11-04 22:22:10,579 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2010-11-04 22:22:10,579 DEBUG examining: 'deb http://download.virtualbox.org/virtualbox/debian lucid non-free'
2010-11-04 22:22:10,584 DEBUG entry '# deb http://download.virtualbox.org/virtualbox/debian maverick non-free # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,584 DEBUG examining: 'deb http://deb.opera.com/opera-beta/ testing non-free #Opera Beta Source'
2010-11-04 22:22:10,588 DEBUG entry '# deb http://deb.opera.com/opera-beta/ testing non-free #Opera Beta Source disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,588 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu lucid main #PPA for Ubuntu Mozilla Daily Build Team'
2010-11-04 22:22:10,593 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu maverick main #PPA for Ubuntu Mozilla Daily Build Team disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,593 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main #PPA for Ubuntu Wine Team'
2010-11-04 22:22:10,598 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu maverick main #PPA for Ubuntu Wine Team disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,598 DEBUG examining: 'deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main #Firefox Stable Channel Packages'
2010-11-04 22:22:10,603 DEBUG entry '# deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu maverick main #Firefox Stable Channel Packages disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,603 DEBUG examining: 'deb http://ppa.launchpad.net/python-snippets-drivers/python-snippets-daily/ubuntu lucid main #python-snippets-daily'
2010-11-04 22:22:10,608 DEBUG entry '# deb http://ppa.launchpad.net/python-snippets-drivers/python-snippets-daily/ubuntu maverick main #python-snippets-daily disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,608 DEBUG examining: 'deb http://ppa.launchpad.net/http/ppa/ubuntu lucid main'
2010-11-04 22:22:10,612 DEBUG entry '# deb http://ppa.launchpad.net/http/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,613 DEBUG examining: 'deb http://linux.dropbox.com/ubuntu lucid main'
2010-11-04 22:22:10,617 DEBUG entry '# deb http://linux.dropbox.com/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,617 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main #X Updates'
2010-11-04 22:22:10,622 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main #X Updates disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,622 DEBUG examining: 'deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu lucid main #Adobe Flash PPA'
2010-11-04 22:22:10,627 DEBUG entry '# deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu maverick main #Adobe Flash PPA disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,627 DEBUG examining: 'deb http://ppa.launchpad.net/acire-team/acire-releases/ubuntu lucid main #Acire Releases'
2010-11-04 22:22:10,632 DEBUG entry '# deb http://ppa.launchpad.net/acire-team/acire-releases/ubuntu maverick main #Acire Releases disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,632 DEBUG examining: 'deb http://ppa.launchpad.net/geany-dev/ppa/ubuntu lucid main #PPA for Geany Developers'
2010-11-04 22:22:10,636 DEBUG entry '# deb http://ppa.launchpad.net/geany-dev/ppa/ubuntu maverick main #PPA for Geany Developers disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,637 DEBUG examining: 'deb http://ppa.launchpad.net/vala-team/ppa/ubuntu lucid main #Vala PPA'
2010-11-04 22:22:10,641 DEBUG entry '# deb http://ppa.launchpad.net/vala-team/ppa/ubuntu maverick main #Vala PPA disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,641 DEBUG examining: 'deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main #Nvidia Vdpau Team PPA'
2010-11-04 22:22:10,646 DEBUG entry '# deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu maverick main #Nvidia Vdpau Team PPA disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,646 DEBUG examining: 'deb http://ppa.launchpad.net/telepathy/ppa/ubuntu lucid main #PPA for Telepathy'
2010-11-04 22:22:10,651 DEBUG entry '# deb http://ppa.launchpad.net/telepathy/ppa/ubuntu maverick main #PPA for Telepathy disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,651 DEBUG examining: 'deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.4 "Lucid"'
2010-11-04 22:22:10,655 DEBUG entry '# deb http://packages.medibuntu.org/ maverick free non-free #Medibuntu - Ubuntu 10.4 "Lucid" disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,656 DEBUG examining: 'deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.4 "Lucid"'
2010-11-04 22:22:10,660 DEBUG entry '# deb-src http://packages.medibuntu.org/ maverick free non-free #Medibuntu (source) - Ubuntu 10.4 "Lucid" disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,660 DEBUG examining: 'deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main #PPA for Ubuntu Chromium - Daily Builds'
2010-11-04 22:22:10,665 DEBUG entry '# deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu maverick main #PPA for Ubuntu Chromium - Daily Builds disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,665 DEBUG examining: 'deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu lucid main #nautilus-elementary'
2010-11-04 22:22:10,670 DEBUG entry '# deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu maverick main #nautilus-elementary disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,670 DEBUG examining: 'deb http://ppa.launchpad.net/jacob/evo230/ubuntu lucid main'
2010-11-04 22:22:10,675 DEBUG entry '# deb http://ppa.launchpad.net/jacob/evo230/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,675 DEBUG examining: 'deb http://ppa.launchpad.net/compiz/ppa/ubuntu lucid main #PPA for compiz packagers'
2010-11-04 22:22:10,679 DEBUG entry '# deb http://ppa.launchpad.net/compiz/ppa/ubuntu maverick main #PPA for compiz packagers disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,679 DEBUG examining: 'deb http://dl.google.com/linux/deb/ stable non-free main #Google Stable Source'
2010-11-04 22:22:10,684 DEBUG entry '# deb http://dl.google.com/linux/deb/ stable non-free main #Google Stable Source disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:10,684 DEBUG examining: 'deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype'
2010-11-04 22:22:10,689 DEBUG entry '# deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype disabled on upgrade to maverick' was disabled (unknown mirror)
2010-11-04 22:22:14,717 DEBUG running doUpdate() (showErrors=True)
2010-11-04 22:22:15,731 DEBUG openCache()
2010-11-04 22:22:15,731 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-11-04 22:22:19,793 DEBUG /openCache(), new cache size 32338
2010-11-04 22:22:19,794 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
[/HTML]

---

### Post by dcstar on 2010-11-04
> **Jonners59 said:**
> On my Toshiba, 32-bit Laptop I opened Update Manager and tried to install the new 10.10 update but got the following error message.

Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
** * Unofficial software packages not provided by Ubuntu**


The bottom-line is that you have heaps of PPA repositories, and there is no guarantee whatsoever that they will all support the upgrade process.

Upgrading a system full of PPA packages will be problematic at best, it will be better to strip out the PPAs and then do the upgrade.

---

### Post by Jonners59 on 2010-11-05
> **dcstar said:**
> The bottom-line is that you have heaps of PPA repositories, and there is no guarantee whatsoever that they will all support the upgrade process.

Upgrading a system full of PPA packages will be problematic at best, it will be better to strip out the PPAs and then do the upgrade.

I turned them all off via Update Manager, Sources....  Still did not work.

---

### Post by Jonners59 on 2010-11-19
Any help please?????????????????

---

### Post by Decatf on 2010-11-19
Disabling them from your sources list doesn't change the fact that you still have unofficial packages installed on the system. You will have to run ppa-purge to completely remove a specific PPA.

I am guessing you have installed packages from the xorg-edgers or x updates ppa. If this is the case you should run ppa-purge on that repo to revert to the official packages.

You probably have to do the same for some of the other ppa's you've used.

---

### Post by Jonners59 on 2010-11-19
> **Decatf said:**
> I am guessing you have installed packages from the xorg-edgers or x updates ppa. If this is the case you should run ppa-purge on that repo to revert to the official packages.

Sorry, could you please give more detailed instructions....  I clearly have done something silly, because I do not know what I am doing.

---

### Post by Decatf on 2010-11-19
[B]sudo apt-get install ppa-purge
sudo ppa-purge [B]ppa:ubuntu-x-swat/x-updates

[/B][/B] Start the 10.10 upgrade again. Post back if you are still getting the same error.

---

### Post by Jonners59 on 2010-11-19
> **Decatf said:**
> [B]sudo apt-get install ppa-purge
sudo ppa-purge [B]ppa:ubuntu-x-swat/x-updates

[/B][/B] Start the 10.10 upgrade again. Post back if you are still getting the same error.

cheers, thanks appreciate lots

---

### Post by Jonners59 on 2010-11-19
> **Decatf said:**
> [B]sudo apt-get install ppa-purge
sudo ppa-purge [B]ppa:ubuntu-x-swat/x-updates

[/B][/B] Start the 10.10 upgrade again. Post back if you are still getting the same error.

No joy....

Results of terminal =

[HTML]jonathan@jonathan-laptop:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ppa-purge
jonathan@jonathan-laptop:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo: ppa-purge: command not found
jonathan@jonathan-laptop:~$[/HTML] 


I also tried the up grade, which naturally failed.

---

### Post by Decatf on 2010-11-19
Get the Karmic version of ppa purge from here. [https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb](https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb)

---

### Post by Jonners59 on 2010-11-21
> **Decatf said:**
> Get the Karmic version of ppa purge from here. [https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb](https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/ppa-purge_0.2.6%7Ekarmic_all.deb)

Thanks for this.  Still failed.

This is what the terminal said when running the app/purge:
[HTML]jonathan@jonathan-laptop:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
PPA to be removed: ubuntu-x-swat x-updates
Warning:  Could not find package list for PPA: ubuntu-x-swat x-updates
jonathan@jonathan-laptop:~$ [/HTML]

Screen shot enclosed

---

### Post by Tony221268 on 2010-11-21
Same thing happening for me and same end point;

tony@tony-desktop:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
PPA to be removed: ubuntu-x-swat x-updates
Warning:  Could not find package list for PPA: ubuntu-x-swat x-updates

---

### Post by Jonners59 on 2010-11-21
Always nice to learn ya not alone.

---

### Post by Tony221268 on 2010-11-21
Solved mine by disabling the Nvidia driver if it is any help...

---

### Post by Jonners59 on 2010-11-25
OK.  How do I do this...?

---

### Post by Jonners59 on 2010-12-01
ANYONE gpoing to help me here, please???????? :confused:

---

### Post by CharlesA on 2010-12-02
The only help I can offer you is this:

Backup the machine and then do a clean install of 10.10, if that's what you want on it. Upgrades can be a pain in the butt, and sometimes it's easier to start with a clean slate.

---

### Post by Jonners59 on 2010-12-02
WHat would and how would I back so that I could install 10.10 and not have to build from scratch....  I.e keep configs, apps, etc..?

---

### Post by CharlesA on 2010-12-02
You can mark whatever packages you have installed in synaptic and then inport it in a new install, but as for keeping the settings and whatnot, I don't know if there is a way out of doing a normal upgrade.

---

### Post by HiImTye on 2010-12-02
enable the PPAs and update your lists then use ppa-purge

---

### Post by Tony221268 on 2010-12-03
Sorry Jonners didn't check back. All I did was go to the Additional Drivers (I think it was called something else then in the System menu) and remove the NVidia proprietary driver. Of course, this may not be your problem...note also that once I then upgraded it was a pain to reinstall because I forgot to include "the universe" in synaptic package manager and there was no helpful error to tell me that.

---

### Post by Jonners59 on 2010-12-03
That's the drivers thingie...  There are non in there....  Still stuck

---

### Post by Tony221268 on 2010-12-03
Sorry to fail  - I guess I can't help any more but my advice FWIW

If you are determined to upgrade (which frankly has not made any difference to me!) all I can recommend is the obvious that you are probably already thinking of doing. 

E.g. copy any important app data files, uninstall just about everything (starting with the oddest stuff) while attempting the upgrade everytime you get rid of something you added. I did exactly that until I came across the nVidia driver. None of the standard Ubuntu Software Centre packages were the problem.

My mentality was "Think back - was there nothing that was a real pain to install and came from "Dodgyubuntuapp.com" but might affect something crucial (like interfaces, security or drivers); I have to admit that on those criteria I wouldn't have suspected nVidia as the problem but hey.

Or create a partition and install fresh or just install fresh...

---

### Post by Jonners59 on 2010-12-03
> **Tony221268 said:**
> Sorry to fail  - I guess I can't help any more but my advice FWIW

If you are determined to upgrade (which frankly has not made any difference to me!) all I can recommend is the obvious that you are probably already thinking of doing. 

E.g. copy any important app data files, uninstall just about everything (starting with the oddest stuff) while attempting the upgrade everytime you get rid of something you added. I did exactly that until I came across the nVidia driver. None of the standard Ubuntu Software Centre packages were the problem.

My mentality was "Think back - was there nothing that was a real pain to install and came from "Dodgyubuntuapp.com" but might affect something crucial (like interfaces, security or drivers); I have to admit that on those criteria I wouldn't have suspected nVidia as the problem but hey.

Or create a partition and install fresh or just install fresh...

Tony
You have not failed, the system has failed.
I have a spare partition with Wubi on it, will probably use that.  Am interested which parts of the current install I can copy over to make it similar config.....

---

### Post by Tony221268 on 2010-12-03
OK good luck with that. You know there are a bunch of hidden data folders in your home folder right? They start with . and are hidden by default.

---

### Post by Jonners59 on 2010-12-03
> **Tony221268 said:**
> OK good luck with that. You know there are a bunch of hidden data folders in your home folder right? They start with . and are hidden by default.
yup... I always show hidden files.  saves making a great bo bo when deleting anything!

---

### Post by Jonners59 on 2010-12-28
First
```
sudo gedit /etc/default/grub
```

then
I deleted "quiet" and "splash" from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and made it "nomodeset"

I then changed GRUB_CMDLINE_LINUX="      splash"  			 		to "acpi=off"

Hope this works for others

---


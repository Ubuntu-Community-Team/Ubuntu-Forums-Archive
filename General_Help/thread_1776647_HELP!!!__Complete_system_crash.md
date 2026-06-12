---
title: "HELP!!!  Complete system crash"
date: 2011-06-06
forum: General Help
---

### Post by CTolley on 2011-06-06
The issue was caused by me, but I have no idea how to recover.  

I built a desktop out of an ammo can but was having trouble loading from the USB boot stick.  So, I did what any retard would do and hooked the hdd up to my laptop with a USB to SATA cable.  I proceeded to load 10.10 onto the hdd with no problem (used entire disk, not side-by-side).  Worked wonderfully actually.  

But, then I did the next logical thing and removed the hdd from the laptop and fired the desktop up.  I get a nice black screen with a flashing cursor. Dang it, that sucks.

I boot the laptop (10.04) back up so I can check email and go to bed.  And wouldn't you know it, I fubar'ed the system all sorts of wrong.  It doesn't load grub, and instead I get a pretty black screen with "grub recover>".  Nothing I input registers with the command prompt.  Granted, I don't know as much as most of you up here, but simple things like "restart" don't work.  It doesn't even recognise "sudo".

I can recover all of my data and reload the system if I need to, but I would prefer to fix it.  Please help.

-CTolley

---

### Post by aphatak on 2011-06-06
If you installed Ubuntu on the USB hard disk, I assume the files Grub needs have been stored on the USB hard disk, not on the local drive.
To recover your lost data, you could boot up from the live disk again, and select 'try Ubuntu' instead of 'Install'.  Once Ubuntu is up and running, plug your USB hard disk in; it should mount automatically, and allow you to access it.  You can then copy your data away from the USB hard disk.
Installing the OS on a removable USB hard disk is possible but tricky.  It was a long time ago that I tried it, and I don't remember how it goes.  From whatever I do remember, you will have to have at least the boot partition on your local hard disk, so Grub can at least access its settings.  If you google it, I am sure you will find the howto.

---

### Post by CTolley on 2011-06-06
The hdd that I hooked up through usb is empty.  That was a fresh install.  Apparently it has no grub loader.  But, that is an issue I can try to resolve later.  My bigger issue is to try and fix the laptop.  

I am running the USB boot drive (made with the USB startup disk creator) right now in order to post this question.  That's also when I checked my file system to ensure I can recover my data if a fix is not an option and I have to reload.

---

### Post by CTolley on 2011-06-07
Well, I have the laptop working again.  Installed a side-by-side load, which fixed my grub.  I then backed up all of my files and loaded a fresh load.  So, that makes me happy.  

Now, for the desktop, I still have the black screen with flashing cursor.  It doesn't accept input at all.  I tried loading with the USB stick again, but it failed again, and again, and again.  I can't figure out how to fix the grub on that machine through the USB boot stick.  Any help is appreciated.  Thank you in advance.

-CTolley

---

### Post by wildmanne39 on 2011-06-07
> **CTolley said:**
> Well, I have the laptop working again.  Installed a side-by-side load, which fixed my grub.  I then backed up all of my files and loaded a fresh load.  So, that makes me happy.  

Now, for the desktop, I still have the black screen with flashing cursor.  It doesn't accept input at all.  I tried loading with the USB stick again, but it failed again, and again, and again.  I can't figure out how to fix the grub on that machine through the USB boot stick.  Any help is appreciated.  Thank you in advance.

-CTolley
Hi, this guide should get you going if all you need is to restore grub.
[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

---

### Post by mastablasta on 2011-06-07
you could have just repaired grub and it would work. otherwise your idea would have worked but you would have to remove the orginial hard drive from the notebook first.
 
as for your desktop it seems it has an older board that can't boot from USB, correct? if so then you can use a boot manager such as for example Plop: [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html). boot from liveUSB and then try to install it again or fix grub if install was done well already.

---

### Post by CTolley on 2011-06-07
None of the commands are working.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type

ubuntu@ubuntu:~$ sudo grub-install /dev/sad1
/usr/bin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found

```

It's killing me.  grub-update doesn't work, and well, nothing has been working.  Can't use a Live CD because the desktop doesn't have a CD drive.  Stuck with the USB loader, and it seems to disagree with my attempts.

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **CTolley said:**
> The issue was caused by me, but I have no idea how to recover.  

I built a desktop out of an ammo can but was having trouble loading from the USB boot stick.  So, I did what any retard would do and hooked the hdd up to my laptop with a USB to SATA cable.  I proceeded to load 10.10 onto the hdd with no problem (used entire disk, not side-by-side).  Worked wonderfully actually.  

But, then I did the next logical thing and removed the hdd from the laptop and fired the desktop up.  I get a nice black screen with a flashing cursor. Dang it, that sucks.

I boot the laptop (10.04) back up so I can check email and go to bed.  And wouldn't you know it, I fubar'ed the system all sorts of wrong.  It doesn't load grub, and instead I get a pretty black screen with "grub recover>".  Nothing I input registers with the command prompt.  Granted, I don't know as much as most of you up here, but simple things like "restart" don't work.  It doesn't even recognise "sudo".

I can recover all of my data and reload the system if I need to, but I would prefer to fix it.  Please help.

-CTolley

That's a really different way to install Ubuntu. :)  

If you can't get it to go, try using a Flash Drive and install a ISO of Ubuntu onto the Flash Drive, and boot from that device.  You can resize your partition, and you can migrate your data later on.  Go ahead and install it for now.

Here is guide to help speed up some of the process of getting your system just right too:

10.10 (recommended) 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

or

11.04

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by CTolley on 2011-06-08
The laptop is on 10.10 now.  It's gtg.  It's the desktop that is causing all of my pains.  I'm thinking that my end solution will be to install the hdd into another desktop and do a nice fresh load.  It really seems like the only viable solution at this point.

---

### Post by CTolley on 2011-06-08
Okay, going through the cinderbox fix your grub link again, I was able to reinstall grub.  W00t!  But, now I get something else when I boot.  At least it's not a blank blank screen.  

```
GNU GRUB  version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported.  For the first word, TAB 
lists possible command completions.  Anywhere else TAB lists possible
device or file completions.  

grub>

```

then:

```
grub> boot
error: no loaded kernel
```

Is this saying that Ubuntu isn't there?  When I try to install, it recognizes an OS.  But I am now lost.

---

### Post by CTolley on 2011-06-08
Fixed.  Hooked hdd up to mb on another desktop.  Ran install with thumb drive.  The world is right once again.


Thank you all for your assistance.

---

### Post by wildmanne39 on 2011-06-09
> **CTolley said:**
> Fixed.  Hooked hdd up to mb on another desktop.  Ran install with thumb drive.  The world is right once again.


Thank you all for your assistance.
Hi, your welcome, have fun.

---

### Post by CTolley on 2011-06-09
Well, I lied.  The world is not as right as I had originally thought.  Same computer, new problem.  Updates will not work.  Tried upgrading to 11.04, but that failed as well.

Below is what I've tried and the errors that came with.

From Update Manager:

```
Run a Partial upgrade because you failed at life.

Partial upgrade doing it's thing...

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

acpi-support
acpid
adium-theme-ubuntu
aisleriot
akonadi-server
alacarte
alsa-base
alsa-utils
app-install-data-partner
apparmor
apparmor-utils
appmenu-gtk
appmenu-qt
apport
apport-gtk
apport-symptoms
apt-xapian-index
aptdaemon
aptdaemon-data
aspell
aspell-en
at-spi
avahi-autoipd
avahi-daemon
avahi-utils
banshee
banshee-extension-soundmenu
banshee-extension-ubuntuonemusicstore
baobab
base-files
bash
bash-completion
binfmt-support
bluez
bluez-alsa
bluez-cups
bluez-gstreamer
bogofilter
bogofilter-bdb
bogofilter-common
branding-ubuntu
brasero
brasero-cdrkit
brasero-common
brltty
brltty-x11
bsdmainutils
bsdutils
build-essential
busybox-static
byobu
ca-certificates
capplets-data
checkbox
checkbox-gtk
cmap-adobe-japan1
command-not-found
command-not-found-data
compiz
compiz-core
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
compiz-plugins-main
compizconfig-backend-gconf
computer-janitor
computer-janitor-gtk
console-setup
consolekit
coreutils
couchdb-bin
cpp
cpp-4.4
cpp-4.5
cpu-checker
cups-driver-gutenprint
dash
dbus
dbus-x11
defoma
desktop-file-utils
desktopcouch
dhcp3-client
dhcp3-common
dictionaries-common
diffstat
dmidecode
dmsetup
dmz-cursor-theme
dnsmasq-base
doc-base
docbook-xsl
dpkg
dpkg-dev
dvd+rw-tools
e2fslibs
e2fsprogs
ed
eject
empathy
empathy-common
eog
espeak
espeak-data
evolution
evolution-common
evolution-couchdb
evolution-data-server
evolution-data-server-common
evolution-exchange
evolution-indicator
evolution-plugins
evolution-webcal
exiv2
fakeroot
fancontrol
file
findutils
fontconfig
fontconfig-config
foo2zjs
foomatic-db-compressed-ppds
foomatic-db-engine
foomatic-filters
friendly-recovery
g++
g++-4.5
gamin
gbrainy
gcalctool
gcc
gcc-4.4
gcc-4.4-base
gcc-4.5
gconf-defaults-service
gconf-editor
gconf2
gconf2-common
gdb
gdm-guest-session
gedit
gedit-common
genisoimage
geoclue
geoclue-ubuntu-geoip
geoip-database
gettext
gettext-base
ghostscript
ghostscript-cups
ghostscript-x
ginn
gir1.2-appindicator-0.1
gir1.2-atk-1.0
gir1.2-atspi-2.0
gir1.2-dbusmenu-glib-0.4
gir1.2-dee-0.5
gir1.2-freedesktop
gir1.2-gconf-2.0
gir1.2-gdkpixbuf-2.0
gir1.2-glib-2.0
gir1.2-gtk-2.0
gir1.2-notify-0.7
gir1.2-pango-1.0
gir1.2-soup-2.4
gir1.2-unity-3.0
gir1.2-vte-0.0
gksu
gnome-about
gnome-accessibility-themes
gnome-applets
gnome-applets-data
gnome-bluetooth
gnome-codec-install
gnome-control-center
gnome-desktop-data
gnome-dictionary
gnome-disk-utility
gnome-doc-utils
gnome-games-common
gnome-icon-theme
gnome-keyring
gnome-mag
gnome-mahjongg
gnome-media
gnome-media-common
gnome-menus
gnome-orca
gnome-power-manager
gnome-screensaver
gnome-screenshot
gnome-search-tool
gnome-session-canberra
gnome-settings-daemon
gnome-sudoku
gnome-system-log
gnome-system-monitor
gnome-system-tools
gnome-terminal
gnome-terminal-data
gnome-themes-selected
gnome-user-share
gnome-utils
gnome-utils-common
gnomine
gnupg
gpgv
grep
groff-base
growisofs
grub-common
grub-pc
gs-cjk-resource
gsettings-desktop-schemas
gstreamer0.10-alsa
gstreamer0.10-gnonlin
gstreamer0.10-nice
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x
gtk2-engines
gtk2-engines-murrine
gtk2-engines-pixbuf
gucharmap
guile-1.8-libs
gvfs
gvfs-backends
gvfs-fuse
hdparm
hicolor-icon-theme
hostname
hpijs
hplip
hplip-cups
hplip-data
humanity-icon-theme
hunspell-en-ca
hwdata
ibus
ibus-gtk
ibus-pinyin
ibus-pinyin-db-android
ibus-pinyin-db-open-phrase
ibus-table
icoutils
ifupdown
im-switch
indicator-applet
indicator-applet-appmenu
indicator-applet-complete
indicator-applet-session
indicator-application
indicator-appmenu
indicator-datetime
indicator-me
indicator-messages
indicator-session
indicator-sound
info
inputattach
intltool-debian
iproute
iptables
iputils-arping
iputils-ping
iputils-tracepath
irqbalance
isc-dhcp-client
isc-dhcp-common
iso-codes
jockey-common
jockey-gtk
kbd
kdebase-runtime
kdebase-runtime-data
kdelibs-bin
kdelibs5-data
kdelibs5-plugins
kdepim-runtime
kdepimlibs-kio-plugins
kdesudo
kdoctools
kerneloops-daemon
keyboard-configuration
kubuntu-debug-installer
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
launchpad-integration
lftp
libacl1
libakonadi-kabc4
libakonadi-kcal4
libakonadi-kde4
libakonadi-kmime4
libakonadiprotocolinternals1
libalgorithm-diff-perl
libalgorithm-diff-xs-perl
libalgorithm-merge-perl
libapparmor-perl
libapparmor1
libappindicator0.1-cil
libappindicator1
libapt-pkg-perl
libart2.0-cil
libasound2
libasound2-plugins
libaspell15
libatasmart4
libatk1.0-0
libatk1.0-data
libatkmm-1.6-1
libatm1
libatspi1.0-0
libatspi2.0-0
libattica0
libattr1
libaudio2
libavahi-client3
libavahi-common-data
libavahi-common3
libavahi-core7
libavahi-glib1
libavahi-gobject0
libavahi-ui0
libblkid1
libbluetooth3
libbonobo2-0
libbonobo2-common
libbonoboui2-0
libbonoboui2-common
libboost-program-options1.42.0
libboost-serialization1.42.0
libbrasero-media1
libbrlapi0.5
libc6
libcairo-gobject2
libcairo2
libcairomm-1.0-1
libcamel1.2-19
libcanberra-gtk-module
libcanberra-gtk0
libcanberra-pulse
libcanberra0
libcap-ng0
libcap2
libcdio-cdda0
libcdio-paranoia0
libcdio10
libcdparanoia0
libck-connector0
libclass-accessor-perl
libcloog-ppl0
libclucene0ldbl
libclutter-1.0-0
libclutter-1.0-common
libclutter-gtk-0.10-0
libcolamd2.7.1
libcomerr2
libcompizconfig0
libcouchdb-glib-1.0-2
libcryptui0
libcurl3
libcurl3-gnutls
libdatrie1
libdb4.8
libdbus-1-3
libdbus-glib-1-2
libdbusmenu-glib3
libdbusmenu-gtk3
libdbusmenu-qt2
libdconf0
libdecoration0
libdee-1.0-1
libdesktopcouch-glib-1.0-2
libdevmapper-event1.02.1
libdevmapper1.02.1
libdigest-hmac-perl
libdjvulibre-text
libdjvulibre21
libdmapsharing2
libdpkg-perl
libdrm-intel1
libdrm-nouveau1a
libdrm-radeon1
libdrm2
libdv4
libebackend1.2-0
libebook1.2-10
libecal1.2-8
libedata-book1.2-8
libedata-cal1.2-10
libedataserver1.2-14
libedataserverui1.2-11
libedit2
libegroupwise1.2-13
libelf1
libelfg0
libemail-valid-perl
libenchant1c2a
libept1
libespeak1
libevolution
libexif12
libexiv2-10
libexpat1
libffi5
libfile-basedir-perl
libfile-desktopentry-perl
libfile-mimeinfo-perl
libfolks-telepathy22
libfolks22
libfontconfig1
libfontenc1
libfreetype6
libfs6
libgadu3
libgail-common
libgail-gnome-module
libgail18
libgamin0
libgc1c2
libgcc1
libgconf2-4
libgconf2.0-cil
libgcr0
libgcrypt11
libgd2-xpm
libgdata-common
libgdata1.7-cil
libgdata11
libgdbm3
libgdict-1.0-6
libgdk-pixbuf2.0-0
libgdu-gtk0
libgdu0
libgee2
libgeoclue0
libgeoip1
libgexiv2-0
libgif4
libgirepository-1.0-1
libgkeyfile1.0-cil
libgksu2-0
libgl1-mesa-dri
libgl1-mesa-glx
libglade2.0-cil
libgladeui-1-11
libglew1.5
libglewmx1.5
libglib2.0-0
libglib2.0-bin
libglib2.0-cil
libglib2.0-data
libglibmm-2.4-1c2a
libglu1-mesa
libgmime-2.4-2
libgmime2.4-cil
libgmp3c2
libgmpxx4ldbl
libgnome-bluetooth8
libgnome-desktop-2-17
libgnome-keyring0
libgnome-mag2
libgnome-media0
libgnome-menu2
libgnome-vfs2.0-cil
libgnome-window-settings1
libgnome2-0
libgnome2-common
libgnome2.24-cil
libgnomecanvas2-0
libgnomecanvas2-common
libgnomepanel2.24-cil
libgnomeui-0
libgnomeui-common
libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libgnutls26
libgomp1
libgp11-0
libgpg-error0
libgpgme11
libgphoto2-2
libgphoto2-port0
libgpod-common
libgpod4
libgs9
libgs9-common
libgssdp-1.0-2
libgstfarsight0.10-0
libgstreamer-plugins-base0.10-0
libgstreamer0.10-0
libgtk-sharp-beans-cil
libgtk-vnc-1.0-0
libgtk2-perl
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-cil
libgtk2.0-common
libgtkhtml-editor-common
libgtkhtml-editor0
libgtkhtml3.14-19
libgtkmm-2.4-1c2a
libgtksourceview2.0-0
libgtksourceview2.0-common
libgtop2-7
libgtop2-common
libgucharmap7
libgudev-1.0-0
libgudev1.0-cil
libgupnp-1.0-3
libgupnp-igd-1.0-3
libgutenprint2
libgvfscommon0
libgweather-common
libgweather1
libgwibber1
libhpmud0
libhtml-parser-perl
libhtml-tree-perl
libhunspell-1.2-0
libhyphen0
libibus2
libice6
libicu44
libidl0
libidn11
libido-0.1-0
libieee1284-3
libijs-0.35
libilmbase6
libimobiledevice2
libindicate-gtk2
libindicate5
libindicator3
libio-pty-perl
libio-string-perl
libiodbc2
libipc-run-perl
libisofs6
libiw30
libjack-jackd2-0
libjasper1
libjbig2dec0
libjpeg62
libjs-jquery
libjson-glib-1.0-0
libkabc4
libkatepartinterfaces4
libkcal4
libkcmutils4
libkdecore5
libkdesu5
libkdeui5
libkdewebkit5
libkdnssd4
libkemoticons4
libkeyutils1
libkfile4
libkhtml5
libkidletime4
libkimap4
libkio5
libkjsapi4
libkjsembed4
libkldap4
libkmediaplayer4
libkmime4
libknewstuff2-4
libknewstuff3-4
libknotifyconfig4
libkntlm4
libkparts4
libkpathsea5
libkpimutils4
libkprintutils4
libkpty4
libkresources4
libkrosscore4
libktexteditor4
liblaunchpad-integration-common
liblaunchpad-integration1
liblaunchpad-integration1.0-cil
liblcms1
libldap-2.4-2
liblouis-data
liblouis2
liblqr-1-0
libltdl7
liblvm2app2.2
liblzma2
libmagic1
libmagickcore3
libmagickwand3
libmailtransport4
libmeanwhile1
libmetacity-private0
libmicroblog4
libmission-control-plugins0
libmng1
libmono-addins-gui0.2-cil
libmono-addins0.2-cil
libmono-cairo2.0-cil
libmono-corlib2.0-cil
libmono-i18n-west2.0-cil
libmono-management2.0-cil
libmono-posix2.0-cil
libmono-security2.0-cil
libmono-sharpzip2.84-cil
libmono-system2.0-cil
libmono-zeroconf1.0-cil
libmozjs185-1.0
libmpc2
libmpfr4
libmtdev1
libmtp8
libmusicbrainz4c2a
libmysqlclient16
libmythes-1.2-0
libnautilus-extension1
libncurses5
libncursesw5
libneon27-gnutls
libnepomuk4
libnepomukquery4a
libnepomukutils4
libnet-dns-perl
libnet-domain-tld-perl
libnet-ip-perl
libnewt0.52
libnfnetlink0
libnice10
libnl1
libnm-glib-vpn1
libnm-glib2
libnm-util1
libnotify0.4-cil
libnotify4
libnspr4
libnspr4-0d
libnss-mdns
libnss3
libnss3-1d
liboobs-1-5
libopencc1
libopenexr6
liborbit2
liborc-0.4-0
libpam-ck-connector
libpam-gnome-keyring
libpango1.0-0
libpangomm-1.4-1
libparse-debianchangelog-perl
libparted0debian1
libpci3
libpciaccess0
libpcre3
libpcsclite1
libphonon4
libpipeline1
libpixman-1-0
libplasma3
libplist1
libpng12-0
libpolkit-agent-1-0
libpolkit-backend-1-0
libpolkit-gobject-1-0
libpolkit-gtk-1-0
libpolkit-qt-1-1
libportaudio2
libppl-c2
libppl7
libprotobuf6
libprotoc6
libproxy0
libpst4
libpth20
libpurple-bin
libpurple0
libpython2.6
libpython2.7
libqapt-runtime
libqapt1
libqca2
libqtassistantclient4
libqtwebkit4
libquvi0
librarian0
librasqal2
libraw1394-11
librdf0
libreadline5
libreadline6
librsvg2-2
librsvg2-common
libsane
libsane-hpaio
libsasl2-2
libsasl2-modules
libsdl1.2debian
libsdl1.2debian-pulseaudio
libselinux1
libsensors4
libsgutils2-2
libsigc++-2.0-0c2a
libslang2
libslp1
libsm6
libsndfile1
libsnmp-base
libsnmp15
libsolid4
libsoprano4
libsoup-gnome2.4-1
libsoup2.4-1
libspectre1
libspeechd2
libsqlite3-0
libss2
libssh-4
libssl0.9.8
libstdc++6
libstdc++6-4.5-dev
libstreamanalyzer0
libstreams0
libsub-name-perl
libtaglib2.0-cil
libtalloc2
libtasn1-3
libtdb1
libtelepathy-farsight0
libtelepathy-glib0
libtextcat-data
libtextcat0
libthai-data
libthai0
libthreadweaver4
libtiff4
libtotem-plparser17
libubuntuone-1.0-1
libubuntuone1.0-cil
libudev0
libunique-1.0-0
libunistring0
libunity-misc0
libunity4
libupower-glib1
liburi-perl
libusb-0.1-4
libusbmuxd1
libutouch-evemu1
libutouch-frame1
libutouch-geis1
libutouch-grail1
libuuid1
libv4l-0
libvala-0.10-0
libvirtodbc0
libvorbis0a
libvorbisenc2
libvorbisfile3
libvte-common
libvte9
libwebkitgtk-1.0-0
libwebkitgtk-1.0-common
libwmf0.2-7
libwmf0.2-7-gtk
libwnck-common
libwnck22
libwpd-0.9-9
libwpg-0.2-2
libwps-0.2-2
libwrap0
libwww-perl
libx11-6
libx11-data
libx11-xcb1
libxapian22
libxau6
libxaw7
libxcb-dri2-0
libxcb-render0
libxcb-shape0
libxcb-shm0
libxcb1
libxcomposite1
libxcursor1
libxdamage1
libxdmcp6
libxext6
libxfixes3
libxfont1
libxft2
libxi6
libxinerama1
libxkbfile1
libxklavier16
libxml2
libxml2-utils
libxmu6
libxmuu1
libxpm4
libxrandr2
libxrender1
libxres1
libxslt1.1
libxss1
libxt6
libxtst6
libxv1
libxvmc1
libxxf86dga1
libxxf86vm1
libzeitgeist-1.0-1
light-themes
lintian
linux-firmware
linux-generic
linux-headers-2.6.38-8
linux-headers-2.6.38-8-generic
linux-headers-generic
linux-image-2.6.38-8-generic
linux-image-generic
linux-libc-dev
linux-sound-base
lm-sensors
locales
login
logrotate
lsb-base
lsb-release
lshw
ltrace
make
man-db
manpages
manpages-dev
media-player-info
memtest86+
metacity
metacity-common
mime-support
mlocate
mobile-broadband-provider-info
modemmanager
mono-2.0-gac
mono-csharp-shell
mono-gac
mono-gmcs
mono-runtime
mountall
mousetweaks
msr-tools
mtr-tiny
myspell-en-gb
myspell-en-za
mysql-client-core-5.1
mysql-common
mysql-server-core-5.1
nano
nautilus
nautilus-data
nautilus-sendto-empathy
nautilus-share
ncurses-base
ncurses-bin
netbase
netcat-openbsd
network-manager
network-manager-gnome
network-manager-pptp
network-manager-pptp-gnome
notify-osd
notify-osd-icons
ntpdate
nvidia-common
obex-data-server
obexd-client
odbcinst
odbcinst1debian2
onboard
openprinting-ppds
openssh-client
openssl
os-prober
oxygen-icon-theme
parted
patch
pciutils
pcmciautils
phonon
pinyin-database
pitivi
pkg-config
plasma-scriptengine-declarative
plasma-scriptengine-javascript
pm-utils
policykit-1
policykit-1-gnome
policykit-desktop-privileges
popularity-contest
ppp
pppconfig
pptp-linux
procps
protobuf-compiler
psmisc
python
python-appindicator
python-apport
python-aptdaemon
python-aptdaemon-gtk
python-aptdaemon.gtk3widgets
python-aptdaemon.gtkwidgets
python-avahi
python-brlapi
python-cairo
python-central
python-chardet
python-couchdb
python-crypto
python-cups
python-dbus
python-debian
python-defer
python-desktopcouch-application
python-desktopcouch-records
python-egenix-mxdatetime
python-egenix-mxtools
python-farsight
python-gconf
python-gdbm
python-gmenu
python-gnome2
python-gnomeapplet
python-gnomecanvas
python-gnomekeyring
python-gnupginterface
python-gst0.10
python-gtksourceview2
python-gtkspell
python-httplib2
python-ibus
python-imaging
python-indicate
python-keyring
python-launchpad-integration
python-launchpadlib
python-lazr.restfulclient
python-lazr.uri
python-libproxy
python-libxml2
python-louis
python-mako
python-markupsafe
python-minimal
python-newt
python-notify
python-openssl
python-pam
python-pexpect
python-piston-mini-client
python-pkg-resources
python-problem-report
python-protobuf
python-pyatspi
python-pycurl
python-pygoocanvas
python-pyorbit
python-qt4
python-rdflib
python-serial
python-simplejson
python-sip
python-smbc
python-software-properties
python-speechd
python-support
python-telepathy
python-twisted-bin
python-twisted-core
python-twisted-names
python-twisted-web
python-ubuntuone
python-ubuntuone-control-panel
python-virtkey
python-vte
python-wadllib
python-webkit
python-wnck
python-wsgi-intercept
python-xapian
python-zope.interface
python2.6
python2.6-minimal
python2.7
python2.7-minimal
qapt-batch
quadrapassel
rarian-compat
readline-common
rfkill
rhythmbox
rhythmbox-plugin-cdrecorder
rhythmbox-plugins
rhythmbox-ubuntuone-music-store
rsync
rsyslog
rtkit
sane-utils
screen
screen-resolution-extra
seahorse
sed
sessioninstaller
sgml-base
sgml-data
shared-desktop-ontologies
shared-mime-info
shotwell
simple-scan
software-properties-gtk
software-properties-kde
soprano-daemon
speech-dispatcher
splix
ssh-askpass-gnome
ssl-cert
synaptic
syslinux
syslinux-common
system-tools-backends
tar
tcl8.4
tcpd
tcpdump
telepathy-butterfly
telepathy-gabble
telepathy-haze
telepathy-idle
telepathy-mission-control-5
telepathy-salut
time
tomboy
totem
totem-common
totem-mozilla
totem-plugins
transmission-common
transmission-gtk
tsclient
ttf-indic-fonts-core
ttf-kacst-one
ttf-lao
ttf-punjabi-fonts
ttf-takao-pgothic
ttf-ubuntu-font-family
ubufox
ubuntu-desktop
ubuntu-minimal
ubuntu-mono
ubuntu-sounds
ubuntu-standard
ubuntu-system-service
ubuntu-wallpapers
ubuntuone-control-panel
ubuntuone-control-panel-gtk
ucf
udev
udisks
ufw
unattended-upgrades
unity-asset-pool
unity-place-applications
unity-place-files
unzip
update-inetd
update-notifier
update-notifier-common
upower
ureadahead
usb-modeswitch
usb-modeswitch-data
usbmuxd
usbutils
uuid-runtime
vbetool
vim-common
vim-tiny
vinagre
virtuoso-minimal
virtuoso-opensource-6.1-bin
virtuoso-opensource-6.1-common
w3m
wget
whiptail
whois
wireless-crda
wireless-tools
wodim
wpasupplicant
x11-apps
x11-common
x11-session-utils
x11-utils
x11-xkb-utils
x11-xserver-utils
xauth
xbitmaps
xcursor-themes
xdg-user-dirs
xdg-utils
xfonts-100dpi
xfonts-75dpi
xfonts-base
xfonts-encodings
xfonts-scalable
xfonts-utils
xinit
xinput
xkb-data
xorg
xorg-docs-core
xscreensaver-data
xscreensaver-gl
xserver-xorg
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse
xserver-xorg-input-wacom
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-ati
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-fbdev
xserver-xorg-video-geode
xserver-xorg-video-i128
xserver-xorg-video-i740
xserver-xorg-video-mach64
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nouveau
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-qxl
xserver-xorg-video-r128
xserver-xorg-video-radeon
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-vesa
xserver-xorg-video-vmware
xserver-xorg-video-voodoo
xsltproc
xterm
xul-ext-ubufox
xulrunner-1.9.2
xz-utils
yelp
yelp-xsl
zeitgeist
zeitgeist-core
zeitgeist-datahub
zeitgeist-extension-fts
zenity
zip
zlib1g

```

Damn that's a lot of crap.

From Package Manager with 11 broken packages, after I "fix" them:

```
An error occurred

The following details are provided:

E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

hit close, then:

```
An error occurred

The following details are provided:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: _cache->open() failed, please report.
```

Whatever that means.  Okay, let's go to the terminal.

```
sudo apt-get -f install
...bunch of stuff...
After this operation, 375MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6 libgomp1 libgcc1 libstdc++6 libpcre3 libglib2.0-0 udev grub-pc
  grub-common python-desktopcouch-records python2.7-minimal libsqlite3-0
  python2.7 python-twisted-bin python-zope.interface python-twisted-core
  python-twisted-names libpython2.7 libaudio2 libjpeg62 libmng1
  libqtassistantclient4 libphonon4 libgstreamer0.10-0
  libgstreamer-plugins-base0.10-0 phonon libqtwebkit4 python-support
  python-sip python-qt4 libasound2 libattica0 libexiv2-10 libkdecore5
  libdbusmenu-qt2 libkdeui5 libkcmutils4 libkpty4 libkdesu5 libkdnssd4
  libclucene0ldbl libiodbc2 librdf0 soprano-daemon libsoprano4 libnepomuk4
  libnepomukquery4a libnepomukutils4 libsolid4 libstreams0 libstreamanalyzer0
  libkio5 libkemoticons4 libkfile4 libgif4 libkjsapi4 libkparts4
  libktexteditor4 libkhtml5 libkidletime4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libilmbase6 libopenexr6 libkdewebkit5 libqca2
  libthreadweaver4 libplasma3 libssh-4 kdebase-runtime-data
  libkatepartinterfaces4 libkjsembed4 libkntlm4 libkrosscore4 policykit-1
  libpolkit-backend-1-0 libgdk-pixbuf2.0-0 xserver-xorg-video-tseng
  xserver-xorg-video-siliconmotion xserver-xorg-video-r128
  xserver-xorg-video-mach64 xserver-xorg-video-radeon xserver-xorg-video-ati
  xserver-xorg-video-i740 xserver-xorg-video-geode xserver-xorg-video-nv
  xserver-xorg-video-chips xserver-xorg-video-trident xserver-xorg-video-s3
  xserver-xorg-video-i128 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-cirrus xserver-xorg-video-ark xserver-xorg-video-tdfx
  xserver-xorg-video-sisusb xserver-xorg-video-rendition
  xserver-xorg-video-vesa xserver-xorg-video-fbdev xserver-xorg-video-savage
  xserver-xorg-video-vmware xserver-xorg-video-openchrome
  xserver-xorg-video-s3virge xserver-xorg-video-voodoo xserver-xorg-video-apm
  xserver-xorg-video-sis xserver-xorg-input-mouse libmtdev1 libutouch-evemu1
  libutouch-frame1 libutouch-grail1 xserver-xorg-video-nouveau
  xserver-xorg-input-evdev xserver-xorg-input-wacom xserver-xorg-input-vmmouse
  xserver-xorg-input-synaptics console-setup keyboard-configuration
  libgpg-error0 libgcrypt11 libdrm-nouveau1a libpango1.0-0 libgail-common
  libgail18 gtk2-engines-pixbuf libgtk2.0-0 libpolkit-gtk-1-0
  libpolkit-agent-1-0 libpolkit-gobject-1-0 libpolkit-qt-1-1 kdelibs5-data
  docbook-xsl kdoctools kdelibs-bin kdelibs5-plugins oxygen-icon-theme
  shared-desktop-ontologies plasma-scriptengine-javascript
  plasma-scriptengine-declarative kdebase-runtime libkmime4 libkimap4
  libkldap4 kdepimlibs-kio-plugins libakonadi-kabc4 libkresources4 libkabc4
  libkpimutils4 libkcal4 libakonadi-kcal4 libakonadiprotocolinternals1
  libakonadi-kde4 libakonadi-kmime4 libmailtransport4 libmicroblog4
  libboost-program-options1.42.0 mysql-common libmysqlclient16
  mysql-server-core-5.1 mysql-client-core-5.1 akonadi-server kdepim-runtime
  libknewstuff2-4 libkprintutils4 python-minimal python-wsgi-intercept
  python-lazr.restfulclient libatspi1.0-0 gnome-mag libgirepository-1.0-1
  gir1.2-glib-2.0 libatspi2.0-0 gir1.2-atspi-2.0 python-pyatspi2 hpijs
  libhpmud0 libsane-hpaio hplip-data hplip-cups hplip libhyphen0 libicu44
  libmythes-1.2-0 libneon27-gnutls libnspr4-0d libnspr4 libnss3-1d libnss3
  libtextcat-data libtextcat0 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  python-httplib2 python-openssl nvidia-common python-libxml2 python-imaging
  python-markupsafe python-rdflib python-virtkey screen-resolution-extra
  python-crypto python-pam libxapian22 python-xapian python-simplejson
  command-not-found ufw python-problem-report python-cups python-smbc
  python-pyorbit python-cairo libcurl3-gnutls python-pycurl libnewt0.52
  python-newt python-lazr.uri python-gnomecanvas python-apport
  python-launchpad-integration python-brlapi python-egenix-mxdatetime
  python-software-properties computer-janitor python-egenix-mxtools
  python-twisted-web lsb-release jockey-common python-dbus python kdesudo
  libqapt1 libqapt-runtime qapt-batch software-properties-kde python-couchdb
  libdbusmenu-glib3 libdbusmenu-gtk3 libindicate5 indicator-messages
  indicator-application indicator-sound libappindicator1 indicator-session
  libindicator3 libjson-glib-1.0-0 libnotify4 pinyin-database appmenu-qt
  brasero-cdrkit growisofs dvd+rw-tools brasero libbrasero-media1 libsoup2.4-1
  libedataserver1.2-14 evolution-exchange evolution libcamel1.2-19
  libebackend1.2-0 libebook1.2-10 libgdata11 libecal1.2-8 libedata-book1.2-8
  libedata-cal1.2-10 libegroupwise1.2-13 evolution-data-server
  evolution-data-server-common libedataserverui1.2-11 libevolution
  evolution-common gir1.2-atk-1.0 libcairo-gobject2 gir1.2-freedesktop
  gir1.2-gdkpixbuf-2.0 ibus-pinyin-db-open-phrase icoutils
  kubuntu-debug-installer libreadline5 virtuoso-opensource-6.1-common
  odbcinst1debian2 odbcinst libvirtodbc0 totem-mozilla totem
  virtuoso-opensource-6.1-bin virtuoso-minimal aptdaemon-data libquvi0
  python-defer
Install these packages without verification [y/N]? y
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

Dang nabbit!

Okay, let's try:

```
 sudo apt-get update
...bunch of stuff...
Something wicked happened resolving 'af.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Really??  WTF.

```
sudo apt-get dist-upgrade -f
After this operation, 756MB of additional disk space will be used.
Do you want to continue [Y/n]? y
...bunch of stuff posted earlier...
Install these packages without verification [y/N]? y
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

```
sudo apt-get clean
ammo@ammocan:~$ sudo apt-get -f install
...whole bunch of stuff getting removed and reinstalled (in theory)...
Fetched 227MB in 16min 9s (234kB/s)                                            
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

:(  Me sad.  Thoughts/suggestions?

---

### Post by linuxinstalledfromhdd on 2011-06-09
I had issues with 11.04 myself. I rolled back to 10.10 where everything functions normally again.  If you can roll back, go for it. Otherwise here is a guide to try to get your system running normally again in 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Or you can wait and have someone try to sort that mess out. :)

---

### Post by wildmanne39 on 2011-06-09
> **CTolley said:**
> Well, I lied.  The world is not as right as I had originally thought.  Same computer, new problem.  Updates will not work.  Tried upgrading to 11.04, but that failed as well.

Below is what I've tried and the errors that came with.

From Update Manager:

```
Run a Partial upgrade because you failed at life.

Partial upgrade doing it's thing...

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

acpi-support
acpid
adium-theme-ubuntu
aisleriot
akonadi-server
alacarte
alsa-base
alsa-utils
app-install-data-partner
apparmor
apparmor-utils
appmenu-gtk
appmenu-qt
apport
apport-gtk
apport-symptoms
apt-xapian-index
aptdaemon
aptdaemon-data
aspell
aspell-en
at-spi
avahi-autoipd
avahi-daemon
avahi-utils
banshee
banshee-extension-soundmenu
banshee-extension-ubuntuonemusicstore
baobab
base-files
bash
bash-completion
binfmt-support
bluez
bluez-alsa
bluez-cups
bluez-gstreamer
bogofilter
bogofilter-bdb
bogofilter-common
branding-ubuntu
brasero
brasero-cdrkit
brasero-common
brltty
brltty-x11
bsdmainutils
bsdutils
build-essential
busybox-static
byobu
ca-certificates
capplets-data
checkbox
checkbox-gtk
cmap-adobe-japan1
command-not-found
command-not-found-data
compiz
compiz-core
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
compiz-plugins-main
compizconfig-backend-gconf
computer-janitor
computer-janitor-gtk
console-setup
consolekit
coreutils
couchdb-bin
cpp
cpp-4.4
cpp-4.5
cpu-checker
cups-driver-gutenprint
dash
dbus
dbus-x11
defoma
desktop-file-utils
desktopcouch
dhcp3-client
dhcp3-common
dictionaries-common
diffstat
dmidecode
dmsetup
dmz-cursor-theme
dnsmasq-base
doc-base
docbook-xsl
dpkg
dpkg-dev
dvd+rw-tools
e2fslibs
e2fsprogs
ed
eject
empathy
empathy-common
eog
espeak
espeak-data
evolution
evolution-common
evolution-couchdb
evolution-data-server
evolution-data-server-common
evolution-exchange
evolution-indicator
evolution-plugins
evolution-webcal
exiv2
fakeroot
fancontrol
file
findutils
fontconfig
fontconfig-config
foo2zjs
foomatic-db-compressed-ppds
foomatic-db-engine
foomatic-filters
friendly-recovery
g++
g++-4.5
gamin
gbrainy
gcalctool
gcc
gcc-4.4
gcc-4.4-base
gcc-4.5
gconf-defaults-service
gconf-editor
gconf2
gconf2-common
gdb
gdm-guest-session
gedit
gedit-common
genisoimage
geoclue
geoclue-ubuntu-geoip
geoip-database
gettext
gettext-base
ghostscript
ghostscript-cups
ghostscript-x
ginn
gir1.2-appindicator-0.1
gir1.2-atk-1.0
gir1.2-atspi-2.0
gir1.2-dbusmenu-glib-0.4
gir1.2-dee-0.5
gir1.2-freedesktop
gir1.2-gconf-2.0
gir1.2-gdkpixbuf-2.0
gir1.2-glib-2.0
gir1.2-gtk-2.0
gir1.2-notify-0.7
gir1.2-pango-1.0
gir1.2-soup-2.4
gir1.2-unity-3.0
gir1.2-vte-0.0
gksu
gnome-about
gnome-accessibility-themes
gnome-applets
gnome-applets-data
gnome-bluetooth
gnome-codec-install
gnome-control-center
gnome-desktop-data
gnome-dictionary
gnome-disk-utility
gnome-doc-utils
gnome-games-common
gnome-icon-theme
gnome-keyring
gnome-mag
gnome-mahjongg
gnome-media
gnome-media-common
gnome-menus
gnome-orca
gnome-power-manager
gnome-screensaver
gnome-screenshot
gnome-search-tool
gnome-session-canberra
gnome-settings-daemon
gnome-sudoku
gnome-system-log
gnome-system-monitor
gnome-system-tools
gnome-terminal
gnome-terminal-data
gnome-themes-selected
gnome-user-share
gnome-utils
gnome-utils-common
gnomine
gnupg
gpgv
grep
groff-base
growisofs
grub-common
grub-pc
gs-cjk-resource
gsettings-desktop-schemas
gstreamer0.10-alsa
gstreamer0.10-gnonlin
gstreamer0.10-nice
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x
gtk2-engines
gtk2-engines-murrine
gtk2-engines-pixbuf
gucharmap
guile-1.8-libs
gvfs
gvfs-backends
gvfs-fuse
hdparm
hicolor-icon-theme
hostname
hpijs
hplip
hplip-cups
hplip-data
humanity-icon-theme
hunspell-en-ca
hwdata
ibus
ibus-gtk
ibus-pinyin
ibus-pinyin-db-android
ibus-pinyin-db-open-phrase
ibus-table
icoutils
ifupdown
im-switch
indicator-applet
indicator-applet-appmenu
indicator-applet-complete
indicator-applet-session
indicator-application
indicator-appmenu
indicator-datetime
indicator-me
indicator-messages
indicator-session
indicator-sound
info
inputattach
intltool-debian
iproute
iptables
iputils-arping
iputils-ping
iputils-tracepath
irqbalance
isc-dhcp-client
isc-dhcp-common
iso-codes
jockey-common
jockey-gtk
kbd
kdebase-runtime
kdebase-runtime-data
kdelibs-bin
kdelibs5-data
kdelibs5-plugins
kdepim-runtime
kdepimlibs-kio-plugins
kdesudo
kdoctools
kerneloops-daemon
keyboard-configuration
kubuntu-debug-installer
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
launchpad-integration
lftp
libacl1
libakonadi-kabc4
libakonadi-kcal4
libakonadi-kde4
libakonadi-kmime4
libakonadiprotocolinternals1
libalgorithm-diff-perl
libalgorithm-diff-xs-perl
libalgorithm-merge-perl
libapparmor-perl
libapparmor1
libappindicator0.1-cil
libappindicator1
libapt-pkg-perl
libart2.0-cil
libasound2
libasound2-plugins
libaspell15
libatasmart4
libatk1.0-0
libatk1.0-data
libatkmm-1.6-1
libatm1
libatspi1.0-0
libatspi2.0-0
libattica0
libattr1
libaudio2
libavahi-client3
libavahi-common-data
libavahi-common3
libavahi-core7
libavahi-glib1
libavahi-gobject0
libavahi-ui0
libblkid1
libbluetooth3
libbonobo2-0
libbonobo2-common
libbonoboui2-0
libbonoboui2-common
libboost-program-options1.42.0
libboost-serialization1.42.0
libbrasero-media1
libbrlapi0.5
libc6
libcairo-gobject2
libcairo2
libcairomm-1.0-1
libcamel1.2-19
libcanberra-gtk-module
libcanberra-gtk0
libcanberra-pulse
libcanberra0
libcap-ng0
libcap2
libcdio-cdda0
libcdio-paranoia0
libcdio10
libcdparanoia0
libck-connector0
libclass-accessor-perl
libcloog-ppl0
libclucene0ldbl
libclutter-1.0-0
libclutter-1.0-common
libclutter-gtk-0.10-0
libcolamd2.7.1
libcomerr2
libcompizconfig0
libcouchdb-glib-1.0-2
libcryptui0
libcurl3
libcurl3-gnutls
libdatrie1
libdb4.8
libdbus-1-3
libdbus-glib-1-2
libdbusmenu-glib3
libdbusmenu-gtk3
libdbusmenu-qt2
libdconf0
libdecoration0
libdee-1.0-1
libdesktopcouch-glib-1.0-2
libdevmapper-event1.02.1
libdevmapper1.02.1
libdigest-hmac-perl
libdjvulibre-text
libdjvulibre21
libdmapsharing2
libdpkg-perl
libdrm-intel1
libdrm-nouveau1a
libdrm-radeon1
libdrm2
libdv4
libebackend1.2-0
libebook1.2-10
libecal1.2-8
libedata-book1.2-8
libedata-cal1.2-10
libedataserver1.2-14
libedataserverui1.2-11
libedit2
libegroupwise1.2-13
libelf1
libelfg0
libemail-valid-perl
libenchant1c2a
libept1
libespeak1
libevolution
libexif12
libexiv2-10
libexpat1
libffi5
libfile-basedir-perl
libfile-desktopentry-perl
libfile-mimeinfo-perl
libfolks-telepathy22
libfolks22
libfontconfig1
libfontenc1
libfreetype6
libfs6
libgadu3
libgail-common
libgail-gnome-module
libgail18
libgamin0
libgc1c2
libgcc1
libgconf2-4
libgconf2.0-cil
libgcr0
libgcrypt11
libgd2-xpm
libgdata-common
libgdata1.7-cil
libgdata11
libgdbm3
libgdict-1.0-6
libgdk-pixbuf2.0-0
libgdu-gtk0
libgdu0
libgee2
libgeoclue0
libgeoip1
libgexiv2-0
libgif4
libgirepository-1.0-1
libgkeyfile1.0-cil
libgksu2-0
libgl1-mesa-dri
libgl1-mesa-glx
libglade2.0-cil
libgladeui-1-11
libglew1.5
libglewmx1.5
libglib2.0-0
libglib2.0-bin
libglib2.0-cil
libglib2.0-data
libglibmm-2.4-1c2a
libglu1-mesa
libgmime-2.4-2
libgmime2.4-cil
libgmp3c2
libgmpxx4ldbl
libgnome-bluetooth8
libgnome-desktop-2-17
libgnome-keyring0
libgnome-mag2
libgnome-media0
libgnome-menu2
libgnome-vfs2.0-cil
libgnome-window-settings1
libgnome2-0
libgnome2-common
libgnome2.24-cil
libgnomecanvas2-0
libgnomecanvas2-common
libgnomepanel2.24-cil
libgnomeui-0
libgnomeui-common
libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libgnutls26
libgomp1
libgp11-0
libgpg-error0
libgpgme11
libgphoto2-2
libgphoto2-port0
libgpod-common
libgpod4
libgs9
libgs9-common
libgssdp-1.0-2
libgstfarsight0.10-0
libgstreamer-plugins-base0.10-0
libgstreamer0.10-0
libgtk-sharp-beans-cil
libgtk-vnc-1.0-0
libgtk2-perl
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-cil
libgtk2.0-common
libgtkhtml-editor-common
libgtkhtml-editor0
libgtkhtml3.14-19
libgtkmm-2.4-1c2a
libgtksourceview2.0-0
libgtksourceview2.0-common
libgtop2-7
libgtop2-common
libgucharmap7
libgudev-1.0-0
libgudev1.0-cil
libgupnp-1.0-3
libgupnp-igd-1.0-3
libgutenprint2
libgvfscommon0
libgweather-common
libgweather1
libgwibber1
libhpmud0
libhtml-parser-perl
libhtml-tree-perl
libhunspell-1.2-0
libhyphen0
libibus2
libice6
libicu44
libidl0
libidn11
libido-0.1-0
libieee1284-3
libijs-0.35
libilmbase6
libimobiledevice2
libindicate-gtk2
libindicate5
libindicator3
libio-pty-perl
libio-string-perl
libiodbc2
libipc-run-perl
libisofs6
libiw30
libjack-jackd2-0
libjasper1
libjbig2dec0
libjpeg62
libjs-jquery
libjson-glib-1.0-0
libkabc4
libkatepartinterfaces4
libkcal4
libkcmutils4
libkdecore5
libkdesu5
libkdeui5
libkdewebkit5
libkdnssd4
libkemoticons4
libkeyutils1
libkfile4
libkhtml5
libkidletime4
libkimap4
libkio5
libkjsapi4
libkjsembed4
libkldap4
libkmediaplayer4
libkmime4
libknewstuff2-4
libknewstuff3-4
libknotifyconfig4
libkntlm4
libkparts4
libkpathsea5
libkpimutils4
libkprintutils4
libkpty4
libkresources4
libkrosscore4
libktexteditor4
liblaunchpad-integration-common
liblaunchpad-integration1
liblaunchpad-integration1.0-cil
liblcms1
libldap-2.4-2
liblouis-data
liblouis2
liblqr-1-0
libltdl7
liblvm2app2.2
liblzma2
libmagic1
libmagickcore3
libmagickwand3
libmailtransport4
libmeanwhile1
libmetacity-private0
libmicroblog4
libmission-control-plugins0
libmng1
libmono-addins-gui0.2-cil
libmono-addins0.2-cil
libmono-cairo2.0-cil
libmono-corlib2.0-cil
libmono-i18n-west2.0-cil
libmono-management2.0-cil
libmono-posix2.0-cil
libmono-security2.0-cil
libmono-sharpzip2.84-cil
libmono-system2.0-cil
libmono-zeroconf1.0-cil
libmozjs185-1.0
libmpc2
libmpfr4
libmtdev1
libmtp8
libmusicbrainz4c2a
libmysqlclient16
libmythes-1.2-0
libnautilus-extension1
libncurses5
libncursesw5
libneon27-gnutls
libnepomuk4
libnepomukquery4a
libnepomukutils4
libnet-dns-perl
libnet-domain-tld-perl
libnet-ip-perl
libnewt0.52
libnfnetlink0
libnice10
libnl1
libnm-glib-vpn1
libnm-glib2
libnm-util1
libnotify0.4-cil
libnotify4
libnspr4
libnspr4-0d
libnss-mdns
libnss3
libnss3-1d
liboobs-1-5
libopencc1
libopenexr6
liborbit2
liborc-0.4-0
libpam-ck-connector
libpam-gnome-keyring
libpango1.0-0
libpangomm-1.4-1
libparse-debianchangelog-perl
libparted0debian1
libpci3
libpciaccess0
libpcre3
libpcsclite1
libphonon4
libpipeline1
libpixman-1-0
libplasma3
libplist1
libpng12-0
libpolkit-agent-1-0
libpolkit-backend-1-0
libpolkit-gobject-1-0
libpolkit-gtk-1-0
libpolkit-qt-1-1
libportaudio2
libppl-c2
libppl7
libprotobuf6
libprotoc6
libproxy0
libpst4
libpth20
libpurple-bin
libpurple0
libpython2.6
libpython2.7
libqapt-runtime
libqapt1
libqca2
libqtassistantclient4
libqtwebkit4
libquvi0
librarian0
librasqal2
libraw1394-11
librdf0
libreadline5
libreadline6
librsvg2-2
librsvg2-common
libsane
libsane-hpaio
libsasl2-2
libsasl2-modules
libsdl1.2debian
libsdl1.2debian-pulseaudio
libselinux1
libsensors4
libsgutils2-2
libsigc++-2.0-0c2a
libslang2
libslp1
libsm6
libsndfile1
libsnmp-base
libsnmp15
libsolid4
libsoprano4
libsoup-gnome2.4-1
libsoup2.4-1
libspectre1
libspeechd2
libsqlite3-0
libss2
libssh-4
libssl0.9.8
libstdc++6
libstdc++6-4.5-dev
libstreamanalyzer0
libstreams0
libsub-name-perl
libtaglib2.0-cil
libtalloc2
libtasn1-3
libtdb1
libtelepathy-farsight0
libtelepathy-glib0
libtextcat-data
libtextcat0
libthai-data
libthai0
libthreadweaver4
libtiff4
libtotem-plparser17
libubuntuone-1.0-1
libubuntuone1.0-cil
libudev0
libunique-1.0-0
libunistring0
libunity-misc0
libunity4
libupower-glib1
liburi-perl
libusb-0.1-4
libusbmuxd1
libutouch-evemu1
libutouch-frame1
libutouch-geis1
libutouch-grail1
libuuid1
libv4l-0
libvala-0.10-0
libvirtodbc0
libvorbis0a
libvorbisenc2
libvorbisfile3
libvte-common
libvte9
libwebkitgtk-1.0-0
libwebkitgtk-1.0-common
libwmf0.2-7
libwmf0.2-7-gtk
libwnck-common
libwnck22
libwpd-0.9-9
libwpg-0.2-2
libwps-0.2-2
libwrap0
libwww-perl
libx11-6
libx11-data
libx11-xcb1
libxapian22
libxau6
libxaw7
libxcb-dri2-0
libxcb-render0
libxcb-shape0
libxcb-shm0
libxcb1
libxcomposite1
libxcursor1
libxdamage1
libxdmcp6
libxext6
libxfixes3
libxfont1
libxft2
libxi6
libxinerama1
libxkbfile1
libxklavier16
libxml2
libxml2-utils
libxmu6
libxmuu1
libxpm4
libxrandr2
libxrender1
libxres1
libxslt1.1
libxss1
libxt6
libxtst6
libxv1
libxvmc1
libxxf86dga1
libxxf86vm1
libzeitgeist-1.0-1
light-themes
lintian
linux-firmware
linux-generic
linux-headers-2.6.38-8
linux-headers-2.6.38-8-generic
linux-headers-generic
linux-image-2.6.38-8-generic
linux-image-generic
linux-libc-dev
linux-sound-base
lm-sensors
locales
login
logrotate
lsb-base
lsb-release
lshw
ltrace
make
man-db
manpages
manpages-dev
media-player-info
memtest86+
metacity
metacity-common
mime-support
mlocate
mobile-broadband-provider-info
modemmanager
mono-2.0-gac
mono-csharp-shell
mono-gac
mono-gmcs
mono-runtime
mountall
mousetweaks
msr-tools
mtr-tiny
myspell-en-gb
myspell-en-za
mysql-client-core-5.1
mysql-common
mysql-server-core-5.1
nano
nautilus
nautilus-data
nautilus-sendto-empathy
nautilus-share
ncurses-base
ncurses-bin
netbase
netcat-openbsd
network-manager
network-manager-gnome
network-manager-pptp
network-manager-pptp-gnome
notify-osd
notify-osd-icons
ntpdate
nvidia-common
obex-data-server
obexd-client
odbcinst
odbcinst1debian2
onboard
openprinting-ppds
openssh-client
openssl
os-prober
oxygen-icon-theme
parted
patch
pciutils
pcmciautils
phonon
pinyin-database
pitivi
pkg-config
plasma-scriptengine-declarative
plasma-scriptengine-javascript
pm-utils
policykit-1
policykit-1-gnome
policykit-desktop-privileges
popularity-contest
ppp
pppconfig
pptp-linux
procps
protobuf-compiler
psmisc
python
python-appindicator
python-apport
python-aptdaemon
python-aptdaemon-gtk
python-aptdaemon.gtk3widgets
python-aptdaemon.gtkwidgets
python-avahi
python-brlapi
python-cairo
python-central
python-chardet
python-couchdb
python-crypto
python-cups
python-dbus
python-debian
python-defer
python-desktopcouch-application
python-desktopcouch-records
python-egenix-mxdatetime
python-egenix-mxtools
python-farsight
python-gconf
python-gdbm
python-gmenu
python-gnome2
python-gnomeapplet
python-gnomecanvas
python-gnomekeyring
python-gnupginterface
python-gst0.10
python-gtksourceview2
python-gtkspell
python-httplib2
python-ibus
python-imaging
python-indicate
python-keyring
python-launchpad-integration
python-launchpadlib
python-lazr.restfulclient
python-lazr.uri
python-libproxy
python-libxml2
python-louis
python-mako
python-markupsafe
python-minimal
python-newt
python-notify
python-openssl
python-pam
python-pexpect
python-piston-mini-client
python-pkg-resources
python-problem-report
python-protobuf
python-pyatspi
python-pycurl
python-pygoocanvas
python-pyorbit
python-qt4
python-rdflib
python-serial
python-simplejson
python-sip
python-smbc
python-software-properties
python-speechd
python-support
python-telepathy
python-twisted-bin
python-twisted-core
python-twisted-names
python-twisted-web
python-ubuntuone
python-ubuntuone-control-panel
python-virtkey
python-vte
python-wadllib
python-webkit
python-wnck
python-wsgi-intercept
python-xapian
python-zope.interface
python2.6
python2.6-minimal
python2.7
python2.7-minimal
qapt-batch
quadrapassel
rarian-compat
readline-common
rfkill
rhythmbox
rhythmbox-plugin-cdrecorder
rhythmbox-plugins
rhythmbox-ubuntuone-music-store
rsync
rsyslog
rtkit
sane-utils
screen
screen-resolution-extra
seahorse
sed
sessioninstaller
sgml-base
sgml-data
shared-desktop-ontologies
shared-mime-info
shotwell
simple-scan
software-properties-gtk
software-properties-kde
soprano-daemon
speech-dispatcher
splix
ssh-askpass-gnome
ssl-cert
synaptic
syslinux
syslinux-common
system-tools-backends
tar
tcl8.4
tcpd
tcpdump
telepathy-butterfly
telepathy-gabble
telepathy-haze
telepathy-idle
telepathy-mission-control-5
telepathy-salut
time
tomboy
totem
totem-common
totem-mozilla
totem-plugins
transmission-common
transmission-gtk
tsclient
ttf-indic-fonts-core
ttf-kacst-one
ttf-lao
ttf-punjabi-fonts
ttf-takao-pgothic
ttf-ubuntu-font-family
ubufox
ubuntu-desktop
ubuntu-minimal
ubuntu-mono
ubuntu-sounds
ubuntu-standard
ubuntu-system-service
ubuntu-wallpapers
ubuntuone-control-panel
ubuntuone-control-panel-gtk
ucf
udev
udisks
ufw
unattended-upgrades
unity-asset-pool
unity-place-applications
unity-place-files
unzip
update-inetd
update-notifier
update-notifier-common
upower
ureadahead
usb-modeswitch
usb-modeswitch-data
usbmuxd
usbutils
uuid-runtime
vbetool
vim-common
vim-tiny
vinagre
virtuoso-minimal
virtuoso-opensource-6.1-bin
virtuoso-opensource-6.1-common
w3m
wget
whiptail
whois
wireless-crda
wireless-tools
wodim
wpasupplicant
x11-apps
x11-common
x11-session-utils
x11-utils
x11-xkb-utils
x11-xserver-utils
xauth
xbitmaps
xcursor-themes
xdg-user-dirs
xdg-utils
xfonts-100dpi
xfonts-75dpi
xfonts-base
xfonts-encodings
xfonts-scalable
xfonts-utils
xinit
xinput
xkb-data
xorg
xorg-docs-core
xscreensaver-data
xscreensaver-gl
xserver-xorg
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse
xserver-xorg-input-wacom
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-ati
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-fbdev
xserver-xorg-video-geode
xserver-xorg-video-i128
xserver-xorg-video-i740
xserver-xorg-video-mach64
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nouveau
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-qxl
xserver-xorg-video-r128
xserver-xorg-video-radeon
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-vesa
xserver-xorg-video-vmware
xserver-xorg-video-voodoo
xsltproc
xterm
xul-ext-ubufox
xulrunner-1.9.2
xz-utils
yelp
yelp-xsl
zeitgeist
zeitgeist-core
zeitgeist-datahub
zeitgeist-extension-fts
zenity
zip
zlib1g

```

Damn that's a lot of crap.

From Package Manager with 11 broken packages, after I "fix" them:

```
An error occurred

The following details are provided:

E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

hit close, then:

```
An error occurred

The following details are provided:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: _cache->open() failed, please report.
```

Whatever that means.  Okay, let's go to the terminal.

```
sudo apt-get -f install
...bunch of stuff...
After this operation, 375MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6 libgomp1 libgcc1 libstdc++6 libpcre3 libglib2.0-0 udev grub-pc
  grub-common python-desktopcouch-records python2.7-minimal libsqlite3-0
  python2.7 python-twisted-bin python-zope.interface python-twisted-core
  python-twisted-names libpython2.7 libaudio2 libjpeg62 libmng1
  libqtassistantclient4 libphonon4 libgstreamer0.10-0
  libgstreamer-plugins-base0.10-0 phonon libqtwebkit4 python-support
  python-sip python-qt4 libasound2 libattica0 libexiv2-10 libkdecore5
  libdbusmenu-qt2 libkdeui5 libkcmutils4 libkpty4 libkdesu5 libkdnssd4
  libclucene0ldbl libiodbc2 librdf0 soprano-daemon libsoprano4 libnepomuk4
  libnepomukquery4a libnepomukutils4 libsolid4 libstreams0 libstreamanalyzer0
  libkio5 libkemoticons4 libkfile4 libgif4 libkjsapi4 libkparts4
  libktexteditor4 libkhtml5 libkidletime4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libilmbase6 libopenexr6 libkdewebkit5 libqca2
  libthreadweaver4 libplasma3 libssh-4 kdebase-runtime-data
  libkatepartinterfaces4 libkjsembed4 libkntlm4 libkrosscore4 policykit-1
  libpolkit-backend-1-0 libgdk-pixbuf2.0-0 xserver-xorg-video-tseng
  xserver-xorg-video-siliconmotion xserver-xorg-video-r128
  xserver-xorg-video-mach64 xserver-xorg-video-radeon xserver-xorg-video-ati
  xserver-xorg-video-i740 xserver-xorg-video-geode xserver-xorg-video-nv
  xserver-xorg-video-chips xserver-xorg-video-trident xserver-xorg-video-s3
  xserver-xorg-video-i128 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-cirrus xserver-xorg-video-ark xserver-xorg-video-tdfx
  xserver-xorg-video-sisusb xserver-xorg-video-rendition
  xserver-xorg-video-vesa xserver-xorg-video-fbdev xserver-xorg-video-savage
  xserver-xorg-video-vmware xserver-xorg-video-openchrome
  xserver-xorg-video-s3virge xserver-xorg-video-voodoo xserver-xorg-video-apm
  xserver-xorg-video-sis xserver-xorg-input-mouse libmtdev1 libutouch-evemu1
  libutouch-frame1 libutouch-grail1 xserver-xorg-video-nouveau
  xserver-xorg-input-evdev xserver-xorg-input-wacom xserver-xorg-input-vmmouse
  xserver-xorg-input-synaptics console-setup keyboard-configuration
  libgpg-error0 libgcrypt11 libdrm-nouveau1a libpango1.0-0 libgail-common
  libgail18 gtk2-engines-pixbuf libgtk2.0-0 libpolkit-gtk-1-0
  libpolkit-agent-1-0 libpolkit-gobject-1-0 libpolkit-qt-1-1 kdelibs5-data
  docbook-xsl kdoctools kdelibs-bin kdelibs5-plugins oxygen-icon-theme
  shared-desktop-ontologies plasma-scriptengine-javascript
  plasma-scriptengine-declarative kdebase-runtime libkmime4 libkimap4
  libkldap4 kdepimlibs-kio-plugins libakonadi-kabc4 libkresources4 libkabc4
  libkpimutils4 libkcal4 libakonadi-kcal4 libakonadiprotocolinternals1
  libakonadi-kde4 libakonadi-kmime4 libmailtransport4 libmicroblog4
  libboost-program-options1.42.0 mysql-common libmysqlclient16
  mysql-server-core-5.1 mysql-client-core-5.1 akonadi-server kdepim-runtime
  libknewstuff2-4 libkprintutils4 python-minimal python-wsgi-intercept
  python-lazr.restfulclient libatspi1.0-0 gnome-mag libgirepository-1.0-1
  gir1.2-glib-2.0 libatspi2.0-0 gir1.2-atspi-2.0 python-pyatspi2 hpijs
  libhpmud0 libsane-hpaio hplip-data hplip-cups hplip libhyphen0 libicu44
  libmythes-1.2-0 libneon27-gnutls libnspr4-0d libnspr4 libnss3-1d libnss3
  libtextcat-data libtextcat0 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  python-httplib2 python-openssl nvidia-common python-libxml2 python-imaging
  python-markupsafe python-rdflib python-virtkey screen-resolution-extra
  python-crypto python-pam libxapian22 python-xapian python-simplejson
  command-not-found ufw python-problem-report python-cups python-smbc
  python-pyorbit python-cairo libcurl3-gnutls python-pycurl libnewt0.52
  python-newt python-lazr.uri python-gnomecanvas python-apport
  python-launchpad-integration python-brlapi python-egenix-mxdatetime
  python-software-properties computer-janitor python-egenix-mxtools
  python-twisted-web lsb-release jockey-common python-dbus python kdesudo
  libqapt1 libqapt-runtime qapt-batch software-properties-kde python-couchdb
  libdbusmenu-glib3 libdbusmenu-gtk3 libindicate5 indicator-messages
  indicator-application indicator-sound libappindicator1 indicator-session
  libindicator3 libjson-glib-1.0-0 libnotify4 pinyin-database appmenu-qt
  brasero-cdrkit growisofs dvd+rw-tools brasero libbrasero-media1 libsoup2.4-1
  libedataserver1.2-14 evolution-exchange evolution libcamel1.2-19
  libebackend1.2-0 libebook1.2-10 libgdata11 libecal1.2-8 libedata-book1.2-8
  libedata-cal1.2-10 libegroupwise1.2-13 evolution-data-server
  evolution-data-server-common libedataserverui1.2-11 libevolution
  evolution-common gir1.2-atk-1.0 libcairo-gobject2 gir1.2-freedesktop
  gir1.2-gdkpixbuf-2.0 ibus-pinyin-db-open-phrase icoutils
  kubuntu-debug-installer libreadline5 virtuoso-opensource-6.1-common
  odbcinst1debian2 odbcinst libvirtodbc0 totem-mozilla totem
  virtuoso-opensource-6.1-bin virtuoso-minimal aptdaemon-data libquvi0
  python-defer
Install these packages without verification [y/N]? y
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

Dang nabbit!

Okay, let's try:

```
 sudo apt-get update
...bunch of stuff...
Something wicked happened resolving 'af.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Really??  WTF.

```
sudo apt-get dist-upgrade -f
After this operation, 756MB of additional disk space will be used.
Do you want to continue [Y/n]? y
...bunch of stuff posted earlier...
Install these packages without verification [y/N]? y
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

```
sudo apt-get clean
ammo@ammocan:~$ sudo apt-get -f install
...whole bunch of stuff getting removed and reinstalled (in theory)...
Fetched 227MB in 16min 9s (234kB/s)                                            
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

:(  Me sad.  Thoughts/suggestions?

Hi let try this in this order one at a time.
```
sudo apt-get install -f install
```
```
sudo apt-get clean
```
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by CTolley on 2011-06-09
> **wildmanne39 said:**
> Hi let try this in this order one at a time.
```
sudo apt-get install -f install
```
```
sudo apt-get clean
```
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update && sudo apt-get upgrade
```

install -f returned the same error.

next two had no error

update and upgrade returned:

```
W: Failed to fetch http://af.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'af.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by wildmanne39 on 2011-06-09
> **CTolley said:**
> install -f returned the same error.

next two had no error

update and upgrade returned:

```
W: Failed to fetch http://af.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'af.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Hi, go into synaptic and uncheck [http://af.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://af.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg) then reload the list and try to update again. Also what version of ubuntu are you using?

---

### Post by CTolley on 2011-06-09
I'm using 10.10, with a partial upgrade to 11.04

Ran those four commands again and got the same error:

```
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

Thought it was working too.  It told me to run the update and upgrade with "-f" which it hadn't done before.

---

### Post by wildmanne39 on 2011-06-09
> **CTolley said:**
> I'm using 10.10, with a partial upgrade to 11.04

Ran those four commands again and got the same error:

```
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

Thought it was working too.  It told me to run the update and upgrade with "-f" which it hadn't done before.
Hi, I believe it is wanting you to 
```
sudo apt-get -f install
``` Partial upgrade will break you system, if only partly upgraded to natty then you should reinstall.

---

### Post by CTolley on 2011-06-10
Nope, that delivers the same feed back.  As does upgrade -f, update -f, the partial upgrade through Update Manager, and the Update/Upgrade through Synaptic.  They all crap out with the same error when it's time to start messing with packages.

---

### Post by CTolley on 2011-06-10
does it make a difference if my 

/usr/share/doc/apt/examples/configure-index.gz

is nothing but gibberish?  Not that I don't understand what's written, it's that it's written in wingdings.  

my 

/usr/share/doc/apt/examples/apt.conf

file is right though.  Well, it uses english, not sure if everything is there, but it's not corrupt.

---

### Post by wildmanne39 on 2011-06-10
> **CTolley said:**
> does it make a difference if my 

/usr/share/doc/apt/examples/configure-index.gz

is nothing but gibberish?  Not that I don't understand what's written, it's that it's written in wingdings.  

my 

/usr/share/doc/apt/examples/apt.conf

file is right though.  Well, it uses english, not sure if everything is there, but it's not corrupt.
Hi, I dont know where to tell you to go from here, if you only got part of your system upgraded and you have part of the old and new system running together the only thing I know to do is reinstall,you might mark this thread solved since this is not the same issue you were having and start a new one with the software not updating.

---

### Post by wildmanne39 on 2011-06-10
> **CTolley said:**
> does it make a difference if my 

/usr/share/doc/apt/examples/configure-index.gz

is nothing but gibberish?  Not that I don't understand what's written, it's that it's written in wingdings.  

my 

/usr/share/doc/apt/examples/apt.conf

file is right though.  Well, it uses english, not sure if everything is there, but it's not corrupt.
Hi, I ran across this while helping other people, try it before you reinstall.
```
sudo rm /var/lib/apt/lists/partial/*
```
```

sudo apt-get update
```

---

### Post by CTolley on 2011-06-11
No glory. 

New thread is [here]("http://ubuntuforums.org/showthread.php?t=1779799").

Thank you for the suggestion of the new thread.  I should have done that earlier.  And thank you all for your help in this thread.

---


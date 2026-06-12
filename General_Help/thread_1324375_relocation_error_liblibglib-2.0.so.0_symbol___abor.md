---
title: "relocation error: /lib/libglib-2.0.so.0: symbol __abort_msg, version GLIBC_PRIVATE"
date: 2009-11-12
forum: General Help
---

### Post by hart02 on 2009-11-12
I have fixed many errors in ubuntu since i first started with back when egdy was new.I am now at 9.10 & i am getting this error that makes me feel like a newbie

```
relocation error: /lib/libglib-2.0.so.0: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
```

this all started when I was trying to do upgrades on packages from a 9.10 build. I reinstalled my OS but i got it again.i cant find any thing from a search engine like google. Could someone tell me what is going on with this and how to fix this.here are what is my current package config setup looks like as of 11-12-09
```
acpi-support					install
acpid						install
adduser						install
aisleriot					install
alsa-base					install
alsa-utils					install
anacron						install
app-install-data				install
app-install-data-partner			install
apparmor					install
apparmor-utils					install
apport-symptoms					install
apt						install
apt-transport-https				install
apt-utils					install
aptitude					install
aspell						install
aspell-en					install
at						install
at-spi						install
avahi-autoipd					install
avahi-daemon					install
base-files					install
base-passwd					install
bash						install
bash-completion					install
bc						install
bcmwl-modaliases				install
bind9-host					install
binfmt-support					install
binutils					install
bluetooth					install
bluez						install
bluez-alsa					install
bluez-cups					install
bluez-gstreamer					install
bluez-utils					install
bogofilter					install
bogofilter-bdb					install
bogofilter-common				install
brasero						install
brltty						install
brltty-x11					install
bsdmainutils					install
bsdutils					install
busybox-initramfs				install
bzip2						install
ca-certificates					install
capplets-data					install
cdparanoia					install
checkbox					install
cli-common					install
command-not-found-data				install
compiz						install
compiz-core					install
compiz-fusion-plugins-extra			install
compiz-fusion-plugins-main			install
compiz-gnome					install
compiz-plugins					install
compiz-wrapper					install
compizconfig-backend-gconf			install
console-setup					install
console-terminus				install
consolekit					install
coreutils					install
couchdb-bin					deinstall
cpio						install
cpp						install
cpp-4.4						install
cron						install
cups						install
cups-bsd					install
cups-client					install
cups-common					install
cups-driver-gutenprint				install
dash						install
dbus						install
dbus-x11					install
dc						install
dcraw						install
debconf						install
debconf-i18n					install
debianutils					install
defoma						install
desktop-file-utils				install
devicekit-disks					install
devicekit-power					install
dhcp3-client					install
dhcp3-common					install
dictionaries-common				install
diff						install
dkms						install
dmidecode					install
dmsetup						install
dmz-cursor-theme				install
dnsmasq-base					install
dnsutils					install
doc-base					install
docbook-xml					install
dosfstools					install
dpkg						install
dvd+rw-tools					install
e2fslibs					install
e2fsprogs					install
ed						install
eject						install
empathy						install
empathy-doc					install
eog						install
erlang-base					install
erlang-crypto					deinstall
erlang-inets					deinstall
erlang-mnesia					deinstall
erlang-public-key				deinstall
erlang-runtime-tools				deinstall
erlang-ssl					deinstall
erlang-syntax-tools				deinstall
erlang-xmerl					deinstall
esound-clients					install
esound-common					install
espeak						install
espeak-data					install
ethtool						install
evince						install
evolution-common				install
evolution-data-server				install
evolution-data-server-common			install
evolution-documentation-en			install
evolution-webcal				install
example-content					install
f-spot						install
fakeroot					install
fglrx-modaliases				install
file						install
file-roller					install
findutils					install
finger						install
firefox						install
firefox-3.5					install
firefox-3.5-branding				install
firefox-3.5-gnome-support			install
firefox-gnome-support				install
fontconfig					install
fontconfig-config				install
foo2zjs						install
foomatic-db					install
foomatic-db-engine				install
foomatic-filters				install
friendly-recovery				install
ftp						install
fuse-utils					install
gamin						install
gcalctool					install
gcc						install
gcc-4.4						install
gcc-4.4-base					install
gconf-defaults-service				install
gconf-editor					install
gconf2						install
gconf2-common					install
gdb						install
gdm						install
gdm-guest-session				deinstall
gedit-common					install
genisoimage					install
geoip-database					deinstall
gettext-base					install
ggzcore-bin					install
ghostscript					install
ghostscript-cups				install
ghostscript-x					install
gimp-data					install
gksu						install
glines						install
gnect						install
gnibbles					install
gnobots2					install
gnome-accessibility-themes			install
gnome-applets-data				install
gnome-blackjack					install
gnome-bluetooth					install
gnome-desktop-data				install
gnome-disk-utility				deinstall
gnome-doc-utils					install
gnome-games-common				install
gnome-icon-theme				install
gnome-keyring					install
gnome-mag					install
gnome-mahjongg					install
gnome-media					install
gnome-media-common				install
gnome-mime-data					install
gnome-nettool					install
gnome-panel-data				install
gnome-pilot					install
gnome-pilot-conduits				install
gnome-power-manager				install
gnome-screensaver				install
gnome-session-bin				install
gnome-session-canberra				install
gnome-settings-daemon				install
gnome-system-monitor				install
gnome-system-tools				install
gnome-terminal					install
gnome-terminal-data				install
gnome-themes-selected				install
gnome-themes-ubuntu				install
gnome-user-guide				install
gnome-utils					install
gnometris					install
gnomine						install
gnotravex					install
gnotski						install
gnupg						install
gpgv						install
grep						install
groff-base					install
grub-common					install
grub-pc						deinstall
gsfonts						install
gstreamer0.10-alsa				install
gstreamer0.10-nice				install
gstreamer0.10-plugins-base			install
gstreamer0.10-plugins-base-apps			install
gstreamer0.10-plugins-good			install
gstreamer0.10-pulseaudio			install
gstreamer0.10-tools				install
gstreamer0.10-x					install
gtali						install
gtk2-engines					install
gtk2-engines-murrine				install
gtk2-engines-pixbuf				install
gucharmap					install
guile-1.8-libs					install
gvfs						install
gvfs-backends					install
gvfs-bin					install
gvfs-fuse					install
gzip						install
hal						install
hal-info					install
hdparm						install
hicolor-icon-theme				install
hostname					install
hpijs						install
hplip						install
hplip-cups					install
hplip-data					install
human-theme					install
humanity-icon-theme				deinstall
hunspell-en-us					install
iagno						install
ibus						install
ibus-gtk					deinstall
ibus-m17n					deinstall
ibus-table					install
ifupdown					install
im-switch					install
info						install
initramfs-tools					install
initscripts					install
inputattach					install
insserv						install
install-info					install
iproute						install
iptables					install
iputils-arping					install
iputils-ping					install
iputils-tracepath				install
iso-codes					install
kbd						install
kerneloops-daemon				deinstall
klibc-utils					install
language-pack-en				install
language-pack-en-base				install
language-pack-gnome-en				install
language-pack-gnome-en-base			install
language-support-en				deinstall
language-support-writing-en			install
laptop-detect					install
laptop-mode-tools				install
latex-xft-fonts					install
launchpad-integration				install
less						install
lftp						install
libaa1						install
libacl1						install
libanthy0					install
libapparmor-perl				install
libapparmor1					install
libarchive1					install
libart-2.0-2					install
libart2.0-cil					install
libasound2					install
libasound2-plugins				install
libaspell15					install
libatasmart4					install
libatk1.0-0					install
libatk1.0-data					install
libatm1						install
libatspi1.0-0					install
libattr1					install
libaudiofile0					install
libavahi-client3				install
libavahi-common-data				install
libavahi-common3				install
libavahi-core6					install
libavahi-glib1					install
libavahi-gobject0				install
libavahi-ui0					install
libavc1394-0					install
libbabl-0.0-0					install
libbeagle1					install
libbind9-50					install
libblkid1					install
libbluetooth3					install
libbonobo2-0					install
libbonobo2-common				install
libbonoboui2-0					install
libbonoboui2-common				install
libbrasero-media0				install
libbrlapi0.5					install
libbsd0						deinstall
libbz2-1.0					install
libc-bin					install
libc-dev-bin					install
libc6						install
libc6-dev					install
libc6-i686					install
libcaca0					install
libcairo-perl					install
libcairo2					install
libcairomm-1.0-1				install
libcamel1.2-14					install
libcanberra-gtk-module				install
libcanberra-gtk0				install
libcanberra-pulse				deinstall
libcanberra0					install
libcap2						install
libcdio-cdda0					install
libcdio-paranoia0				install
libcdio7					install
libcdparanoia0					install
libck-connector0				install
libclass-accessor-perl				install
libcloog-ppl0					install
libclutter-1.0-0				install
libclutter-gtk-0.10-0				install
libcolamd2.7.1					install
libcomerr2					install
libcompizconfig0				install
libcompress-bzip2-perl				deinstall
libcouchdb-glib-1.0-1				deinstall
libcroco3					install
libcryptui0					install
libcups2					install
libcupscgi1					deinstall
libcupsdriver1					deinstall
libcupsimage2					install
libcupsmime1					deinstall
libcupsppdc1					install
libcurl3					install
libcurl3-gnutls					install
libcwidget3					install
libdaemon0					install
libdatrie1					install
libdb4.5					deinstall
libdb4.7					install
libdb4.8					deinstall
libdbus-1-3					install
libdbus-glib-1-2				install
libdbusmenu-glib0				deinstall
libdbusmenu-gtk0				deinstall
libdecoration0					install
libdevkit-power-gobject1			install
libdevmapper1.02.1				install
libdirectfb-1.2-0				install
libdjvulibre-text				install
libdjvulibre21					install
libdns50					install
libdotconf1.0					install
libdrm-intel1					install
libdrm-radeon1					install
libdrm2						install
libdv4						install
libebackend1.2-0				install
libebook1.2-9					install
libecal1.2-7					install
libedata-book1.2-2				install
libedata-cal1.2-6				install
libedataserver1.2-11				install
libedataserverui1.2-8				install
libedit2					install
libeggdbus-1-0					install
libegroupwise1.2-13				install
libelf1						install
libempathy-common				install
libempathy-gtk-common				install
libempathy-gtk28				install
libempathy30					install
libenchant1c2a					install
libept0						install
libesd-alsa0					install
libespeak1					install
libevdocument1					install
libevent-1.4-2					deinstall
libevview1					install
libexchange-storage1.2-3			install
libexempi3					install
libexif12					install
libexpat1					install
libffi5						install
libflac8					install
libflickrnet2.2-cil				install
libfont-afm-perl				install
libfontconfig1					install
libfontenc1					install
libfreetype6					install
libfreezethaw-perl				install
libfribidi0					install
libfs6						install
libfuse2					install
libgadu3					install
libgail-common					install
libgail-gnome-module				install
libgail18					install
libgamin0					install
libgc1c2					install
libgcc1						install
libgconf2-4					install
libgconf2.0-cil					install
libgcr0						install
libgcrypt11					install
libgd2-noxpm					install
libgdata-common					deinstall
libgdata-google1.2-1				install
libgdata1.2-1					install
libgdata5					deinstall
libgdbm3					install
libgdict-1.0-6					install
libgdiplus					install
libgdu-gtk0					deinstall
libgdu0						install
libgegl-0.0-0					install
libgeoip1					install
libggz2						install
libggzcore9					install
libggzmod4					install
libgif4						install
libgimp2.0					install
libgksu2-0					install
libgl1-mesa-dri					install
libgl1-mesa-glx					install
libglade2-0					install
libglade2.0-cil					install
libglew1.5					install
libglib-perl					install
libglib2.0-0					install
libglib2.0-cil					install
libglib2.0-data					install
libglibmm-2.4-1c2a				install
libglitz-glx1					install
libglitz1					install
libglu1-mesa					install
libgmime-2.0-2a					install
libgmime-2.4-2					install
libgmime2.2a-cil				install
libgmp3c2					install
libgmpxx4ldbl					install
libgnome-bluetooth7				deinstall
libgnome-desktop-2-11				install
libgnome-keyring0				install
libgnome-keyring1.0-cil				install
libgnome-mag2					install
libgnome-media0					install
libgnome-menu2					install
libgnome-pilot2					install
libgnome-vfs2.0-cil				install
libgnome-window-settings1			install
libgnome2-0					install
libgnome2-canvas-perl				install
libgnome2-common				install
libgnome2-perl					install
libgnome2-vfs-perl				install
libgnome2.24-cil				install
libgnomecanvas2-0				install
libgnomecanvas2-common				install
libgnomekbd-common				install
libgnomekbd4					install
libgnomekbdui4					install
libgnomepanel2.24-cil				install
libgnomeui-0					install
libgnomeui-common				install
libgnomevfs2-0					install
libgnomevfs2-common				install
libgnomevfs2-extra				install
libgnutls26					install
libgomp1					install
libgp11-0					install
libgpg-error0					install
libgpgme11					install
libgphoto2-2					install
libgphoto2-port0				install
libgpm2						install
libgpod-common					install
libgpod4					install
libgraphviz4					install
libgs8						install
libgsf-1-114					install
libgsf-1-common					install
libgsl0ldbl					install
libgssapi-krb5-2				install
libgssdp-1.0-1					install
libgstfarsight0.10-0				install
libgstreamer-plugins-base0.10-0			install
libgstreamer0.10-0				install
libgtk-vnc-1.0-0				install
libgtk2-perl					install
libgtk2.0-0					install
libgtk2.0-bin					install
libgtk2.0-cil					install
libgtk2.0-common				install
libgtkhtml-editor-common			install
libgtkhtml-editor0				install
libgtkhtml2-0					install
libgtkhtml3.14-19				install
libgtkmm-2.4-1c2a				install
libgtksourceview2.0-0				install
libgtksourceview2.0-common			install
libgtkspell0					install
libgtop2-7					install
libgtop2-common					install
libgucharmap7					install
libgudev-1.0-0					install
libgupnp-1.0-2					install
libgupnp-igd-1.0-2				install
libgutenprint2					install
libgvfscommon0					install
libgweather-common				install
libgweather1					install
libhal-storage1					install
libhal1						install
libhtml-format-perl				install
libhtml-parser-perl				install
libhtml-tagset-perl				install
libhtml-tree-perl				install
libhunspell-1.2-0				install
libhyphen0					install
libibus1					install
libical0					install
libice6						install
libicu40					install
libicu42					deinstall
libidl0						install
libidn11					install
libiec61883-0					install
libieee1284-3					install
libijs-0.35					install
libilmbase6					install
libindicate-gtk1				deinstall
libindicate3					install
libio-string-perl				install
libisc50					install
libisccc50					install
libisccfg50					install
libiw29						install
libjasper1					install
libjpeg62					install
libjs-jquery					install
libjson-glib-1.0-0				install
libk5crypto3					install
libkeyutils1					install
libklibc					install
libkpathsea4					install
libkrb5-3					install
libkrb5support0					install
liblaunchpad-integration1			install
liblcms1					install
libldap-2.4-2					install
liblircclient0					install
liblocale-gettext-perl				install
liblockfile1					install
libloudmouth1-0					install
liblouis-data					deinstall
liblouis0					deinstall
liblpint-bonobo0				install
libltdl7					install
liblwres50					install
libm17n-0					deinstall
libmagic1					install
libmagickcore2					install
libmagickwand2					install
libmailtools-perl				install
libmeanwhile1					install
libmetacity0					install
libmldbm-perl					install
libmng1						install
libmono-addins-gui0.2-cil			install
libmono-addins0.2-cil				install
libmono-cairo2.0-cil				install
libmono-corlib2.0-cil				install
libmono-data-tds2.0-cil				install
libmono-i18n-west2.0-cil			install
libmono-posix2.0-cil				install
libmono-security2.0-cil				install
libmono-sharpzip2.84-cil			install
libmono-sqlite2.0-cil				install
libmono-system-data2.0-cil			install
libmono-system-web2.0-cil			install
libmono-system2.0-cil				install
libmono2.0-cil					install
libmpfr1ldbl					install
libmtp8						install
libmusicbrainz4c2a				install
libmysqlclient16				install
libnautilus-extension1				install
libncurses5					install
libncursesw5					install
libndesk-dbus-glib1.0-cil			install
libndesk-dbus1.0-cil				install
libneon27					install
libneon27-gnutls				install
libnet-dbus-perl				install
libnewt0.52					install
libnice0					install
libnl1						install
libnm-glib2					install
libnm-util1					install
libnotify1					install
libnspr4-0d					install
libnss-mdns					install
libnss3-1d					install
libntfs-3g54					deinstall
libogg0						install
liboil0.3					install
liboobs-1-4					install
libopenexr6					install
libopenobex1					install
liborbit2					install
libotf0						install
libpam-ck-connector				install
libpam-gnome-keyring				install
libpam-modules					install
libpam-runtime					install
libpam0g					install
libpanel-applet2-0				install
libpango-perl					deinstall
libpango1.0-0					install
libpango1.0-common				install
libpangomm-1.4-1				install
libpaper-utils					install
libpaper1					install
libparse-debianchangelog-perl			install
libparted1.8-12					install
libpcap0.8					install
libpci3						install
libpciaccess0					install
libpcre3					install
libpcsclite1					install
libperl5.10					install
libpisock9					install
libpisync1					install
libpixman-1-0					install
libpng12-0					install
libpolkit-agent-1-0				install
libpolkit-backend-1-0				install
libpolkit-dbus2					install
libpolkit-gobject-1-0				install
libpolkit-grant2				install
libpolkit-gtk-1-0				deinstall
libpolkit2					install
libpoppler-glib4				install
libpoppler5					install
libpopt0					install
libportaudio2					install
libppl-c2					install
libppl7						install
libpq5						install
libprotobuf3					install
libproxy0					install
libpth20					install
libpulse-browse0				install
libpulse-mainloop-glib0				install
libpulse0					install
libpurple-bin					install
libpurple0					install
libpython2.6					install
libraptor1					install
librarian0					install
librasqal1					install
libraw1394-11					install
librdf0						install
libreadline5					install
libreadline6					install
librpc-xml-perl					install
librsvg2-2					install
librsvg2-common					install
libsamplerate0					install
libsane						install
libsasl2-2					install
libsasl2-modules				install
libschroedinger-1.0-0				install
libsdl1.2debian					install
libsdl1.2debian-alsa				install
libselinux1					install
libsensors3					install
libsepol1					install
libsexy2					install
libsgutils2-2					install
libshout3					install
libsigc++-2.0-0c2a				install
libsilc-1.1-2					install
libsilcclient-1.1-3				deinstall
libslang2					install
libslp1						install
libsm6						install
libsmbclient					install
libsndfile1					install
libsnmp-base					install
libsnmp15					install
libsoup-gnome2.4-1				install
libsoup2.4-1					install
libspectre1					install
libspeechd2					install
libspeex1					install
libspeexdsp1					install
libsqlite0					install
libsqlite3-0					install
libss2						install
libssl0.9.8					install
libstartup-notification0			install
libstdc++6					install
libstlport4.6ldbl				install
libsub-name-perl				deinstall
libsysfs2					install
libtag1-vanilla					deinstall
libtag1c2a					install
libtalloc1					install
libtasn1-3					install
libtdb1						install
libtelepathy-farsight0				install
libtelepathy-glib0				install
libterm-readkey-perl				install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
libthai-data					install
libthai0					install
libtheora0					install
libtie-ixhash-perl				install
libtiff4					install
libtimedate-perl				install
libtotem-plparser12				install
libtrackerclient0				install
libts-0.0-0					install
libudev0					install
libunique-1.0-0					install
liburi-perl					install
libusb-0.1-4					install
libusplash0					install
libuuid-perl					install
libuuid1					install
libv4l-0					install
libvisual-0.4-0					install
libvisual-0.4-plugins				install
libvorbis0a					install
libvorbisenc2					install
libvorbisfile3					install
libvte-common					install
libvte9						install
libwavpack1					install
libwbclient0					install
libwebkit-1.0-2					install
libwebkit-1.0-common				install
libwmf0.2-7					install
libwmf0.2-7-gtk					install
libwnck-common					install
libwnck22					install
libwpd8c2a					install
libwpg-0.1-1					install
libwps-0.1-1					install
libwrap0					install
libwww-perl					install
libx11-6					install
libx11-data					install
libx86-1					install
libxapian15					install
libxau6						install
libxaw7						install
libxcb-atom1					install
libxcb-aux0					install
libxcb-event1					install
libxcb-render-util0				install
libxcb-render0					install
libxcb1						install
libxcomposite1					install
libxcursor1					install
libxdamage1					install
libxdmcp6					install
libxext6					install
libxfixes3					install
libxfont1					install
libxft2						install
libxi6						install
libxinerama1					install
libxkbfile1					install
libxklavier15					install
libxml-parser-perl				install
libxml-twig-perl				install
libxml-xpath-perl				install
libxml2						install
libxml2-utils					install
libxmu6						install
libxmuu1					install
libxp6						install
libxpm4						install
libxrandr2					install
libxrender1					install
libxres1					install
libxslt1.1					install
libxss1						install
libxt6						install
libxtrap6					install
libxtst6					install
libxv1						install
libxvmc1					install
libxxf86dga1					install
libxxf86misc1					install
libxxf86vm1					install
libzephyr4					deinstall
linux-firmware					install
linux-generic					deinstall
linux-generic-pae				install
linux-headers-2.6.31-11				deinstall
linux-headers-2.6.31-11-generic			deinstall
linux-headers-generic				install
linux-image-2.6.31-11-generic			deinstall
linux-image-2.6.31-15-generic-pae		deinstall
linux-image-generic				deinstall
linux-image-generic-pae				install
linux-libc-dev					install
linux-sound-base				install
locales						install
lockfile-progs					install
login						install
logrotate					install
lp-solve					install
lsb-base					install
lsb-release					install
lshw						install
lsof						install
ltrace						install
lzma						install
m17n-contrib					deinstall
m17n-db						deinstall
make						install
makedev						install
man-db						install
manpages					install
mawk						install
media-player-info				deinstall
memtest86+					install
mesa-utils					install
metacity					install
metacity-common					install
mime-support					install
min12xxw					install
mlocate						install
mobile-broadband-provider-info			install
modemmanager					deinstall
module-init-tools				install
mono-2.0-gac					install
mono-gac					install
mono-runtime					install
mount						install
mountall					install
mousetweaks					install
mscompress					install
mtools						install
mtr-tiny					install
myspell-en-au					install
myspell-en-gb					install
myspell-en-za					install
mysql-common					install
nano						install
nautilus-data					install
nautilus-sendto					install
ncurses-base					install
ncurses-bin					install
net-tools					install
netbase						install
netcat						install
netcat-traditional				install
network-manager-gnome				purge
notify-osd					install
notify-osd-icons				deinstall
ntfs-3g						install
ntpdate						install
nvidia-173-modaliases				deinstall
nvidia-185-modaliases				deinstall
nvidia-96-modaliases				deinstall
nvidia-common					install
obex-data-server				install
obexd-client					deinstall
onboard						install
openoffice.org-base-core			install
openoffice.org-calc				install
openoffice.org-common				install
openoffice.org-core				install
openoffice.org-draw				install
openoffice.org-emailmerge			install
openoffice.org-gnome				install
openoffice.org-gtk				install
openoffice.org-help-en-us			install
openoffice.org-hyphenation			install
openoffice.org-hyphenation-en-us		install
openoffice.org-impress				install
openoffice.org-math				install
openoffice.org-style-human			install
openoffice.org-thesaurus-en-au			install
openoffice.org-thesaurus-en-us			install
openoffice.org-writer				install
openprinting-ppds				install
openssh-client					install
openssl						install
os-prober					install
parted						install
passwd						install
patch						install
pciutils					install
pcmciautils					install
perl						install
perl-base					install
perl-modules					install
pkg-config					install
pm-utils					install
pnm2ppa						install
policykit					install
policykit-1					install
policykit-1-gnome				install
poppler-utils					install
popularity-contest				install
powermgmt-base					install
ppp						install
pppconfig					install
pppoeconf					install
procps						install
protobuf-compiler				deinstall
psfontmgr					install
psmisc						install
pulseaudio					install
pulseaudio-esound-compat			install
pulseaudio-module-bluetooth			deinstall
pulseaudio-module-gconf				install
pulseaudio-module-udev				deinstall
pulseaudio-module-x11				install
pulseaudio-utils				install
pxljr						install
python						install
python-apt					install
python-aptdaemon				deinstall
python-aptdaemon-gtk				deinstall
python-avahi					install
python-brlapi					install
python-cairo					install
python-central					install
python-configglue				deinstall
python-couchdb					deinstall
python-crypto					install
python-cups					install
python-cupshelpers				install
python-dbus					install
python-debian					install
python-fstab					install
python-gconf					install
python-gdbm					install
python-glade2					install
python-gmenu					install
python-gnome2					install
python-gnomeapplet				deinstall
python-gnomecanvas				install
python-gnomekeyring				deinstall
python-gnupginterface				install
python-gobject					install
python-gst0.10					install
python-gtk2					install
python-gtkhtml2					install
python-gtksourceview2				install
python-httplib2					install
python-ibus					install
python-imaging					install
python-launchpad-integration			install
python-launchpadlib				install
python-lazr-restfulclient			deinstall
python-lazr-uri					deinstall
python-libxml2					install
python-louis					deinstall
python-minimal					install
python-newt					install
python-notify					install
python-oauth					deinstall
python-openssl					install
python-pam					install
python-papyon					install
python-pkg-resources				install
python-problem-report				install
python-protobuf					deinstall
python-pyatspi					install
python-pycurl					install
python-pyinotify				install
python-pyorbit					install
python-rdflib					install
python-serial					install
python-sexy					install
python-simplejson				install
python-smbc					install
python-speechd					deinstall
python-support					install
python-telepathy				install
python-twisted-bin				install
python-twisted-core				install
python-twisted-names				install
python-twisted-web				install
python-ubuntuone-client				deinstall
python-ubuntuone-storageprotocol		deinstall
python-uno					install
python-virtkey					install
python-vte					install
python-wadllib					install
python-webkit					install
python-xapian					install
python-xdg					install
python-xkit					install
python-zope.interface				deinstall
python2.5					install
python2.5-minimal				install
python2.6					install
python2.6-minimal				install
radeontool					install
raptor-utils					install
rarian-compat					install
rdesktop					install
readline-common					install
redland-utils					install
rhythmbox					install
rss-glx						install
rsync						install
rsyslog						install
rtkit						deinstall
samba-common					install
samba-common-bin				deinstall
same-gnome					install
sane-utils					install
screen						install
screen-resolution-extra				install
screensaver-default-images			install
seahorse					install
sed						install
sgml-base					install
sgml-data					install
shared-mime-info				install
smartdimmer					install
smbclient					install
speech-dispatcher				install
splix						install
sreadahead					deinstall
ssh-askpass-gnome				install
ssl-cert					install
strace						install
sudo						install
synaptic					install
syslinux					install
system-config-printer-common			install
system-config-printer-gnome			install
system-config-printer-udev			install
system-tools-backends				install
sysv-rc						install
sysvinit-utils					install
tar						install
tasksel						install
tasksel-data					install
tcl8.4						install
tcpd						install
tcpdump						install
telepathy-butterfly				install
telepathy-gabble				install
telepathy-haze					install
telepathy-idle					deinstall
telepathy-mission-control-5			install
telepathy-salut					install
telnet						install
time						install
tk8.4						install
tomboy						install
toshset						install
totem						install
totem-common					install
totem-mozilla					install
totem-plugins					install
transmission-common				install
transmission-gtk				install
tsclient					install
tsconf						install
ttf-dejavu-core					install
ttf-freefont					install
ttf-indic-fonts-core				install
ttf-kacst					install
ttf-lao						install
ttf-opensymbol					install
ttf-thai-tlwg					install
ttf-unfonts-core				install
ttf-vlgothic					deinstall
ttf-wqy-zenhei					install
tzdata						install
ubuntu-artwork					install
ubuntu-docs					install
ubuntu-keyring					install
ubuntu-minimal					install
ubuntu-sounds					install
ubuntu-standard					install
ubuntu-wallpapers				install
ubuntu-xsplash-artwork				deinstall
ucf						install
udev						install
ufw						install
uno-libs3					install
unzip						install
update-inetd					install
update-manager					purge
update-notifier					purge
upstart						install
ure						install
usb-creator-common				deinstall
usb-creator-gtk					deinstall
usbutils					install
usplash						install
usplash-theme-ubuntu				install
util-linux					install
uuid-runtime					install
vbetool						install
vim-common					install
vim-tiny					install
vinagre						install
vino						install
w3m						install
wamerican					install
wbritish					install
wget						install
whiptail					install
whois						install
wireless-crda					install
wireless-tools					install
wodim						install
wpasupplicant					install
x-ttcidfont-conf				install
x11-apps					install
x11-common					install
x11-session-utils				install
x11-utils					install
x11-xfs-utils					install
x11-xkb-utils					install
x11-xserver-utils				install
xauth						install
xbitmaps					install
xcursor-themes					install
xdg-user-dirs					install
xdg-user-dirs-gtk				install
xdg-utils					install
xfonts-100dpi					install
xfonts-75dpi					install
xfonts-base					install
xfonts-encodings				install
xfonts-mathml					deinstall
xfonts-scalable					install
xfonts-utils					install
xinit						install
xinput						install
xkb-data					install
xml-core					install
xorg						install
xorg-docs-core					deinstall
xsane						install
xsane-common					install
xscreensaver-data				install
xscreensaver-gl					install
xserver-common					install
xserver-xorg					install
xserver-xorg-core				install
xserver-xorg-input-all				install
xserver-xorg-input-evdev			install
xserver-xorg-input-synaptics			install
xserver-xorg-input-wacom			install
xserver-xorg-video-all				install
xserver-xorg-video-apm				install
xserver-xorg-video-ark				install
xserver-xorg-video-ati				install
xserver-xorg-video-chips			install
xserver-xorg-video-cirrus			install
xserver-xorg-video-fbdev			install
xserver-xorg-video-geode			install
xserver-xorg-video-i128				install
xserver-xorg-video-i740				install
xserver-xorg-video-intel			install
xserver-xorg-video-mach64			install
xserver-xorg-video-mga				install
xserver-xorg-video-neomagic			install
xserver-xorg-video-nv				install
xserver-xorg-video-openchrome			install
xserver-xorg-video-r128				install
xserver-xorg-video-radeon			install
xserver-xorg-video-rendition			install
xserver-xorg-video-s3				install
xserver-xorg-video-s3virge			install
xserver-xorg-video-savage			install
xserver-xorg-video-siliconmotion		install
xserver-xorg-video-sis				install
xserver-xorg-video-sisusb			install
xserver-xorg-video-tdfx				install
xserver-xorg-video-trident			install
xserver-xorg-video-tseng			install
xserver-xorg-video-v4l				install
xserver-xorg-video-vesa				install
xserver-xorg-video-vmware			install
xserver-xorg-video-voodoo			install
xsltproc					install
xsplash						deinstall
xterm						install
xulrunner-1.9.1					install
xulrunner-1.9.1-gnome-support			install
yelp						install
zenity						install
zip						install
zlib1g						install
```

---

### Post by jackb2009 on 2009-11-20
Hello,
 
   I am having the same problem while trying to upgrade to 9.10. When upgrading sun-java6-jre_6-15-1_all.deb. get same relocation error. Did you were able to solve it, let me know how. I am upgrading and the server is offline. Thanks in advance,
Jack

---

### Post by radi5 on 2009-12-04
Hi together,

I have just registred to join this thread. I have the same problem here. Did you find any solution or idea whats wrong? It seems that this is a quite seldom problem. Could it be hardware dependend issue?

I'm running on a LG S510.

best regards
radi5

---

### Post by stelf on 2009-12-30
Hi Everyone,

Been stuck with this issue for days since I failed to do the karmic upgrade. Hopefully, after days confusion, i did a move forward, though I still haven't managed to fully recover the system.

Some background info first (not quite sure if this is not actually supposed to be filed as bug report)

* it was for some weeks time that the auto updates suggested partial or incomplete upgrade took place. not in detail which package caused this, though i guess it's one of the mandatory lib packages

* the system was quite useful before the upgrade

* I've tried to *aptitude safe-upgrade* where the relocation error was first noted, though I initially ignored it, since I'm not in complete detail of apt/aptitude/dpkg. Basically, aptitude suggested to upgrade nearly every package on the system (900+ upgraded) and to DL some 60MBytes... which seemed okay, since when upgrades take place most packages are affeceteed.

* I've noticed a lot of packages did not successfully upgrade, such as :

dbus
gconf2
...(some other 5)

AFAIK dbus is becoming more and more important since the move from HAL, and it may be the package causing the trouble. though this can 

* almost immediately after the failed upgrade the system became unstable outputting various relocation/link errors. i guess some libs' dependencies were severely damaged or not processed at all. i had no other option, but to reboot. honestly, i didn't expect it to  be that major, but just a race condition of lib deps during upgrade.

...


well, this got me to the point where Ubuntu fails to boot, screen freezes with splash. removing the "quiet splash" directives from grub revealed the real trouble - kernel fails to load with a kernel panic and the** __abort_msg** symbol missing.

what i did next was to spend days reading forums and posts, just to find out that it's a new December'09 issue that others encounter in quite a similar fashion. well, not much of a help though, no one did provide a complete/working solution...

I thought it should be possible to recover Ubuntu in a Windows-fashion, by simply reinstalling. well, dumb idea, though it could've saved effort if a tool such as "rebuild existing installation based on version number" ever existed.

By that time it was becoming clear that the issue is some lib-linking kind of thing, so I tried to **chroot** to the damaged partition, check symlinks and do **ldconfig,** but this did not fix the issue.  

I also tried running **apt-get** to fix dependencies, but this resulted in nearly the same output as the initial upgrade attempt. 

Then I realized that I've used a 10.04 beta CD to boot, that was supposed to have all these libraries properly sorted. A quick check of libraries' symbols on both the live 10.04 and the broken 9.10 revealed that **__abort_msg **string was missing in my 9.10's** libc.so.6 **and[B] libglib-2.0.so. 

[/B]Since it's the same architecture, I've decided to save the current versions and bring the 10.04 manually into /lib. Well, now I could at least boot, though i got the erroneous X prompt with KBD and mouse frozen. 

Hopefully the recovery boot option was working and I was able to go and run the basic dpkg fix script. Running dpkg --configure --pending fixed all pending updates, but the system still fails to boot into X (though now I get a brand new error and still no mouse/kbd)

I hope this makes sense, I'll post further instructions in case I manage to reclaim my system, though its' still way to go, and aptitude keeps reporting some 900+ packages scheduled for upgrade.

Best luck to everyone, though this seems a major issue and Canonical should be really serious about it.

---

### Post by wesli_1 on 2010-03-27
Hi guys,

I have had the same problem on 9.10 desktop after trying to upgrade packages, failing the first time, then suggesting partial upgrade. Now unable to boot, gets stuck on the black screen with the white ubuntu logo (doesn't pulsate like it should). Starting in recovery mode gives an error "gave up waiting for root device"

The problems packages for me were dbus, hal, and rhythmbox.

I also get the same "relocation error..." when trying to execute halt, shutdown, or restart.

I've seen plenty of other posts around the internet on this problem, but no solutions... yet.

Here's some more info, I hope it helps with a solution.


```

# dpkg --configure -a
Setting up dbus (1.2.24-1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LANG = "C.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LANG = "C.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
update-rc.d: warning: /etc/init.d/dbus missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
start: relocation error: start: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of hal:
 hal depends on dbus (>= 0.61); however:
  Package dbus is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 hal
 
``````

# halt
halt: relocation error: halt: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference

``````

# apt-get install dbus
Reading package lists...
Building dependency tree...
Reading state information...
hal is already the newest version.
The following packages were automatically installed and are no longer required:
  libmtp8 linux-headers-2.6.31-16 linux-headers-2.6.31-19 libcompizconfig0
  libdmraid1.0.0.rc15 libdmraid1.0.0.rc16 libgda-4.0-common apport-symptoms
  liblog-log4perl-perl python-gnome2-extras libparams-validate-perl
  libdbusmenu-glib0 compiz-wrapper libdecoration0 bcmwl-modaliases
  compizconfig-backend-gconf libcpufreq0 python-gda python-gdl python-gtkspell
  python-gtkmozembed compiz-plugins liblog-dispatch-perl gnome-about
  libgda-4.0-4 python-eggtrayicon python-sexy libdbusmenu-gtk0
  libipc-shareable-perl linux-headers-2.6.31-16-generic pulseaudio-utils
  fglrx-modaliases libslab0a nvidia-173-modaliases libgnome-window-settings1
  nvidia-185-modaliases linux-headers-2.6.31-19-generic paman nvidia-common
  librrds-perl compiz-fusion-plugins-extra python-gksu2 libpulse-browse0
  python-xkit watershed compiz-core compiz-fusion-plugins-main pavumeter
  mscompress nvidia-96-modaliases libgdl-1-3 compiz-gnome gnome-panel-data
  libgdl-1-common
Use 'apt-get autoremove' to remove them.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LANG = "C.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
0 upgraded, 0 newly installed, 0 to remove and 1056 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up dbus (1.2.24-1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LANG = "C.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en",
    LC_ALL = (unset),
    LANG = "C.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
update-rc.d: warning: /etc/init.d/dbus missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
start: relocation error: start: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of hal:
 hal depends on dbus (>= 0.61); however:
  Package dbus is not configured yet.
dpkg: error processing hal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

---

### Post by wesli_1 on 2010-03-31
Hi guys

Just letting everyone know that I ended up having to reinstall ubuntu to solve this problem.

Also turns out the reason I couldn't boot was because lvm2 was corrupted therefore unable to mount root partition which was a lvm volume

wesli_1

---

### Post by Sepiraph on 2010-05-26
There is a bug report for this ([https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/486576](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/486576)) but no fix. :(

Also it may be similar to [http://ubuntuforums.org/showthread.php?p=9366098#post9366098](http://ubuntuforums.org/showthread.php?p=9366098#post9366098)

---


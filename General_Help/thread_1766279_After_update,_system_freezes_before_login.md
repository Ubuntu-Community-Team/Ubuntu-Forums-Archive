---
title: "After update, system freezes before login"
date: 2011-05-24
forum: General Help
---

### Post by MiOiM on 2011-05-24
Hello all.

I am running 64b Ubuntu 10.10 in an external USB HD in a Asus 1015PED netbook. Everything was working fine until I run a huge update. Now the system freezes in the Ubuntu logo, just after a battery check [OK]
I can start into recovery mode, but I cannot access into my documents -I think they are encrypted...-
This is the update history:

> Commit Log for Sun May 22 11:36:21 2011


Removed the following packages:
anacron
apport
apport-gtk
at
byobu
evolution
evolution-couchdb
evolution-exchange
friendly-recovery
gdm
gdm-guest-session
gnome-user-guide-en
libgvfscommon0
network-manager
network-manager-gnome
plymouth-label
plymouth-theme-ubuntu-logo
screen
synce-gvfs
ubuntu-desktop
ubuntu-minimal
ubuntu-standard
ufw
ureadahead

Upgraded the following packages:
acpi-support (0.137) to 0.137-5
acpid (1.0.10-5ubuntu4) to 1:2.0.7-1
adduser (3.112ubuntu1) to 3.112+nmu2
alacarte (0.13.2-0ubuntu1) to 0.13.2-1
alsa-base (1.0.23+dfsg-1ubuntu4) to 1.0.23+dfsg-2
alsa-utils (1.0.23-2ubuntu3.4) to 1.0.23-3
app-install-data (0.10.10.6) to 2010.11.17
apt (0.8.3ubuntu7.1) to 0.8.10.3
apt-transport-https (0.8.3ubuntu7.1) to 0.8.10.3
apt-utils (0.8.3ubuntu7.1) to 0.8.10.3
apt-xapian-index (0.39ubuntu1) to 0.41
apturl (0.4.1ubuntu7) to 0.4.1ubuntu7.1
apturl-common (0.4.1ubuntu7) to 0.4.1ubuntu7.1
aspell-en (6.0-0-5.1ubuntu3) to 6.0-0-6
avahi-autoipd (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
avahi-daemon (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
avahi-utils (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
base-files (5.0.0ubuntu23) to 6.0squeeze1
bash (4.1-2ubuntu4) to 4.1-3
bash-completion (1:1.2-2ubuntu1.1) to 1:1.2-3
bind9-host (1:9.7.1.dfsg.P2-2ubuntu0.2) to 1:9.7.2.dfsg.P3-1.1
bogofilter (1.2.2-1ubuntu1) to 1.2.2-2
bogofilter-bdb (1.2.2-1ubuntu1) to 1.2.2-2
bogofilter-common (1.2.2-1ubuntu1) to 1.2.2-2
brltty (4.2-3ubuntu1) to 4.2-7
brltty-x11 (4.2-3ubuntu1) to 4.2-7
bsdmainutils (8.0.11ubuntu1) to 8.0.13
bsdutils (1:2.17.2-0ubuntu1.10.10.2) to 1:2.17.2-9
busybox-static (1:1.15.3-1ubuntu5) to 1:1.17.1-8
bzip2 (1.0.5-4ubuntu1) to 1.0.5-6
ca-certificates (20090814) to 20090814+nmu2
chromium-browser (11.0.696.65~r84435-0ubuntu0.10.10.1) to 11.0.696.68~r84545-0ubuntu0.10.10.1
chromium-browser-inspector (11.0.696.65~r84435-0ubuntu0.10.10.1) to 11.0.696.68~r84545-0ubuntu0.10.10.1
chromium-browser-l10n (11.0.696.65~r84435-0ubuntu0.10.10.1) to 11.0.696.68~r84545-0ubuntu0.10.10.1
chromium-codecs-ffmpeg (11.0.696.65~r84435-0ubuntu0.10.10.1) to 11.0.696.68~r84545-0ubuntu0.10.10.1
compizconfig-settings-manager (0.8.2-0ubuntu1) to 0.8.4-2
console-setup (1.34ubuntu15) to 1.68+squeeze2
cron (3.0pl1-114ubuntu1) to 3.0pl1-116
cryptsetup (2:1.1.2-1ubuntu1) to 2:1.1.3-4squeeze2
cups (1.4.4-6ubuntu2.3) to 1.4.4-7
cups-bsd (1.4.4-6ubuntu2.3) to 1.4.4-7
cups-client (1.4.4-6ubuntu2.3) to 1.4.4-7
cups-common (1.4.4-6ubuntu2.3) to 1.4.4-7
cups-driver-gutenprint (5.2.6-0ubuntu8) to 5.2.6-1
cups-ppdc (1.4.4-6ubuntu2.3) to 1.4.4-7
dash (0.5.5.1-7ubuntu1) to 0.5.5.1-7.4
dcraw (8.99-1) to 8.99-1+b1
debconf (1.5.32ubuntu3) to 1.5.36.1
debconf-i18n (1.5.32ubuntu3) to 1.5.36.1
debianutils (3.2.3) to 3.4
deskbar-applet (2.30.1-1ubuntu2) to 2.32.0-1
dhcp3-client (3.1.3-2ubuntu6.2) to 4.1.1-P1-15+squeeze1
dhcp3-common (3.1.3-2ubuntu6.2) to 4.1.1-P1-15+squeeze1
dictionaries-common (1.5.11ubuntu1) to 1.5.17
dkms (2.1.1.2-3ubuntu1.1) to 2.1.1.2-5
dmsetup (2:1.02.39-1ubuntu6) to 2:1.02.48-5
dmz-cursor-theme (0.4.1) to 0.4.3
dnsmasq-base (2.55-1) to 2.55-2
dnsutils (1:9.7.1.dfsg.P2-2ubuntu0.2) to 1:9.7.2.dfsg.P3-1.1
dpkg (1.15.8.4ubuntu3.1) to 1.15.8.10
e2fslibs (1.41.12-1ubuntu2) to 1.41.12-2
e2fsprogs (1.41.12-1ubuntu2) to 1.41.12-2
ecryptfs-utils (83-0ubuntu3) to 83-4
ed (1.4-1build1) to 1.4-3
eject (2.1.5+deb1+cvs20081104-7) to 2.1.5+deb1+cvs20081104-7.1
erlang-base (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-crypto (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-inets (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-mnesia (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-public-key (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-runtime-tools (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-ssl (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-syntax-tools (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
erlang-xmerl (1:13.b.3-dfsg-2ubuntu3) to 1:14.a-dfsg-3
evolution-common (2.30.3-1ubuntu7.3) to 2.30.3-5
exiftran (2.07-3) to 2.07-6
exiv2 (0.19-3) to 0.20-2
file (5.03-5ubuntu1) to 5.04-5
findutils (4.4.2-1ubuntu1) to 4.4.2-1+b1
fontconfig (2.8.0-2ubuntu1) to 2.8.0-2.1
fontconfig-config (2.8.0-2ubuntu1) to 2.8.0-2.1
foomatic-filters (4.0.5-0ubuntu3) to 4.0.5-6
fuse-utils (2.8.4-1ubuntu1.3) to 2.8.4-1.1
gamin (0.1.10-1ubuntu3) to 0.1.10-2+b1
gedit (2.30.3-1ubuntu1) to 2.30.4-1squeeze1
gedit-common (2.30.3-1ubuntu1) to 2.30.4-1squeeze1
genisoimage (9:1.1.10-1ubuntu3) to 9:1.1.11-1
geoip-database (1.4.7~beta5+dfsg-1) to 1.4.7~beta6+dfsg-1
gettext-base (0.18.1.1-1ubuntu2) to 0.18.1.1-3
gksu (2.0.2-2ubuntu3) to 2.0.2-5
gnome-codec-install (0.4.7ubuntu2) to 0.4.7+nmu1
gnome-power-manager (2.32.0-0ubuntu1.1) to 2.32.0-2
gnome-screensaver (2.30.0-1ubuntu1.1) to 2.30.0-2squeeze1
gnome-user-guide (2.30.0+git20100403ubuntu2) to 2.30.1-1
gnupg (1.4.10-2ubuntu2) to 1.4.10-4
gpgv (1.4.10-2ubuntu2) to 1.4.10-4
grub-common (1.98+20100804-5ubuntu3) to 1.98+20100804-14
grub-pc (1.98+20100804-5ubuntu3) to 1.98+20100804-14
gvfs (1.6.4-0ubuntu1.1) to 1.6.4-3
gvfs-backends (1.6.4-0ubuntu1.1) to 1.6.4-3
gvfs-fuse (1.6.4-0ubuntu1.1) to 1.6.4-3
hal (0.5.14-0ubuntu6) to 0.5.14-3
hdparm (9.27-2ubuntu2) to 9.32-1
hicolor-icon-theme (0.11-1) to 0.12-1
hotot (1:0.9.6~hg785-0ubuntu0ppa1~maverick1) to 1:0.9.6~hg792-0ubuntu0ppa1~maverick1
hpijs (3.10.6-1ubuntu10.2) to 3.10.6-2
hplip (3.10.6-1ubuntu10.2) to 3.10.6-2
hplip-cups (3.10.6-1ubuntu10.2) to 3.10.6-2
hplip-data (3.10.6-1ubuntu10.2) to 3.10.6-2
hwdata (0.227-1) to 0.230-1
idle (2.6.6-2ubuntu2) to 2.6.6-3+squeeze6
idle-python2.6 (2.6.6-5ubuntu1) to 2.6.6-8
imagemagick (7:6.6.2.6-1ubuntu1.1) to 8:6.6.0.4-3
info (4.13a.dfsg.1-5ubuntu1) to 4.13a.dfsg.1-6
initramfs-tools (0.98.1ubuntu6) to 0.98.8
initscripts (2.87dsf-4ubuntu19.1) to 2.88dsf-13.1
install-info (4.13a.dfsg.1-5ubuntu1) to 4.13a.dfsg.1-6
iproute (20100519-2) to 20100519-3
iptables (1.4.4-2ubuntu3) to 1.4.8-3
iputils-arping (3:20100418-2ubuntu1) to 3:20100418-3
iputils-ping (3:20100418-2ubuntu1) to 3:20100418-3
iputils-tracepath (3:20100418-2ubuntu1) to 3:20100418-3
irqbalance (0.56-0ubuntu2) to 0.56-1
iso-codes (3.17-1) to 3.23-1
java-common (0.38) to 0.40
kbd (1.15-1ubuntu3) to 1.15.2-2
lib32asound2 (1.0.23-1ubuntu2.1) to 1.0.23-2.1
lib32bz2-1.0 (1.0.5-4ubuntu1) to 1.0.5-6
lib32v4l-0 (0.6.4-1ubuntu1) to 0.8.0-1
libacl1 (2.2.49-3) to 2.2.49-4
liballegro4.2 (2:4.2.2-2.2ubuntu2) to 2:4.2.2-2.2+b1
liballegro4.2-plugin-jack (2:4.2.2-2.2ubuntu2) to 2:4.2.2-2.2+b1
libasound2 (1.0.23-1ubuntu2.1) to 1.0.23-2.1
libasound2-plugins (1.0.23-1ubuntu2) to 1.0.23-1+b1
libaudio2 (1.9.2-3) to 1.9.2-4
libavahi-client3 (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
libavahi-common-data (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
libavahi-common3 (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
libavahi-core7 (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
libavahi-glib1 (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
libavahi-gobject0 (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
libavahi-ui0 (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
libavc1394-0 (0.5.3-1build4) to 0.5.3-1+b2
libbind9-60 (1:9.7.1.dfsg.P2-2ubuntu0.2) to 1:9.7.2.dfsg.P3-1.1
libblas3gf (1.2-7) to 1.2-8
libblkid1 (2.17.2-0ubuntu1.10.10.2) to 2.17.2-9
libboost-python1.42.0 (1.42.0-3ubuntu1) to 1.42.0-4
libbrlapi0.5 (4.2-3ubuntu1) to 4.2-7
libbz2-1.0 (1.0.5-4ubuntu1) to 1.0.5-6
libcap-ng0 (0.6.3-1) to 0.6.4-1
libcap2 (1:2.19-2) to 1:2.19-3
libcdt4 (2.26.3-4) to 2.26.3-5
libclutter-1.0-0 (1.2.12-0ubuntu13) to 1.2.12-3
libcomerr2 (1.41.12-1ubuntu2) to 1.41.12-2
libcups2 (1.4.4-6ubuntu2.3) to 1.4.4-7
libcupscgi1 (1.4.4-6ubuntu2.3) to 1.4.4-7
libcupsdriver1 (1.4.4-6ubuntu2.3) to 1.4.4-7
libcupsimage2 (1.4.4-6ubuntu2.3) to 1.4.4-7
libcupsmime1 (1.4.4-6ubuntu2.3) to 1.4.4-7
libcupsppdc1 (1.4.4-6ubuntu2.3) to 1.4.4-7
libdatrie1 (0.2.3-1) to 0.2.4-1
libdb4.8 (4.8.30-1) to 4.8.30-2
libdbus-glib-1-2 (0.88-2) to 0.88-2.1
libdevmapper1.02.1 (2:1.02.39-1ubuntu6) to 2:1.02.48-5
libdjvulibre-text (3.5.22-9ubuntu1) to 3.5.23-3
libdjvulibre21 (3.5.22-9ubuntu1) to 3.5.23-3
libdv4 (1.0.0-2ubuntu2) to 1.0.0-2.1
libecryptfs0 (83-0ubuntu3) to 83-4
libedit2 (2.11-20080614-1build1) to 2.11-20080614-2
libelf1 (0.147-2) to 0.148-1
libenca0 (1.13-2) to 1.13-3
libept1 (1.0.3) to 1.0.4
libfaad2 (2.7-4) to 2.7-6
libffi5 (3.0.9-2ubuntu2) to 3.0.9-3
libfltk1.1 (1.1.10-2) to 1.1.10-2+b1
libfontconfig1 (2.8.0-2ubuntu1) to 2.8.0-2.1
libfreetype6 (2.4.2-2ubuntu0.1) to 2.4.2-2.1
libfuse2 (2.8.4-1ubuntu1.3) to 2.8.4-1.1
libgadu3 (1:1.9.0-1~pidgin1.10.10) to 1:1.9.0-2
libgail-gnome-module (1.20.2-1) to 1.20.3-1
libgamin0 (0.1.10-1ubuntu3) to 0.1.10-2+b1
libgd2-xpm (2.0.36~rc1~dfsg-3.2ubuntu1) to 2.0.36~rc1~dfsg-5
libgdata1.4-cil (1.4.0.2-3) to 1.4.0.2-4
libgdiplus (2.6.7-2) to 2.6.7-3
libgegl-0.0-0 (0.0.22-2ubuntu2) to 0.0.22-2+b1
libgeoip1 (1.4.7~beta5+dfsg-1) to 1.4.7~beta6+dfsg-1
libgksu2-0 (2.0.13~pre1-1ubuntu5) to 2.0.13~pre1-3
libgnomepanel2.24-cil (2.26.0-3) to 2.26.0-3+b1
libgraph4 (2.26.3-4) to 2.26.3-5
libgssapi-krb5-2 (1.8.1+dfsg-5ubuntu0.7) to 1.8.3+dfsg-4
libgssdp-1.0-2 (0.7.2-2build1) to 0.8.0-2
libgtk-vnc-1.0-0 (0.4.1-3ubuntu2) to 0.4.1-4
libgupnp-1.0-3 (0.13.4-1build1) to 0.14.0-2
libgupnp-igd-1.0-3 (0.1.7-2) to 0.1.7-3
libgutenprint2 (5.2.6-0ubuntu8) to 5.2.6-1
libgvc5 (2.26.3-4) to 2.26.3-5
libgweather-common (2.30.3-0ubuntu1) to 2.30.3-1
libgweather1 (2.30.3-0ubuntu1) to 2.30.3-1
libhal-storage1 (0.5.14-0ubuntu6) to 0.5.14-3
libhal1 (0.5.14-0ubuntu6) to 0.5.14-3
libhpmud0 (3.10.6-1ubuntu10.2) to 3.10.6-2
libhtml-parser-perl (3.65-1) to 3.66-1
libice6 (2:1.0.6-1) to 2:1.0.6-2
libieee1284-3 (0.2.11-5ubuntu3) to 0.2.11-6
libimlib2 (1.4.2-8) to 1.4.2-8+b2
libimobiledevice1 (1.0.1-1) to 1.0.2-1
libiptcdata0 (1.0.4-1) to 1.0.4-1+b1
libisccc60 (1:9.7.1.dfsg.P2-2ubuntu0.2) to 1:9.7.2.dfsg.P3-1.1
libiw30 (30~pre9-3ubuntu4) to 30~pre9-5
libjack-jackd2-0 (1.9.5~dfsg-19ubuntu1) to 1.9.6~dfsg.1-2
libjasper1 (1.900.1-7) to 1.900.1-7+b1
libjpeg62 (6b-16.1) to 6b1-1
libk5crypto3 (1.8.1+dfsg-5ubuntu0.7) to 1.8.3+dfsg-4
libkpathsea5 (2009-7) to 2009-8
libkrb5-3 (1.8.1+dfsg-5ubuntu0.7) to 1.8.3+dfsg-4
libkrb5support0 (1.8.1+dfsg-5ubuntu0.7) to 1.8.3+dfsg-4
liblcms1 (1.18.dfsg-1ubuntu2.10.10.1) to 1.18.dfsg-1.2+b3
libldap-2.4-2 (2.4.23-0ubuntu3.5) to 2.4.23-7
liblwres60 (1:9.7.1.dfsg.P2-2ubuntu0.2) to 1:9.7.2.dfsg.P3-1.1
liblzma2 (4.999.9beta+20100527-1) to 5.0.0-2
libmad0 (0.15.1b-4ubuntu2) to 0.15.1b-5
libmagic1 (5.03-5ubuntu1) to 5.04-5
libmagick++3 (7:6.6.2.6-1ubuntu1.1) to 8:6.6.0.4-3
libmagickcore3 (7:6.6.2.6-1ubuntu1.1) to 8:6.6.0.4-3
libmagickcore3-extra (7:6.6.2.6-1ubuntu1.1) to 8:6.6.0.4-3
libmagickwand3 (7:6.6.2.6-1ubuntu1.1) to 8:6.6.0.4-3
libmimic0 (1.0.4-2build1) to 1.0.4-2+b2
libmng1 (1.0.10-1) to 1.0.10-1+b1
libmono-cairo2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-corlib2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-data-tds2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-getoptions2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-i18n-west2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-management2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-messaging2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-posix2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-security2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-sharpzip2.84-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-sqlite2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-system-data2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-system-messaging2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-system-runtime2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-system-web2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-system2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono-wcf3.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libmono2.0-cil (2.6.7-3ubuntu1) to 2.6.7-5
libneon27-gnutls (0.29.3-2) to 0.29.3-3
libnetpbm10 (2:10.0-12.2) to 2:10.0-12.2+b1
libnl1 (1.1-5build1) to 1.1-6
libnspr4-0d (4.8.6-0ubuntu1) to 4.8.6-1
libnss-mdns (0.10-3ubuntu4) to 0.10-3.1
libntfs10 (2.0.0-1ubuntu4) to 2.0.0-1+b1
libnunit2.4-cil (2.4.7+dfsg-5) to 2.4.7+dfsg-6
liboil0.3 (0.3.16-1ubuntu2) to 0.3.17-2
liborc-0.4-0 (0.4.6-1) to 1:0.4.6-2
libpam-modules (1.1.1-4ubuntu2) to 1.1.1-6.1
libpam-runtime (1.1.1-4ubuntu2) to 1.1.1-6.1
libpam0g (1.1.1-4ubuntu2) to 1.1.1-6.1
libpango1.0-0 (1.28.2-0ubuntu1.1) to 1.28.3-1+squeeze2
libpango1.0-common (1.28.2-0ubuntu1.1) to 1.28.3-1+squeeze2
libparted0debian1 (2.3-2ubuntu2) to 2.3-5
libpathplan4 (2.26.3-4) to 2.26.3-5
libpci3 (1:3.1.7-4ubuntu2) to 1:3.1.7-6
libpcre3 (8.02-1) to 8.02-1.1
libpcsclite1 (1.5.5-3ubuntu2.1) to 1.5.5-4
libperl5.10 (5.10.1-12ubuntu2.1) to 5.10.1-17
libplist1 (1.3-1) to 1.3-2
libpolkit-agent-1-0 (0.96-2ubuntu1.1) to 0.96-4
libpolkit-backend-1-0 (0.96-2ubuntu1.1) to 0.96-4
libpolkit-gobject-1-0 (0.96-2ubuntu1.1) to 0.96-4
libpolkit-gtk-1-0 (0.96-2ubuntu4) to 0.96-3
libprotobuf6 (2.3.0-2ubuntu1) to 2.3.0-4
libprotoc6 (2.3.0-2ubuntu1) to 2.3.0-4
libproxy0 (0.3.1-1ubuntu1) to 0.3.1-2
libpython2.6 (2.6.6-5ubuntu1) to 2.6.6-8+b1
librarian0 (0.8.1-4.1) to 0.8.1-5
librasqal2 (0.9.19-1) to 0.9.20-1
librdf0 (1.0.10-2) to 1.0.10-3
libsane (1.0.21-2ubuntu2) to 1.0.21-9
libsane-hpaio (3.10.6-1ubuntu10.2) to 3.10.6-2
libsasl2-2 (2.1.23.dfsg1-5ubuntu2) to 2.1.23.dfsg1-7
libsasl2-modules (2.1.23.dfsg1-5ubuntu2) to 2.1.23.dfsg1-7
libsdl-image1.2 (1.2.10-2) to 1.2.10-2+b2
libsdl-mixer1.2 (1.2.8-6build1) to 1.2.8-6.3
libsdl1.2debian (1.2.14-6ubuntu3) to 1.2.14-6.1
libsdl1.2debian-pulseaudio (1.2.14-6ubuntu3) to 1.2.14-6.1
libselinux1 (2.0.94-1) to 2.0.96-1
libshout3 (2.2.2-5ubuntu1) to 2.2.2-5+b1
libslp1 (1.2.1-7.7ubuntu0.1) to 1.2.1-7.8
libsmbclient (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.6~dfsg-3squeeze2
libsndfile1 (1.0.21-2) to 1.0.21-3
libsnmp-base (5.4.3~dfsg-1ubuntu3) to 5.4.3~dfsg-2
libsnmp15 (5.4.3~dfsg-1ubuntu3) to 5.4.3~dfsg-2
libspeechd2 (0.7-5ubuntu3) to 0.7-6.1
libsqlite3-0 (3.7.2-1ubuntu0.1) to 3.7.3-1
libss2 (1.41.12-1ubuntu2) to 1.41.12-2
libssl0.9.8 (0.9.8o-1ubuntu4.4) to 0.9.8o-4squeeze1
libtdb1 (1.2.1-2) to 1.2.1-2+b1
libtelepathy-farsight0 (0.0.14-2) to 0.0.14-2+b1
libtiff-tools (3.9.4-2ubuntu0.4) to 3.9.4-5
libtiff4 (3.9.4-2ubuntu0.4) to 3.9.4-5
libtotem-plparser17 (2.30.3-0ubuntu1) to 2.30.3-1
libudev0 (162-2.2) to 164-3
libunique-1.0-0 (1.1.6-1ubuntu3) to 1.1.6-1.1
libupower-glib1 (0.9.5-4) to 0.9.5-5
liburi-perl (1.54-1) to 1.54-2
libusb-0.1-4 (2:0.1.12-15ubuntu2) to 2:0.1.12-16
libuuid1 (2.17.2-0ubuntu1.10.10.2) to 2.17.2-9
libv4l-0 (0.6.4-1ubuntu1) to 0.8.0-1
libvcdinfo0 (0.7.23-4ubuntu2) to 0.7.23-4+b2
libwbclient0 (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.6~dfsg-3squeeze2
libwebkit-1.0-2 (1.2.5-0ubuntu0.10.10.1) to 1.2.6-2
libwebkit-1.0-common (1.2.5-0ubuntu0.10.10.1) to 1.2.6-2
libwnck2.20-cil (2.26.0-3) to 2.26.0-3+b1
libx11-6 (2:1.3.3-3ubuntu1) to 2:1.3.3-4
libx11-data (2:1.3.3-3ubuntu1) to 2:1.3.3-4
libx11-dev (2:1.3.3-3ubuntu1) to 2:1.3.3-4
libx11-xcb1 (2:1.3.3-3ubuntu1) to 2:1.3.3-4
libxdot4 (2.26.3-4) to 2.26.3-5
libxi6 (2:1.3-4) to 2:1.3-6
libxml-parser-perl (2.36-1.1build3) to 2.36-1.1+b1
libxml2 (2.7.7.dfsg-4ubuntu0.1) to 2.7.8.dfsg-2
libxml2-utils (2.7.7.dfsg-4ubuntu0.1) to 2.7.8.dfsg-2
libxmu6 (2:1.0.5-1) to 2:1.0.5-2
libxmuu1 (2:1.0.5-1) to 2:1.0.5-2
libzbar0 (0.10+doc-3build1) to 0.10+doc-4
linux-sound-base (1.0.23+dfsg-1ubuntu4) to 1.0.23+dfsg-2
login (1:4.1.4.2-1ubuntu3.2) to 1:4.1.4.2+svn3283-2+squeeze1
ltrace (0.5.3-2ubuntu6) to 0.5.3-2.1
man-db (2.5.7-4) to 2.5.7-8
manpages (3.24-1ubuntu1) to 3.27-1
manpages-dev (3.24-1ubuntu1) to 3.27-1
memtest86+ (4.10-1ubuntu2) to 4.10-1.1
mobile-broadband-provider-info (20100910-1) to 20101106-1
mono-2.0-gac (2.6.7-3ubuntu1) to 2.6.7-5
mono-csharp-shell (2.6.7-3ubuntu1) to 2.6.7-5
mono-gac (2.6.7-3ubuntu1) to 2.6.7-5
mono-gmcs (2.6.7-3ubuntu1) to 2.6.7-5
mono-runtime (2.6.7-3ubuntu1) to 2.6.7-5
mount (2.17.2-0ubuntu1.10.10.2) to 2.17.2-9
nautilus-share (0.7.2-13.1) to 0.7.2-14
netbase (4.35ubuntu3) to 4.45
netcat-openbsd (1.89-3ubuntu2) to 1.89-4
netpbm (2:10.0-12.2) to 2:10.0-12.2+b1
ntfsprogs (2.0.0-1ubuntu4) to 2.0.0-1+b1
ntpdate (1:4.2.4p8+dfsg-1ubuntu6.1) to 1:4.2.6.p2+dfsg-1+b1
obex-data-server (0.4.5-1build1) to 0.4.5-1+b1
openoffice.org-base-core (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-calc (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-common (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-core (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-draw (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-emailmerge (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-gnome (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-gtk (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-help-en-gb (1:3.2.1-6ubuntu1) to 1:3.2.1-11+squeeze2
openoffice.org-help-en-us (1:3.2.1-6ubuntu1) to 1:3.2.1-11+squeeze2
openoffice.org-impress (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-l10n-en-gb (1:3.2.1-6ubuntu1) to 1:3.2.1-11+squeeze2
openoffice.org-l10n-en-za (1:3.2.1-6ubuntu1) to 1:3.2.1-11+squeeze2
openoffice.org-math (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openoffice.org-writer (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
openssh-client (1:5.5p1-4ubuntu5) to 1:5.5p1-6
openssl (0.9.8o-1ubuntu4.4) to 0.9.8o-4squeeze1
os-prober (1.39) to 1.42
parted (2.3-2ubuntu2) to 2.3-5
passwd (1:4.1.4.2-1ubuntu3.2) to 1:4.1.4.2+svn3283-2+squeeze1
pciutils (1:3.1.7-4ubuntu2) to 1:3.1.7-6
pcmciautils (014-4ubuntu4) to 015-1
perl (5.10.1-12ubuntu2.1) to 5.10.1-17
perl-base (5.10.1-12ubuntu2.1) to 5.10.1-17
perl-modules (5.10.1-12ubuntu2.1) to 5.10.1-17
perlmagick (7:6.6.2.6-1ubuntu1.1) to 8:6.6.0.4-3
phatch (0.2.7-2) to 0.2.7-5
phatch-cli (0.2.7-2) to 0.2.7-5
pkg-config (0.25-1) to 0.25-1.1
plymouth (0.8.2-2ubuntu5.1) to 0.8.3-9.1
policykit-1 (0.96-2ubuntu1.1) to 0.96-4
policykit-1-gnome (0.96-2ubuntu4) to 0.96-3
popularity-contest (1.48ubuntu1) to 1.49
ppp (2.4.5~git20081126t100229-0ubuntu4) to 2.4.5-4
pppconfig (2.3.18ubuntu2) to 2.3.18+nmu2
protobuf-compiler (2.3.0-2ubuntu1) to 2.3.0-4
python (2.6.6-2ubuntu2) to 2.6.6-3+squeeze6
python-apt (0.7.96.1ubuntu11.1) to 0.7.100.1
python-avahi (0.6.27-2ubuntu3.1) to 0.6.27-2+squeeze1
python-brlapi (4.2-3ubuntu1) to 4.2-7
python-cairo (1.8.8-1) to 1.8.8-1+b1
python-central (0.6.15ubuntu2) to 0.6.16+nmu1
python-crypto (2.0.1+dfsg1-4ubuntu2) to 2.1.0-2
python-dbus (0.83.0-1ubuntu3) to 0.83.1-1
python-debian (0.1.16ubuntu1) to 0.1.18
python-gdbm (2.6.6-0ubuntu1) to 2.6.6-1
python-gnomeapplet (2.30.0-1ubuntu5.1) to 2.30.0-4
python-gnomedesktop (2.30.0-1ubuntu5.1) to 2.30.0-4
python-gnomekeyring (2.30.0-1ubuntu5.1) to 2.30.0-4
python-gtkspell (2.25.3-5ubuntu2.1) to 2.25.3-7
python-httplib2 (0.6.0-3build1) to 0.6.0-4
python-launchpadlib (1.6.1-1) to 1.6.2-1
python-lazr.restfulclient (0.9.20-0ubuntu1) to 0.9.21-1
python-libproxy (0.3.1-1ubuntu1) to 0.3.1-2
python-libxml2 (2.7.7.dfsg-4ubuntu0.1) to 2.7.8.dfsg-2
python-lxml (2.2.6-1) to 2.2.8-2
python-mako (0.3.4-2) to 0.3.4-5
python-markupsafe (0.9.2-2build1) to 0.9.2-3
python-minimal (2.6.6-2ubuntu2) to 2.6.6-3+squeeze6
python-notify (0.1.1-2build3) to 0.1.1-2+b2
python-numpy (1:1.3.0-3build1) to 1:1.4.1-5
python-oauth (1.0a~svn1124-0ubuntu2) to 1.0.1-2
python-pam (0.4.2-12.1ubuntu1) to 0.4.2-12.2
python-pkg-resources (0.6.14-3ubuntu1) to 0.6.14-4
python-protobuf (2.3.0-2ubuntu1) to 2.3.0-4
python-pycurl (7.19.0-3) to 7.19.0-3+b1
python-pyexiv2 (0.1.3-6fakesync1) to 0.1.3-6+b4
python-pygoocanvas (0.14.1-1ubuntu2) to 0.14.1-1+b1
python-pyorbit (2.24.0-5ubuntu3) to 2.24.0-6
python-rdflib (2.4.2-1) to 2.4.2-1+b1
python-renderpm (2.4-3) to 2.4-4
python-reportlab (2.4-3) to 2.4-4
python-reportlab-accel (2.4-3) to 2.4-4
python-speechd (0.7-5ubuntu3) to 0.7-6.1
python-support (1.0.9ubuntu1) to 1.0.10
python-tk (2.6.6-0ubuntu1) to 2.6.6-1
python-twisted-bin (10.1.0-2) to 10.1.0-3
python-twisted-core (10.1.0-2) to 10.1.0-3
python-uniconvertor (1.1.4-1build1) to 1.1.4-1+b1
python-uno (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
python-wnck (2.30.0-1ubuntu5.1) to 2.30.0-4
python-xapian (1.0.20-1) to 1.2.3-3
python2.6 (2.6.6-5ubuntu1) to 2.6.6-8+b1
python2.6-minimal (2.6.6-5ubuntu1) to 2.6.6-8+b1
rarian-compat (0.8.1-4.1) to 0.8.1-5
rsyslog (4.2.0-2ubuntu8) to 4.6.4-2
samba-common (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.6~dfsg-3squeeze2
samba-common-bin (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.6~dfsg-3squeeze2
sane-utils (1.0.21-2ubuntu2) to 1.0.21-9
sgml-base (1.26) to 1.26+nmu1
shared-mime-info (0.71-3) to 0.71-4
smbclient (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.6~dfsg-3squeeze2
speech-dispatcher (0.7-5ubuntu3) to 0.7-6.1
ssh-askpass-gnome (1:5.5p1-4ubuntu5) to 1:5.5p1-6
ssl-cert (1.0.26) to 1.0.28
sudo (1.7.2p7-1ubuntu2.1) to 1.7.4p4-2.squeeze.2
synaptic (0.63.1ubuntu14) to 0.70~pre1+b1
syslinux (2:4.01+dfsg-3ubuntu1) to 2:4.02+dfsg-7
syslinux-common (2:4.01+dfsg-3ubuntu1) to 2:4.02+dfsg-7
system-tools-backends (2.10.1-0ubuntu1) to 2.10.1-2
sysv-rc (2.87dsf-4ubuntu19.1) to 2.88dsf-13.1
sysvinit-utils (2.87dsf-4ubuntu19.1) to 2.88dsf-13.1
tar (1.23-2ubuntu2) to 1.23-3
time (1.7-23ubuntu1) to 1.7-23.1
ttf-lao (0.0.20060226-6) to 0.0.20060226-7
ttf-liberation (1.05.2.20091019-4) to 1.05.2.20091019-4squeeze1
ttf-opensymbol (1:3.2.1-7ubuntu1.1) to 1:3.2.1-11+squeeze2
ttf-punjabi-fonts (1:0.5.10ubuntu1) to 1:0.5.11
ubuntu-sso-client (1.0.8-0ubuntu1) to 1.0.9-0ubuntu1
ubuntu-tweak (0.5.12-1~maverick1) to 0.5.13-1~maverick1
ucf (3.0025) to 3.0025+nmu1
udev (162-2.2) to 164-3
unattended-upgrades (0.62ubuntu1) to 0.62.2
uno-libs3 (1.6.1+OOo3.2.1-7ubuntu1.1) to 1.6.1+OOo3.2.1-11+squeeze2
update-inetd (4.36ubuntu0.1) to 4.38+nmu1
upower (0.9.5-4) to 0.9.5-5
ure (1.6.1+OOo3.2.1-7ubuntu1.1) to 1.6.1+OOo3.2.1-11+squeeze2
usb-modeswitch (1.1.4-1) to 1.1.4-2
usb-modeswitch-data (20100826-1) to 20100826-1+squeeze0
usbutils (0.87-4) to 0.87-5
util-linux (2.17.2-0ubuntu1.10.10.2) to 2.17.2-9
uuid-runtime (2.17.2-0ubuntu1.10.10.2) to 2.17.2-9
vim-common (2:7.2.330-1ubuntu4) to 2:7.2.445+hg~cb94c42c0e1a-1
vim-tiny (2:7.2.330-1ubuntu4) to 2:7.2.445+hg~cb94c42c0e1a-1
vinagre (2.30.2-1ubuntu1) to 2.30.3-1
w3m (0.5.2-6ubuntu1) to 0.5.2-9
wget (1.12-1.1ubuntu3) to 1.12-2.1
whois (5.0.7ubuntu1) to 5.0.10
wireless-tools (30~pre9-3ubuntu4) to 30~pre9-5
wodim (9:1.1.10-1ubuntu3) to 9:1.1.11-1
wpasupplicant (0.6.10-2) to 0.6.10-2.1
x11-common (1:7.5+6ubuntu3) to 1:7.5+8
xdg-user-dirs (0.12-1ubuntu1) to 0.13-2
xdg-utils (1.0.2+cvs20100307-1ubuntu0.3) to 1.0.2+cvs20100307-2
xkb-data (1.8-1ubuntu8.1~10.10.1) to 1.8-2
xorg (1:7.5+6ubuntu3) to 1:7.5+8
xscreensaver-data (5.11-1ubuntu2) to 5.11-1+b1
xscreensaver-gl (5.11-1ubuntu2) to 5.11-1+b1
xserver-xorg (1:7.5+6ubuntu3) to 1:7.5+8
xserver-xorg-input-all (1:7.5+6ubuntu3) to 1:7.5+8
xserver-xorg-video-all (1:7.5+6ubuntu3) to 1:7.5+8
xz-utils (4.999.9beta+20100527-1) to 5.0.0-2
yelp (2.30.1-0ubuntu1) to 2.30.1+webkit-1

Installed the following packages:
acpi-fakekey (0.137-5)
acpi-support-base (0.137-5)
bsd-mailx (8.1.2-0.20100314cvs-1)
debian-archive-keyring (2010.08.28)
exim4 (4.72-6)
exim4-base (4.72-6)
exim4-config (4.72-6)
exim4-daemon-light (4.72-6)
gcj-4.4-base (4.4.5-2)
gcj-4.4-jre-lib (4.4.5-2)
gnupg-curl (1.4.10-4)
isc-dhcp-client (4.1.1-P1-15+squeeze1)
isc-dhcp-common (4.1.1-P1-15+squeeze1)
keyboard-configuration (1.68+squeeze2)
libcommons-beanutils-java (1.8.3-1)
libcommons-collections3-java (3.2.1-4)
libcommons-compress-java (1.0-1)
libcommons-digester-java (1.8.1-2)
libcommons-logging-java (1.1.1-8)
libdb-je-java (3.3.62-3)
libdb4.7 (4.7.25-9)
libdb4.7-java (4.7.25-9)
libdb4.7-java-gcj (4.7.25-9)
libdns69 (1:9.7.2.dfsg.P3-1.1)
libelfg0 (0.8.13-1)
libexiv2-9 (0.20-2)
libgcj-bc (4.4.5-1)
libgcj-common (1:4.4.5-1)
libgcj10 (4.4.5-2)
libgtkimageview0 (1.6.4-1)
libicu44 (4.4.1-7)
libicu4j-java (4.0.1.1-1)
libisc62 (1:9.7.2.dfsg.P3-1.1)
libisccfg62 (1:9.7.2.dfsg.P3-1.1)
libjaxp1.3-java (1.3.05-1)
libjline-java (0.9.94-5)
libjtidy-java (7+svn20070309-4)
liblucene2-java (2.9.2+ds1-1)
libmono-system-data-linq2.0-cil (2.6.7-5)
libmythes-1.2-0 (2:1.2.1-1)
libnfnetlink0 (1.0.0-1)
libopenjpeg2 (1.3+dfsg-4)
libopenraw1 (0.0.8-2)
libpoppler5 (0.12.4-1.2)
libregexp-java (1.5-2)
libsane-extras (1.0.21.2)
libsvga1 (1:1.4.3-29)
libtextcat-data-utf8 (2.2-4)
libxapian22 (1.2.3-2)
openoffice.org-filter-binfilter (1:3.2.1-11+squeeze2)
openoffice.org-java-common (1:3.2.1-11+squeeze2)
openoffice.org-style-tango (1:3.2.1-11+squeeze2)
openssh-blacklist (0.4.1)
openssh-blacklist-extra (0.4.1)
plymouth-themes-all (0.8.3-9.1)
plymouth-themes-fade-in (0.8.3-9.1)
plymouth-themes-glow (0.8.3-9.1)
plymouth-themes-script (0.8.3-9.1)
plymouth-themes-solar (0.8.3-9.1)
plymouth-themes-spinfinity (0.8.3-9.1)
python-apt-common (0.7.100.1)
python-chardet (2.0.1-1)
ttf-dejavu (2.31-1)
ufraw-batch (0.16-3+b1)
xserver-xorg-video-glint (1:1.2.4-2build2)
xserver-xorg-video-i740 (1:1.3.2-2build1)
xserver-xorg-video-qxl (0.0.12-1ubuntu1)

Several issues I've also found in recovery mode:
-I cannot go into 'Additional drivers' (Cannot connect to D-BUS. org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory)
-Cannot shut down/restart. No options appeared when clicking in the 'shut down' icon. Options in gray when Ctrl+Alt+Del

I don't know which log file could you need to see, and how to find them. I am rather new in here.

Thanks in advance.

---


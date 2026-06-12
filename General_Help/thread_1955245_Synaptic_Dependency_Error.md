---
title: "Synaptic Dependency Error"
date: 2012-04-09
forum: General Help
---

### Post by ItsAllLinux on 2012-04-09
Hi,

Every time i install/remove something via Synaptic, I always get this error

E: foomatic-filters: subprocess installed post-installation script returned error exit status 10
E: rsyslog: subprocess installed post-installation script returned error exit status 10
E: foo2zjs: dependency problems - leaving unconfigured
E: samba-common: subprocess installed post-installation script returned error exit status 10
E: samba-common-bin: dependency problems - leaving unconfigured
E: smbclient: dependency problems - leaving unconfigured

The following is what I get from executing the following command:
sudo dpkg --configure -a> 
dpkg: error: dpkg status database is locked by another process
ming@ming-desktop:~$ sudo dpkg --configure -a
Setting up samba-common (2:3.5.8~dfsg-1ubuntu2.3) ...
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.5.8~dfsg-1ubuntu2.3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up foomatic-filters (4.0.7-0ubuntu1.1) ...
dpkg: error processing foomatic-filters (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (4.6.4-2ubuntu4.2) ...
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of foo2zjs:
 foo2zjs depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foo2zjs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 smbclient
 foomatic-filters
 samba-common-bin
 rsyslog
 foo2zjs
If you happen to know what this error really mean and how I can fix it (if it is necessary + easy to do so) please let me know!

Thanks in advance!

FYI:

My problem was actually to get MusicBrainz Picard installed on my Ubuntu Natty but after several reinstallations, the programme fails to start up. I am wondering whether the error I get from Synaptic is an explanation to this.

The following is the error I get from installing Picard from the Software Centre

```

installArchives() failed: Selecting previously deselected package libdiscid0. 
(Reading database ...  
dpkg: warning: files list file for package `libio-string-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxau6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblaunchpad-integration1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblockfile1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lsof' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-media0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwrap0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `protobuf-compiler' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-twisted-names' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnfnetlink0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `upower' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `policykit-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcap2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `linux-sound-base' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `readline-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxt6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtext-charwidth-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-tseng' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `wodim' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgomp1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnet-dbus-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-configglue' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglib2.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgphoto2-port0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libraptor1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-lazr.restfulclient' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gconf' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-corlib2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-siliconmotion' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-bluetooth8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xorg-docs-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-debian' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `vim-tiny' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `strace' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libhtml-tagset-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmpfr4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-system2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtelepathy-farsight0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libprotoc6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `zip' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-i740' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `x11-xfs-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpcsclite1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libvisual-0.4-plugins' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libevolution' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libstdc++6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `network-manager-gnome' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `powermgmt-base' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglew1.5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfontenc1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `popularity-contest' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-minimal' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-mag2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmeanwhile1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xfonts-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libindicator3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcursor1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `speech-dispatcher' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblouis-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `util-linux' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `make' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmetacity-private0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxml-twig-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgee2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxklavier16' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpixman-1-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdjvulibre21' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `udev' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-geode' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdee-1.0-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-sharpzip2.84-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `tcl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnm-glib-vpn1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `zeitgeist-datahub' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libstlport4.6ldbl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `onboard' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglib2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `notify-osd' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsm6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglewmx1.5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtalloc2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-piston-mini-client' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libiw30' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-openssl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `vbetool' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-khmeros-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `openssh-client' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `totem-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libopenobex1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libselinux1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `time' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libx11-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libntfs-3g79' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnih-dbus1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libspectre1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb-shape0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libzephyr4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libparse-debianchangelog-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libvte9' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libice6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-input-mouse' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libemail-valid-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libipc-run-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libindicate5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `nano' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgkeyfile1.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-security2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcdparanoia0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwpg-0.2-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxtst6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libedit2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-oauth' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `network-manager-pptp-gnome' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-keyring0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-system-service' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-vfs2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xml-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-pygoocanvas' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `zenity' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mime-support' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgdata1.7-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgupnp-1.0-3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `librasqal2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `linux-firmware' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtksourceview2.0-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libexiv2-10' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwnck22' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lp-solve' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpciaccess0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-mono' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `unzip' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-imaging' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libutouch-grail1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgphoto2-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-notify' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwnck-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsub-name-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libx11-xcb1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xscreensaver-gl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsdl1.2debian-pulseaudio' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libio-pty-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libjbig2dec0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `telepathy-salut' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtag1c2a' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgucharmap7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblua5.1-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-markupsafe' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmythes-1.2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `wireless-tools' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libzeitgeist-1.0-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdrm-intel1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtaglib2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-rdflib' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-virtkey' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-wadllib' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libhtml-parser-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `network-manager' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnautilus-extension1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcaca0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnm-glib2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpolkit-gtk-1-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libhyphen0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-mach64' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `rarian-compat' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcairo-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libboost-serialization1.42.0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libedata-book1.2-8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdotconf1.0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-pyatspi' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgsl0ldbl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libunity-misc0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-i18n-west2.0-cil' missing, assuming package has no files currently installed. 
 (Reading database ... 5% 
dpkg: warning: files list file for package `libvisual-0.4-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-chips' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwmf0.2-7-gtk' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-trident' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxp6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-dejavu-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-cairo2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblcms1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-s3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-crypto' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-xdg' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglade2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtextcat-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmtdev1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `totem-plugins' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfile-copy-recursive-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcap-ng0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `min12xxw' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libedataserverui1.2-11' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `usb-modeswitch-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-telepathy' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gst0.10' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-twisted-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `yelp-xsl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcanberra-gtk0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xbitmaps' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-xapian' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-keyring' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblocale-gettext-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-simplejson' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libncursesw5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `x-ttcidfont-conf' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pkg-config' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libept1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpcre3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-chardet' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-pyinotify' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgail-gnome-module' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwww-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomeui-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `syslinux' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-i128' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libbrasero-media1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `notify-osd-icons' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgpm2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-mga' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xsltproc' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfile-desktopentry-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libplist1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnss-mdns' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcroco3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtkhtml3.14-19' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglibmm-2.4-1c2a' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libubuntuone1.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnih1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblzma2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglib2.0-bin' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-central' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `nautilus' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpolkit-backend-1-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-zeroconf1.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libjack-jackd2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsigc++-2.0-0c2a' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `tsclient' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpaper1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libido-0.1-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpangomm-1.4-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgmime-2.4-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-argparse' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `media-player-info' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcanberra0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsensors4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libx11-6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xfonts-encodings' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomevfs2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-wsgi-intercept' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liboobs-1-5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-nouveau' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgail-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xz-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomecanvas2-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxft2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libbsd0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtksourceview2.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libunique-1.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libss2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xinput' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `linux-image-2.6.38-8-generic' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liborbit2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgeoclue0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdatrie1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pnm2ppa' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libslang2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libisofs6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ufw' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libebackend1.2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdjvulibre-text' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xauth' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xdg-user-dirs' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gtksourceview2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `sessioninstaller' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libstartup-notification0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gnomekeyring' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-farsight' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xkb-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-webkit' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libiec61883-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `passwd' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsasl2-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsasl2-modules' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `obexd-client' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomekbd-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpipeline1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `wbritish' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcamel1.2-19' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgadu3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ureadahead' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mlocate' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `sgml-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-neomagic' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `telepathy-idle' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `upstart' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libijs-0.35' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxaw7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `x11-xserver-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome2.24-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxdamage1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `toshset' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-cups' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `yelp' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libhpmud0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libx86-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfolks22' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgs9-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxmu6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mono-gmcs' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `linux-headers-2.6.38-8-generic' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfs6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libntfs10' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `unattended-upgrades' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xdg-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `myspell-en-za' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcanberra-pulse' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblouis2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-r128' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgutenprint2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-addins0.2-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libndesk-dbus-glib1.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxfixes3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `net-tools' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgail18' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `x11-apps' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `rtkit' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdb4.8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcryptui0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ltrace' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnewt0.52' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libubuntuone-1.0-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-cirrus' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpst4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libbrlapi0.5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsilcclient-1.1-3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtk2-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-ark' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-speechd' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-sounds' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mawk' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-serial' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcomerr2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpaper-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-wallpapers' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcrypt-passwdmd5-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgexiv2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `transmission-gtk' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `uuid-runtime' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `x11-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libutouch-geis1' missing, assuming package has no files currently installed. 
 (Reading database ... 10% 
dpkg: warning: files list file for package `libgtkhtml-editor0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `wget' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcdio-paranoia0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-louis' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgmime2.4-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-wqy-microhei' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgs9' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lintian' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsilc-1.1-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `radeontool' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-unfonts-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdevmapper-event1.02.1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xfonts-scalable' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-smbc' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-menu2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libquvi0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `splix' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libopencc1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libhunspell-1.2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-vte' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libshout3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libvte-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lshw' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-punjabi-fonts' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ntfsprogs' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-tdfx' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtk2.0-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libupower-glib1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb-render0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `tcpdump' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python2.7-minimal' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtheora0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libidn11' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `sed' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsnmp15' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libspeexdsp1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libhtml-tree-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpcap0.8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmpc2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdaemon0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-sisusb' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xfonts-base' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblvm2app2.2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xinit' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxi6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-freefont' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdevmapper1.02.1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `usbutils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcairomm-1.0-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libevent-1.4-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-pyorbit' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpango1.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `patch' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libportaudio2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libterm-readkey-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `synaptic' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtk-sharp-beans-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libproxy0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-artwork' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-kacst-one' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgudev1.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `simple-scan' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-rendition' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome2-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblaunchpad-integration1.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb-atom1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtextcat0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-keyring' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnet-dns-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `librarian0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libexpat1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libltdl7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libedata-cal1.2-10' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `telepathy-haze' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `parted' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libkeyutils1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb-aux0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-cairo' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ppp' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnspr4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglib-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lockfile-progs' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb-dri2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `rsync' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `system-tools-backends' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libncurses5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-appindicator' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfreezethaw-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libreadline6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-vesa' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-management2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pm-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-pycurl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gmenu' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnice10' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgdata-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libuuid-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtext-iconv-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsqlite3-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmission-control-plugins0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcairo-gobject2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcdio10' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwps-0.2-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pcmciautils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mount' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libspeechd2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libieee1284-3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgpgme11' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcdio-cdda0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-lao' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgirepository-1.0-1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `totem-mozilla' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libneon27-gnutls' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwmf0.2-7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdv4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxv1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `metacity-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libidl0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb-event1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libklibc' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-addins-gui0.2-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mousetweaks' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcomposite1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libck-connector0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgcc1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pppconfig' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-indic-fonts-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `policykit-1-gnome' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `manpages' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `network-manager-pptp' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libutouch-frame1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python2.7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmldbm-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfolks-telepathy22' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `locales' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `linux-headers-2.6.38-8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-support' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgconf2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libedataserver1.2-14' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-lazr.uri' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `telepathy-butterfly' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxrandr2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libburn4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-xkit' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gnomecanvas' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libunity4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libespeak1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libindicate-gtk2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcloog-ppl0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `zlib1g' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfribidi0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwebkitgtk-1.0-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `netcat-openbsd' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `librpc-xml-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `nautilus-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `zeitgeist-extension-fts' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtkhtml-editor-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `vinagre' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfont-afm-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `totem' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdrm-radeon1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnet-domain-tld-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnl1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liburi-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gdbm' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-liberation' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `tar' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-protobuf' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtdb1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-pexpect' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxpm4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-takao-pgothic' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libthai-data' missing, assuming package has no files currently installed. 
 (Reading database ... 15% 
dpkg: warning: files list file for package `libppl-c2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsnmp-base' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfile-mimeinfo-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomevfs2-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-input-evdev' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtag1-vanilla' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpolkit-agent-1-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libslp1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtk2.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgstreamer-plugins-base0.10-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxvmc1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-ubuntu-font-family' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `usb-modeswitch' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libthai0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libecal1.2-8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `zeitgeist' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libenchant1c2a' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgoocanvas-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-fbdev' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-savage' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-qxl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtop2-7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `transmission-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libkpathsea5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mountall' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxrender1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsgutils2-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcolamd2.7.1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `x11-session-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libogg0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `myspell-en-gb' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xterm' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libusb-1.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgconf2-4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxext6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglade2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxxf86dga1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `syslinux-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-window-settings1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-input-wacom' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfontconfig1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `obex-data-server' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libudev0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomecanvas2-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-vmware' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgdu-gtk0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libelfg0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtkmm-2.4-1c2a' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwpd-0.9-9' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsepol1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ntfs-3g' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-openchrome' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `whiptail' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtotem-plparser17' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdrm-nouveau1a' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-indicate' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdrm2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmagic1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `netbase' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdigest-sha1-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgupnp-igd-1.0-3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgdata11' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `librdf0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mtr-tiny' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomeui-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pxljr' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mtools' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `telepathy-gabble' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `unity-asset-pool' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-launchpad-integration' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxres1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-standard' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `manpages-dev' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdbus-glib-1-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libunistring0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `rfkill' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pciutils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-brlapi' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdigest-hmac-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxslt1.1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `sgml-base' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `policykit-desktop-privileges' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libdconf0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libegroupwise1.2-13' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmtp8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `telepathy-mission-control-5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libutouch-evemu1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libndesk-dbus1.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `zeitgeist-core' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtimedate-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libutempter0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-egenix-mxdatetime' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtelepathy-glib0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ncurses-bin' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libical0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnet-ip-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgdk-pixbuf2.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libglib2.0-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `modemmanager' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ttf-thai-tlwg' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwavpack1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-egenix-mxtools' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `vim-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgladeui-1-11' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnotify4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnm-util1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnotify1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcanberra-gtk-module' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-s3virge' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsamplerate0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxml-xpath-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgudev-1.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xdg-user-dirs-gtk' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `update-inetd' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-twisted-web' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lsb-release' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxkbfile1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfile-basedir-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxss1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libmono-posix2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `liblaunchpad-integration-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-voodoo' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtk-vnc-1.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-defer' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-mako' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxapian22' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `sensible-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mono-gac' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `seahorse' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-apm' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ucf' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `psmisc' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpython2.7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libusb-0.1-4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libebook1.2-10' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpci3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libnotify0.4-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libstdc++6-4.5-dev' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpopt0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `wamerican' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ncurses-base' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-zope.interface' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `ubuntu-extras-keyring' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `nautilus-share' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libv4l-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libfuse2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-ibus' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mscompress' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libspeex1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgeoip1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `wpasupplicant' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libppl7' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnome-desktop-2-17' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-libproxy' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `metacity' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libjpeg62' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libparted0debian1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lsb-base' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtasn1-3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgd2-xpm' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtk2.0-cil' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtop2-common' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libuuid1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `screensaver-default-images' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `lzma' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxinerama1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsdl1.2debian' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-wnck' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libwebkitgtk-1.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-video-sis' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-dbus' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xcursor-themes' missing, assuming package has no files currently installed. 
 (Reading database ... 20% 
dpkg: warning: files list file for package `libjs-jquery' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtie-ixhash-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libexif12' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libhtml-format-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libibus2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgstfarsight0.10-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `myspell-en-au' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `man-db' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libffi5' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgraphite3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgamin0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgmp3c2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xscreensaver-data' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `login' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgoocanvas3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `telnet' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `x11-xkb-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `wireless-crda' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `makedev' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libprotobuf6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-twisted-bin' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gtkspell' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxmuu1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libclass-accessor-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxml-parser-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xfonts-mathml' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsysfs2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mono-csharp-shell' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsane' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libsane-hpaio' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `shared-mime-info' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libraw1394-11' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpolkit-gobject-1-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mono-runtime' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-gnome2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `memtest86+' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libelf1' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgnomekbd4' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libpth20' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `mono-2.0-gac' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `pitivi' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libjson-glib-1.0-0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgssdp-1.0-2' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgmpxx4ldbl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `sane-utils' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `tcpd' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `python-pkg-resources' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libgtkspell0' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `libexempi3' missing, assuming package has no files currently installed. 
 
dpkg: warning: files list file for package `xserver-xorg-input-vmmouse' missing, assuming package has no files currently installed. 
 (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 102282 files and directories currently installed.) 
Unpacking libdiscid0 (from .../libdiscid0_0.2.2-1_i386.deb) ... 
Selecting previously deselected package mysql-common. 
Unpacking mysql-common (from .../mysql-common_5.1.61-0ubuntu0.11.04.1_all.deb) ... 
Selecting previously deselected package libmysqlclient16. 
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.61-0ubuntu0.11.04.1_i386.deb) ... 
Selecting previously deselected package libphonon4. 
Unpacking libphonon4 (from .../libphonon4_4%3a4.7.0really4.5.0-0ubuntu3_i386.deb) ... 
Selecting previously deselected package libqt4-network. 
Unpacking libqt4-network (from .../libqt4-network_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-script. 
Unpacking libqt4-script (from .../libqt4-script_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-sql. 
Unpacking libqt4-sql (from .../libqt4-sql_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-xmlpatterns. 
Unpacking libqt4-xmlpatterns (from .../libqt4-xmlpatterns_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-declarative. 
Unpacking libqt4-declarative (from .../libqt4-declarative_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-designer. 
Unpacking libqt4-designer (from .../libqt4-designer_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-help. 
Unpacking libqt4-help (from .../libqt4-help_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-opengl. 
Unpacking libqt4-opengl (from .../libqt4-opengl_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-scripttools. 
Unpacking libqt4-scripttools (from .../libqt4-scripttools_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-sql-mysql. 
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-svg. 
Unpacking libqt4-svg (from .../libqt4-svg_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqt4-test. 
Unpacking libqt4-test (from .../libqt4-test_4%3a4.7.2-0ubuntu6.3_i386.deb) ... 
Selecting previously deselected package libqtassistantclient4. 
Unpacking libqtassistantclient4 (from .../libqtassistantclient4_4.6.3-3_i386.deb) ... 
Selecting previously deselected package phonon-backend-gstreamer. 
Unpacking phonon-backend-gstreamer (from .../phonon-backend-gstreamer_4%3a4.7.0really4.5.0-0ubuntu2.1_i386.deb) ... 
Selecting previously deselected package phonon. 
Unpacking phonon (from .../phonon_4%3a4.7.0really4.5.0-0ubuntu3_all.deb) ... 
Selecting previously deselected package libqtwebkit4. 
Unpacking libqtwebkit4 (from .../libqtwebkit4_2.1~really2.0.2-0ubuntu1_i386.deb) ... 
Selecting previously deselected package python-qt4. 
Unpacking python-qt4 (from .../python-qt4_4.8.3-2_i386.deb) ... 
Selecting previously deselected package python-mutagen. 
Unpacking python-mutagen (from .../python-mutagen_1.19-2build1_all.deb) ... 
Selecting previously deselected package picard. 
Unpacking picard (from .../picard_0.16+bzr1217~ppa6~natty1_i386.deb) ... 
Selecting previously deselected package picard-plugins. 
Unpacking picard-plugins (from .../picard-plugins_0.16+bzr1217~ppa6~natty1_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Processing triggers for hicolor-icon-theme ... 
Setting up foomatic-filters (4.0.7-0ubuntu1.1) ... 
dpkg: error processing foomatic-filters (--configure): 
 subprocess installed post-installation script returned error exit status 10 
No apport report written because MaxReports is reached already
Setting up rsyslog (4.6.4-2ubuntu4.2) ... 
dpkg: error processing rsyslog (--configure): 
 subprocess installed post-installation script returned error exit status 10 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of foo2zjs: 
 foo2zjs depends on foomatic-filters; however: 
  Package foomatic-filters is not configured yet. 
dpkg: error processing foo2zjs (--configure): 
 dependency problems - leaving unconfigured 
Setting up samba-common (2:3.5.8~dfsg-1ubuntu2.3) ... 
No apport report written because MaxReports is reached already
dpkg: error processing samba-common (--configure): 
 subprocess installed post-installation script returned error exit status 10 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of samba-common-bin: 
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however: 
  Package samba-common is not configured yet. 
dpkg: error processing samba-common-bin (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of smbclient: 
 smbclient depends on samba-common (= 2:3.5.8~dfsg-1ubuntu2.3); however: 
  Package samba-common is not configured yet. 
dpkg: error processing smbclient (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Setting up libdiscid0 (0.2.2-1) ... 
Setting up mysql-common (5.1.61-0ubuntu0.11.04.1) ... 
Setting up libmysqlclient16 (5.1.61-0ubuntu0.11.04.1) ... 
Setting up libphonon4 (4:4.7.0really4.5.0-0ubuntu3) ... 
Setting up libqt4-network (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-script (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-sql (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-xmlpatterns (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-declarative (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-designer (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-help (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-opengl (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-scripttools (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-sql-mysql (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-svg (4:4.7.2-0ubuntu6.3) ... 
Setting up libqt4-test (4:4.7.2-0ubuntu6.3) ... 
Setting up libqtassistantclient4 (4.6.3-3) ... 
Setting up phonon-backend-gstreamer (4:4.7.0really4.5.0-0ubuntu2.1) ... 
Setting up phonon (4:4.7.0really4.5.0-0ubuntu3) ... 
Setting up libqtwebkit4 (2.1~really2.0.2-0ubuntu1) ... 
Setting up python-qt4 (4.8.3-2) ... 
Setting up python-mutagen (1.19-2build1) ... 
Setting up picard (0.16+bzr1217~ppa6~natty1) ... 
Processing triggers for python-central ... 
Setting up picard-plugins (0.16+bzr1217~ppa6~natty1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for python-support ... 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 foomatic-filters 
 rsyslog 
 foo2zjs 
 samba-common 
 samba-common-bin 
 smbclient 
Setting up samba-common (2:3.5.8~dfsg-1ubuntu2.3) ... 
dpkg: error processing samba-common (--configure): 
 subprocess installed post-installation script returned error exit status 10 
dpkg: dependency problems prevent configuration of smbclient: 
 smbclient depends on samba-common (= 2:3.5.8~dfsg-1ubuntu2.3); however: 
  Package samba-common is not configured yet. 
dpkg: error processing smbclient (--configure): 
 dependency problems - leaving unconfigured 
Setting up foomatic-filters (4.0.7-0ubuntu1.1) ... 
dpkg: error processing foomatic-filters (--configure): 
 subprocess installed post-installation script returned error exit status 10 
dpkg: dependency problems prevent configuration of samba-common-bin: 
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however: 
  Package samba-common is not configured yet. 
dpkg: error processing samba-common-bin (--configure): 
 dependency problems - leaving unconfigured 
Setting up rsyslog (4.6.4-2ubuntu4.2) ... 
dpkg: error processing rsyslog (--configure): 
 subprocess installed post-installation script returned error exit status 10 
dpkg: dependency problems prevent configuration of foo2zjs: 
 foo2zjs depends on foomatic-filters; however: 
  Package foomatic-filters is not configured yet. 
dpkg: error processing foo2zjs (--configure): 
 dependency problems - leaving unconfigured 

```Thankyou

---

### Post by westie457 on 2012-04-09
Hi try these commands in thus order```
sudo apt-get install -f

sudo apt-get update

sudo apt-get upgrade
```

Post any errors you get.

This should sort the dependency errors and refresh your package list and finally update to the newest versions in the repositories.
You might have to re-install the apps you were trying to install.

---

### Post by ItsAllLinux on 2012-04-09
Thanks for your reply. This is what I get from the commands:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up foomatic-filters (4.0.7-0ubuntu1.1) ...
dpkg: error processing foomatic-filters (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up rsyslog (4.6.4-2ubuntu4.2) ...
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of foo2zjs:
 foo2zjs depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foo2zjs (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.5.8~dfsg-1ubuntu2.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.5.8~dfsg-1ubuntu2.3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 foomatic-filters
 rsyslog
 foo2zjs
 samba-common
 samba-common-bin
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by ItsAllLinux on 2012-04-09
If you recognise this type of error, any help will be appreciated.

---


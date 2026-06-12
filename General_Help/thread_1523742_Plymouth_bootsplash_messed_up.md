---
title: "Plymouth bootsplash messed up"
date: 2010-07-04
forum: General Help
---

### Post by darkforester67 on 2010-07-04
Hey guys iv had this probleam for awhile when i tried to fix my 800x600 plymouth bootsplash when i did it came like when you go on a channel without a signal with all thoso dots and stuff i don't know how im gonna fix it...and can you remove the plymouth and use xsplash instead? i really want to use my own theme :S 

Note: Im using nvidia drivers

---

### Post by Claus7 on 2010-07-04
Hello,

at least for fixing things, this:
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

is supposed to do the trick. In my case I used much less things than expressed there, yet I cannot find the link. The general idea is the same though...

Regards!

---

### Post by philinux on 2010-07-04
> **darkforester67 said:**
> Hey guys iv had this probleam for awhile when i tried to fix my 800x600 plymouth bootsplash when i did it came like when you go on a channel without a signal with all thoso dots and stuff i don't know how im gonna fix it...and can you remove the plymouth and use xsplash instead? i really want to use my own theme :S 

Note: Im using nvidia drivers

See the General Help forum sticky.

---

### Post by darkforester67 on 2010-07-04
Can you still remove plymouth :D?

---

### Post by philinux on 2010-07-04
> **darkforester67 said:**
> Can you still remove plymouth :D?

No as it's used to manage fsck and other things and it's integral to the system. If you try to remove plymouth it will want to remove half your installation. Result = totally borked.

See this.
```
apt-get purge plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-4-generic fakeroot libxcb-dri2-0 linux-headers-2.6.35-4 linux-headers-2.6.35-5
  openoffice.org-l10n-en-gb libx11-xcb1 libexiv2-6 libappindicator0.1-cil grub-pc linux-headers-2.6.35-5-generic
  libsyncdaemon-1.0-1 os-prober exiv2 patch grub-common libvala0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  acpi-support* acpid* aisleriot* alsa-base* alsa-utils* anacron* apparmor* apparmor-utils* apport* apport-gtk* aptdaemon*
  apturl* at* at-spi* avahi-daemon* avahi-utils* baobab* bluez* bluez-cups* brasero* brasero-common* brltty* brltty-x11*
  byobu* capplets-data* checkbox* checkbox-gtk* compiz* compiz-core* compiz-fusion-plugins-extra*
  compiz-fusion-plugins-main* compiz-gnome* compiz-plugins* compizconfig-backend-gconf* compizconfig-settings-manager*
  computer-janitor-gtk* console-setup* consolekit* couchdb-bin* cron* cups* cups-driver-gutenprint* dbus* dbus-x11*
  desktopcouch* dkms* dmsetup* e2fsprogs* empathy* eog* erlang-base* erlang-crypto* erlang-inets* erlang-mnesia*
  erlang-public-key* erlang-runtime-tools* erlang-ssl* erlang-syntax-tools* erlang-xmerl* evince* evolution*
  evolution-couchdb* evolution-data-server* evolution-exchange* evolution-indicator* evolution-plugins* evolution-webcal*
  f-spot* file-roller* firefox* firefox-branding* firefox-gnome-support* flashplugin-installer* foo2zjs* foomatic-db*
  foomatic-db-engine* friendly-recovery* ftp* gbrainy* gcalctool* gconf-defaults-service* gconf-editor* gconf2*
  gconf2-common* gdebi* gdm* gdm-guest-session* gedit* ghostscript-cups* ghostscript-x* gksu* gnome-about* gnome-applets*
  gnome-applets-data* gnome-bluetooth* gnome-codec-install* gnome-control-center* gnome-dictionary* gnome-disk-utility*
  gnome-games-common* gnome-keyring* gnome-mag* gnome-mahjongg* gnome-media* gnome-media-common* gnome-nettool* gnome-orca*
  gnome-panel* gnome-panel-data* gnome-power-manager* gnome-screensaver* gnome-screenshot* gnome-search-tool* gnome-session*
  gnome-session-bin* gnome-session-canberra* gnome-settings-daemon* gnome-sudoku* gnome-system-log* gnome-system-monitor*
  gnome-system-tools* gnome-terminal* gnome-terminal-data* gnome-user-guide* gnome-user-guide-en* gnome-utils* gnomine*
  gstreamer0.10-plugins-bad-multiverse* gstreamer0.10-plugins-good* gstreamer0.10-pulseaudio* gthumb* gthumb-data*
  gucharmap* gvfs* gvfs-backends* gvfs-bin* gvfs-fuse* gwibber* gwibber-service* hal* hostname* hplip* hplip-cups* ibus*
  ibus-m17n* ibus-table* icedtea6-plugin* ifupdown* imagemagick* indicator-applet* indicator-applet-session* indicator-me*
  indicator-session* indicator-sound* initramfs-tools* initscripts* irqbalance* jockey-common* jockey-gtk* kbd*
  language-selector* lftp* libaccess-bridge-java* libaccess-bridge-java-jni* libasound2-plugins* libatspi1.0-0*
  libbonoboui2-0* libbrasero-media0* libcamel1.2-14* libcanberra-pulse* libcompizconfig0* libcouchdb-glib-1.0-2*
  libcryptui0* libdesktopcouch-glib-1.0-2* libebackend1.2-0* libebook1.2-9* libecal1.2-7* libedata-book1.2-2*
  libedata-cal1.2-7* libedataserver1.2-11* libedataserver1.2-13* libedataserverui1.2-8* libegroupwise1.2-13* libevolution*
  libgail-gnome-module* libgconf2-4* libgconf2.0-cil* libgdata7* libgdu0* libgksu2-0* libgnome-desktop-2-17*
  libgnome-media0* libgnome-vfs2.0-cil* libgnome-window-settings1* libgnome2-0* libgnome2-common* libgnome2-perl*
  libgnome2-vfs-perl* libgnome2.24-cil* libgnomekbd-common* libgnomekbd4* libgnomepanel2.24-cil* libgnomeui-0*
  libgnomevfs2-0* libgnomevfs2-common* libgnomevfs2-extra* libgstfarsight0.10-0* libgtkhtml-editor0* libgtkhtml3.14-19*
  libgweather-common* libgweather1* libice6* libm17n-0* libmagickcore2* libmagickcore2-extra* libmagickwand2*
  libmetacity-private0* libmjpegtools-1.9* libnet-dbus-perl* libnss-mdns* liboobs-1-4* libpanel-applet2-0*
  libpolkit-gtk-1-0* libpulse-browse0* libpulse-mainloop-glib0* libpulse0* libpurple0* librpc-xml-perl* libsdl1.2debian*
  libsdl1.2debian-pulseaudio* libsm6* libsoup-gnome2.4-1* libstartup-notification0* libtelepathy-farsight0*
  libubuntuone-1.0-1* libwebkit-1.0-2* libwnck22* libwww-perl* libxaw7* libxklavier16* libxml-parser-perl* libxml-twig-perl*
  libxml-xpath-perl* libxmu6* libxres1* libxss1* libxt6* libxtst6* libxvmc1* libxxf86dga1* light-themes* linux-generic*
  linux-image-2.6.35-4-generic* linux-image-2.6.35-5-generic* linux-image-2.6.35-6-generic* linux-image-generic*
  linux-sound-base* logrotate* m17n-contrib* m17n-db* media-player-info* metacity* metacity-common* module-init-tools*
  mountall* mousetweaks* nautilus* nautilus-data* nautilus-gksu* nautilus-sendto* nautilus-sendto-empathy* nautilus-share*
  netbase* network-manager* network-manager-gnome* network-manager-pptp* network-manager-pptp-gnome* notify-osd*
  nspluginwrapper* ntfs-3g* ntpdate* nvidia-current* nvidia-settings* obex-data-server* onboard* openjdk-6-jre*
  openoffice.org-base-core* openoffice.org-calc* openoffice.org-core* openoffice.org-draw* openoffice.org-emailmerge*
  openoffice.org-gnome* openoffice.org-gtk* openoffice.org-help-en-gb* openoffice.org-help-en-us* openoffice.org-impress*
  openoffice.org-math* openoffice.org-writer* openprinting-ppds* pcmciautils* pitivi* plymouth* plymouth-label*
  plymouth-theme-ubuntu-logo* plymouth-theme-ubuntu-text* plymouth-x11* pm-utils* pm-utils-powersave-policy* policykit-1*
  policykit-1-gnome* powermgmt-base* ppp* pppconfig* pppoeconf* pptp-linux* procps* pulseaudio* pulseaudio-esound-compat*
  pulseaudio-module-bluetooth* pulseaudio-module-gconf* pulseaudio-module-x11* pulseaudio-utils* pxljr* python-aptdaemon*
  python-aptdaemon-gtk* python-compizconfig* python-desktopcouch* python-desktopcouch-records* python-farsight*
  python-gconf* python-gnome2* python-gnomeapplet* python-papyon* python-pyatspi* python-speechd* python-ubuntuone*
  python-uno* python-virtkey* python-webkit* python-wnck* quadrapassel* rhythmbox* rhythmbox-plugin-cdrecorder*
  rhythmbox-plugins* rhythmbox-ubuntuone-music-store* rsyslog* screen* screen-resolution-extra* screensaver-default-images*
  seahorse* shotwell* simple-scan* software-center* software-properties-gtk* speech-dispatcher* splix*
  system-config-printer-gnome* system-tools-backends* telepathy-butterfly* telepathy-haze* telepathy-salut* telnet* tomboy*
  totem* totem-common* totem-mozilla* totem-plugins* transmission-gtk* tsclient* ttf-mscorefonts-installer* ubufox*
  ubuntu-artwork* ubuntu-docs* ubuntu-minimal* ubuntu-standard* ubuntu-system-service* ubuntu-wallpapers*
  ubuntuone-client-gnome* udev* udisks* ufw* update-manager* update-notifier* upower* upstart* ureadahead*
  usb-creator-common* usb-creator-gtk* util-linux* vinagre* vino* wireless-crda* x-ttcidfont-conf* x11-apps* x11-common*
  x11-session-utils* x11-utils* x11-xfs-utils* x11-xkb-utils* x11-xserver-utils* xfonts-100dpi* xfonts-75dpi* xfonts-base*
  xfonts-encodings* xfonts-mathml* xfonts-scalable* xfonts-utils* xinit* xscreensaver-data* xscreensaver-gl* xserver-common*
  xserver-xorg* xserver-xorg-core* xserver-xorg-input-all* xserver-xorg-input-evdev* xserver-xorg-input-mouse*
  xserver-xorg-input-synaptics* xserver-xorg-input-vmmouse* xserver-xorg-input-wacom* xserver-xorg-video-all*
  xserver-xorg-video-apm* xserver-xorg-video-ark* xserver-xorg-video-ati* xserver-xorg-video-chips*
  xserver-xorg-video-cirrus* xserver-xorg-video-fbdev* xserver-xorg-video-i128* xserver-xorg-video-intel*
  xserver-xorg-video-mach64* xserver-xorg-video-mga* xserver-xorg-video-neomagic* xserver-xorg-video-nouveau*
  xserver-xorg-video-nv* xserver-xorg-video-openchrome* xserver-xorg-video-r128* xserver-xorg-video-radeon*
  xserver-xorg-video-rendition* xserver-xorg-video-s3* xserver-xorg-video-s3virge* xserver-xorg-video-savage*
  xserver-xorg-video-siliconmotion* xserver-xorg-video-sis* xserver-xorg-video-sisusb* xserver-xorg-video-tdfx*
  xserver-xorg-video-trident* xserver-xorg-video-tseng* xserver-xorg-video-vesa* xserver-xorg-video-vmware*
  xserver-xorg-video-voodoo* xterm* xulrunner-1.9.2* yelp*
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 452 to remove and 1 not upgraded.
After this operation, 1,885MB disk space will be freed.
[B][COLOR="Red"]You are about to do something potentially harmful
To continue type in the phrase ‘Yes, do as I say!’
 ?[/COLOR][/B]]
```

---


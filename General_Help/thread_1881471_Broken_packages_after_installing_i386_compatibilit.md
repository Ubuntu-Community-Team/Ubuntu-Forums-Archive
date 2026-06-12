---
title: "Broken packages after installing i386 compatibility"
date: 2011-11-15
forum: General Help
---

### Post by Anaximandre on 2011-11-15
Hi. I am rather a beginner in all-linux things. I installed Ubuntu 11.10 x64 a few months ago and I needed to get Lotus Notes 8.5.3 installed.

After following steps described [here]("http://metkhoo.blogspot.com/2010/10/lotus-notes-853-on-ubuntu-meerkat-1010.html") for an older version, I found out that Synaptic now tells me I have 2 broken packages when starting.

When I use the Edit > Fix broken packages menu, many packages are marked for removal, and it looks like Synaptic wants to remove all my amd64 packages to install i386 packages. I guess that as long as I do not fix the broken package issue, I will not be able to apply any update to current packages nor to use Synaptic to install anything new. However, I really fear that applying the changes WILL remove the amd64 packages to replace them by i386 ones and will break my system.

Would someone please help on this matter?


Thanks in advance

A.

Results of apt-get -f install:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpango1.0-0-dbg libgnumail-java menu-xdg libdcerpc0 libgdl-3-common gnome-panel-dbg libnumber-compare-perl libjaxp1.3-java python-evolution ekiga libgsf-1-common libgstreamer0.10-0-dbg libopal3.10.2
  python-pyorbit gir1.2-rb-3.0 liboro-java gnome-backgrounds libgda-4.0-common libgeronimo-jms-1.1-spec-java libpangomm-1.4-dbg libroken18-heimdal gtali libxerces2-java python-numpy libanjuta-3-0
  libglibmm-2.4-dbg python-mako libwrap0:i386 glchess libgtk-vnc-1.0-0 libdmapsharing-3.0-2 libtotem-plparser-dbg libsamplerate0:i386 glib-networking-dbg devhelp-common libgda-4.0-4
  gstreamer0.10-plugins-ugly-dbg libdiscid0 gnome-games cheese gdebi libhdb9-heimdal gstreamer0.10-plugins-good-dbg libswt-cairo-gtk-3-jni antlr gnobots2 python-reportlab libpdfbox-java libgnuinet-java
  libclutter-gtk-1.0-dbg gnome-icon-theme-extras libopts25 libnspr4-dbg libsamdb0 libfile-find-rule-perl libcheese-gtk20 valac-0.14 libasn1-8-heimdal libmapi0 autogen libboost-signals1.46.1 libcheese1
  libjack-jackd2-0:i386 eog-dbg libapr1 libjpfcodegen-java libnspr4-0d:i386 python-uniconvertor libgdict-1.0-6 libgda-4.0-4-dbg libcommons-cli-java gdebi-core libcapi20-3 python-lxml libboost-date-time1.46.1
  libgoffice-0.8-8-common librhythmbox-core4 libfontconfig1-dbg libcommons-logging-java libgail-dbg libgssapi3-heimdal liblapack3gf libnss3-dbg libjempbox-java gnibbles libxft2-dbg libjpf-java libmicroba-java
  python-renderpm python-talloc libndr-standard0 gnuchess-book libatk1.0-dbg librsvg2-dbg unixodbc libpt2.10.2 libopal-dbg libsvn1 browser-plugin-gnash gnome-games-extra-data libgoffice-0.8-8 python-gtk-vnc
  libjson0:i386 anjuta poppler-dbg libvala-0.14-0 libexchangemapi-1.0-0 libstringtemplate-java libwind0-heimdal network-manager-dbg libgnujaf-java gnash-common libgtk-3-0-dbg libwebkitgtk-3.0-0-dbg anjuta-dbg
  libgtk2.0-0-dbg libcluttergesture-0.0.2-0 libgladeui-2-0 libgladeui-common libgtkmm-3.0-dbg gnotski valac gir1.2-gucharmap-2.90 libjiu-java libclutter-imcontext-0.1-0 libopts25-dev libtevent0 libspandsp2
  libgsf-1-114 libjgoodies-forms-java libspeexdsp1:i386 cheese-common sound-juicer libsoup2.4-dbg libgnome-keyring0-dbg libpt-dbg libglib2.0-dev libxml2-dbg libxine1-console zlib1g-dev liblzo2-2
  libdate-calc-perl anjuta-common libantlr-java libdevhelp-3-0 iagno glines wine1.2-gecko libspin-java libboost-thread1.46.1 libasound2:i386 libflac8:i386 libjdom1-java libdconf-dbg libhcrypto4-heimdal
  libglazedlists-java libhx509-5-heimdal libvorbisenc2:i386 libclutter-1.0-dbg libmx-1.0-2 libcarp-clan-perl libfolks-eds25 libasyncns0:i386 ekiga-dbg libtext-glob-perl gstreamer0.10-plugins-base-dbg
  libheimbase1-heimdal gnome-dictionary libsamba-util0 gnome-contacts pxlib1 gedit-plugins gnumeric-common libxine1-misc-plugins libgnomeui-common liferea libmysql-java gnash fastjar gnotravex libldb1 gnect
  libclutter-gst-1.0-0 velocity quadrapassel libatspi1.0-0 libwerken.xpath-java libgfortran3 python-markupsafe libsamba-hostconfig0 libmusicbrainz3-6 libcommons-lang-java liferea-data libpulse0:i386
  libheimntlm0-heimdal libcommons-collections3-java libjgoodies-looks-java samba-dsdb-modules gnuchess libjgoodies-common-java libglib2.0-0-dbg libvorbis0a:i386 libbonoboui2-common perlmagick libjlibeps-java
  libaprutil1 libndr0 antlr3 liblog4j1.2-java libnss3-1d:i386 libgtkhtml-4.0-dbg libgail-3-0-dbg dconf-tools libexcalibur-logkit-java libsndfile1:i386 libswt-webkit-gtk-3-jni gimp-dbg gnumeric-doc
  libclutter-gtk-1.0-0 libgensec0 libbit-vector-perl ttf-droid libkrb5-26-heimdal libasound2-plugins:i386 gnome-video-effects libgdl-3-1 python-reportlab-accel libogg0:i386 libpam0g:i386 grep:i386 libxp6:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-kde compizconfig-backend-kconfig default-jre default-jre-headless grep:i386 kdesudo libpam0g:i386 libxp6:i386 plasma-netbook tcl8.4 tk8.4
Suggested packages:
  libpam-doc:i386 tclreadline
The following packages will be REMOVED:
  acpi-support acpid acroread acroread-fonts alien alsa-utils app-runner apparmor apport-gtk aptdaemon apturl asymptote at at-spi at-spi2-core avahi-daemon avahi-utils azureus banshee
  banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore base-files bash bash-completion binfmt-support blt bluez bluez-alsa bluez-cups bluez-gstreamer brasero brltty bsd-mailx bug-buddy
  build-essential carmetal checkinstall clamav clamav-daemon clamav-freshclam clamtk compiz-gnome console-setup cron cups cups-driver-gutenprint dash debhelper dpkg-dev empathy empathy-dbg epiphany-browser
  epiphany-browser-dbg epiphany-extensions evolution evolution-dbg evolution-exchange evolution-mapi evolution-plugins evolution-plugins-experimental foo2zjs foomatic-db-engine foomatic-filters ftp fuse-utils
  gamin gconf-editor gdb gdm ginn gnome-applets gnome-bluetooth gnome-control-center gnome-disk-utility gnome-keyring gnome-power-manager gnome-screensaver gnome-session gnome-session-bin
  gnome-session-fallback gnome-shell gnome-user-share gnumeric gnumeric-plugins-extra gok google-chrome-stable google-earth-stable grdesktop grep grub-common grub-gfxpayload-lists grub-pc grub-pc-bin
  grub2-common gsfonts-x11 gtkvncviewer gvfs gvfs-backends gvfs-bin gvfs-dbg gvfs-fuse gwibber gxine hamster-applet hplip hplip-cups ia32-crossover-games-demo ia32-crossover-pro ia32-libs-multiarch:i386
  ibm-lotus-activities:i386 ibm-lotus-cae:i386 ibm-lotus-feedreader:i386 ibm-lotus-notes:i386 ibm-lotus-sametime:i386 ibm-lotus-symphony:i386 icedtea-netx icedtea-plugin icedtea6-plugin indicator-datetime
  indicator-power indicator-session indicator-sound inkscape intltool irqbalance jabref jarwrapper java-wrappers jockey-common jockey-gtk kbd kde-plasma-desktop kde-standard kde-window-manager kde-workspace
  kde-workspace-bin kdeplasma-addons kdm kopete kopete-message-indicator kscreensaver kscreensaver-xsavers kubuntu-debug-installer language-selector-common language-selector-gnome latexdraw lftp lib32nss-mdns
  libaudio-scrobbler-perl libaudio2:i386 libbonoboui2-0 libgamin0 libgdu0 libgnome-speech7 libgnome2-0 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libice6:i386
  libkopete4 libnm-gtk0 libnss-mdns libqapt-runtime libqt4-declarative:i386 libqt4-designer:i386 libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-scripttools:i386 libqt4-svg:i386 libqtgui4:i386
  libreoffice-gnome libsigsegv2 libsm6:i386 libswt-gnome-gtk-3-jni libswt-gtk-3-java libswt-gtk-3-jni libsyncdaemon-1.0-1 libubuntuone-1.0-1 libubuntuone1.0-cil libunique-1.0-0 libunique-3.0-0 libwnck22
  libxine1 libxine1-x libxml-parser-perl libxp6 libxss1:i386 libxt6:i386 libxvmc1 lightdm lsb lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-multimedia lsb-printing lsb-qt4 lsb-security mencoder mousetweaks
  mplayer nautilus nautilus-dbg nautilus-dropbox nautilus-script-audio-convert nautilus-scripts-manager nautilus-sendto nautilus-share network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome nspluginviewer:i386 nspluginwrapper ntfs-3g ntpdate nvidia-current nvidia-settings onboard oneconf openjdk-7-jre openssh-server pcmciautils plasma-widget-networkmanagement
  plasma-widgets-addons policykit-1 policykit-1-gnome polkit-kde-1 ppp pppconfig pppoeconf pptp-linux pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pxljr
  python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-gnome2 python-imaging-tk python-tk python-ubuntuone-control-panel python-virtkey python-wnck qapt-batch
  rarian-compat rhythmbox rhythmbox-dbg rhythmbox-plugin-cdrecorder rhythmbox-plugins rsync rsyslog samba screen-resolution-extra seahorse sessioninstaller shotwell software-center software-properties-gtk
  spamassassin speech-dispatcher ssh ssvnc startupmanager stunnel4 telepathy-salut telnet tex-gyre tightvncserver tk tk8.5 totem totem-dbg totem-mozilla totem-plugins ttf-mscorefonts-installer ubuntu-minimal
  ubuntu-sso-client ubuntu-standard ubuntu-system-service ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk ubuntuone-couch ubuntuone-installer udisks unzip
  update-notifier upower usb-creator-common usb-creator-gtk vino vnc4server vuze winbind wine1.2 winetricks wpasupplicant x11-apps x2vnc xbase-clients xdiagnose xfonts-base xfonts-mathml xfonts-scalable xfs
  xinit xorg xserver-xorg-video-all xserver-xorg-video-intel xserver-xorg-video-openchrome xul-ext-ubufox
The following NEW packages will be installed:
  compiz-kde compizconfig-backend-kconfig default-jre default-jre-headless grep:i386 kdesudo libpam0g:i386 libxp6:i386 plasma-netbook tcl8.4 tk8.4
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  base-files bash dash (due to bash) grep
0 upgraded, 11 newly installed, 319 to remove and 1 not upgraded.
Need to get 2,581 kB of archives.
After this operation, 2,669 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'


(at which point I did not go forward...)

---

### Post by Anaximandre on 2011-11-15
Problem solved:

remove all lotus packages
Use script on [http://ubuntuforums.org/showthread.php?t=636724]("http://ubuntuforums.org/showthread.php?t=636724") to remove all dependencies from Lotus packages
Reinstall all Lotus packages..

---


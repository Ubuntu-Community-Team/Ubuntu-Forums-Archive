---
title: "Can't install libqt4-dev"
date: 2010-04-27
forum: General Help
---

### Post by walkeraj on 2010-04-27
Was attempting to install libqt4-dev so that I could use openscad, but keep running into inane dependency issues:

First I tried:

```
$ apt-get install -f libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-dev: Depends: libxft-dev but it is not going to be installed
```

Which meant that I then had to walk the dependency tree *manually* to determine the problem:

```
$ apt-get install libxft-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxft-dev: Depends: libfontconfig1-dev but it is not going to be installed
```

And then

```
$ apt-get install libfontconfig1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfontconfig1-dev: Depends: libfontconfig1 (= 2.6.0-1ubuntu12) but 2.8.0-0ubuntu1 is to be installed
```

Ah, finally some useful information!  So what's the deal here?  My /etc/apt/sources.list is:

```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
deb http://archive.ubuntu.com/ubuntu/ karmic main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe main multiverse restricted
```

If I look at the properties of libfontconfig1 in synaptic, the versions tab lists:

```
2.8.0-0ubuntu1 (now)
2.6.0-1ubuntu12 (karmic)
```

Sooo.. what does that mean,exactly?  Is the libqt4-dev package out of date?  Am I somehow ahead of where I should be?  What do I need to do?

---

### Post by guriinii on 2010-04-27
This tedious process does end. I have done it. The Packages do genuinely need the dependencies. Just keep at it.

---

### Post by walkeraj on 2010-04-27
> **guriinii said:**
> This tedious process does end. I have done it. The Packages do genuinely need the dependencies. Just keep at it.

What?  What does that even mean?  I can't 'just keep at it'.  I kept at it, but I couldn't figure it out, now I'm asking here for the answer to my problem.

---

### Post by bodhi.zazen on 2010-04-27
You should file a bug report about the "missing" dependencies on launchpad.

I would file a bug against libfontconfig1-dev

---

### Post by walkeraj on 2010-04-27
Well I'm not sure if they're "missing", they just seem to be unresolved somehow.  The main reason I came here was to determine if it is or is not a bug or if it's just something I myself need to do.  Does it look like a bug?

---

### Post by mc4man on 2010-04-27
Don't believe this is a bug - the current version of libfontconfig1 in karmic is 2.6.0-1ubuntu12 

You got  2.8.0-0ubuntu1 from somewhere, you'll need to get a matching libfontconfig1-dev  from the same source (if even possible

Otherwise you should downgrade libfontconfig1 back to the karmic version


Edit - lok at the properties of libfontconfig1 in synaptic, may show who built it

---

### Post by walkeraj on 2010-04-27
Yeah, I thought that's what I was seeing with the "now" vs. "karmic" thing.  Is there any way to tell where I got this one from?  Is that stored anywhere?

---

### Post by mc4man on 2010-04-27
> Is that stored anywhere? 

As mentioned see what the properties of  libfontconfig1 in synaptic say.

(you may be able to force the version back in synaptic - though it's possible something will break (if that version was installed as a dependency

There are some other possibilities if you can't locate the mayching -dev and don't want or can't downgrade

edit: also be aware that you may (most likely) have an updated fontconfig-config which would be a factor if downgrading - I would be careful in what you do

---

### Post by walkeraj on 2010-04-27
I looked at the properties in synaptic, but there wasn't anything to indicate where it came from, if not from Ubuntu.  Where should I look for it?  apt-cache show, maybe?

---

### Post by walkeraj on 2010-04-28
OK, so here's some more information:

```
$ apt-cache policy libfontconfig1
libfontconfig1:
  Installed: 2.8.0-0ubuntu1
  Candidate: 2.8.0-0ubuntu1
  Version table:
 *** 2.8.0-0ubuntu1 0
        100 /var/lib/dpkg/status
     2.6.0-1ubuntu12 0
        500 http://archive.ubuntu.com karmic/main Packages

```

Which is interesting, because if I run apt-cache policy against something like wine, I get:

```
$ apt-cache policy wine
wine:
  Installed: 1.1.43-0ubuntu1~karmicppa1
  Candidate: 1.1.43-0ubuntu1~karmicppa1
  Version table:
 *** 1.1.43-0ubuntu1~karmicppa1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     1.0.1-0ubuntu8 0
        500 http://archive.ubuntu.com karmic/universe Package
```

To my unfamiliar eye, this appears to mean that there is no information on where my version of libfontconfig1 came from?  Is this correct?  If I want to bring it back inline with karmic, what should I do? I attempted:

```
$ apt-get install libfontconfig1=2.6.0-1ubuntu12
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.6.0-1ubuntu12) but 2.8.0-0ubuntu1 is to be installed
```

Does this mean I need to walk backwards to downgrade it?  I attempted 'force version' in synaptic as well, but nothing happened.

---

### Post by walkeraj on 2010-04-28
Thinking it was the correct solution, I attempted to downgrade fontconfig-config, which, given that that's my ENTIRE SYSTEM, didn't seem like the right solution...

```
$ apt-get install fontconfig-config=2.6.0-1ubuntu12
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblash2 libfreebob0 gcj-4.4-jre-headless libecj-java libxml++2.6-2 libwxbase2.8-0 kdebase-runtime-data-common libpolkit-dbus2 python-numpy unetbootin-translations libgcj-bc gcj-4.4-base libxine1-x libsad2 libmodplug0c2
  libchm-bin libotr2 libfluidsynth1 python-reportlab odbcinst1debian1 libqt4-test libqt4-script openoffice.org-l10n-en-gb libqt4-network libftgl2 libglew1.5 libqt4-dbus libjack0 libxcb-xv0 libboost-program-options1.38.0
  java-common libflac++6 libchm1 gcj-4.4-jre-lib python-chm libcddb2 python-uniconvertor libprojectm2 libaudutil1 python-lxml ecj-gcj alsa-oss libexiv2-5 liblapack3gf sun-java6-bin pidgin-data libecj-java-gcj python-renderpm
  libgcj10 liblzma0 libqt4-xmlpatterns unixodbc libakonadiprivate1 libprojectm-data libsoprano4 libfontforge1 libbinio1ldbl kde-icons-oxygen sun-java6-jre htmldoc-common ecj libclucene0ldbl libuninameslist0 libcelt0
  libaudclient2 libqtcore4 python-sip4 libresid-builder0c2a kdepimlibs-data libpolkit-grant2 audacity-data libwmf-bin libxine1-console libantlr-java soprano-daemon libffado1 libqt4-sql language-pack-kde-en libspiro0
  gcj-jre-headless tcl libmowgli1 libqt4-xml libblas3gf libqt4-assistant libaudcore1 xchat-common libsidplay2 fastjar libsoundtouch1c2 libgfortran3 libstreams0 exiv2 kdelibs5-data xvfb libmcs1 libgcj-common libqt4-sql-mysql
  libxcb-shape0 libxcb-shm0 language-pack-kde-en-base kdebase-runtime-data libaudid3tag2 libmpcdec3 libxine1-bin libmms0 libxine1-ffmpeg libstreamanalyzer0 libpolkit2 python-reportlab-accel
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  aisleriot alacarte apport-gtk apturl at-spi audacious audacious-plugins audacious-plugins-extra audacity bluez-cups brasero brltty-x11 checkbox-gtk chm2pdf compiz compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins computer-janitor-gtk couchdb-bin cups cups-driver-gutenprint desktopcouch dia dia-common dia-libs empathy envyng-qt eog evince evolution evolution-couchdb evolution-data-server
  evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal f-spot file-roller firefox firefox-3.5 firefox-3.5-branding fontconfig fontforge foo2zjs foomatic-db foomatic-db-engine
  foomatic-filters gcalctool gcj-4.4-jdk gcj-4.4-jre gcj-jdk gcj-jre gconf-editor gdebi gdm gdm-guest-session gedit gfceu ghostscript ghostscript-cups ghostscript-x gimp gksu glchess glines gnect gnibbles gnobots2 gnome-about
  gnome-accessibility-themes gnome-applets gnome-blackjack gnome-codec-install gnome-control-center gnome-disk-utility gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media
  gnome-menus gnome-nettool gnome-orca gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-user-guide-en gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-plugins-good
  gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse gxine gxmessage hpijs hplip htmldoc human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n
  ibus-table imagemagick indicator-applet indicator-applet-session indicator-messages indicator-session inkscape jockey-gtk kde-l10n-engb kdebase-runtime kdebase-runtime-bin-kde4 kdelibs-bin kdelibs5 kdepimlibs5 kdesudo
  khelpcenter4 language-selector language-support-en language-support-writing-en libatspi1.0-0 libavahi-ui0 libbonoboui2-0 libbrasero-media0 libcairo-perl libcairo2 libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0
  libclutter-1.0-0 libclutter-gtk-0.10-0 libcryptui0 libdbusmenu-gtk0 libedataserverui1.2-8 libempathy-gtk-common libempathy-gtk28 libempathy30 libevdocument1 libevview1 libexchange-storage1.2-3 libflickrnet2.2-cil libfltk1.1
  libfontconfig1 libgail-common libgail-gnome-module libgail18 libgcj10-awt libgcj10-dev libgcr0 libgd2-xpm libgdict-1.0-6 libgdiplus libgdraw4 libgdu-gtk0 libgegl-0.0-0 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil
  libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-media0 libgnome-pilot2 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-perl libgnome2.24-cil libgnomecanvas2-0 libgnomekbd4 libgnomekbdui4
  libgnomepanel2.24-cil libgnomeui-0 libgpod-common libgpod4 libgraphviz4 libgs8 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19
  libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtkspell0 libgucharmap7 libgweather1 libindicate-gtk1 libknotificationitem1 liblaunchpad-integration1 liblpint-bonobo0 libm17n-0 libmagick++2 libmagickcore2 libmagickwand2
  libmetacity0 libmono-addins-gui0.2-cil libmono-cairo2.0-cil libmono-system-web2.0-cil libmono2.0-cil libnautilus-extension1 libnotify1 libpanel-applet2-0 libpango-perl libpango1.0-0 libpango1.0-common libpangomm-1.4-1
  libplasma3 libpolkit-gtk-1-0 libpolkit-qt0 libpoppler-glib4 libpoppler5 libpurple0 libqt3-mt libqt4-designer libqt4-help libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-scripttools libqt4-svg libqt4-webkit libqtgui4
  librsvg2-2 librsvg2-common libsexy2 libspectre1 libtelepathy-farsight0 libtotem-plparser12 libunique-1.0-0 libvte9 libwebkit-1.0-2 libwmf0.2-7-gtk libwnck22 libwxgtk2.8-0 libxft2 libxine1 libxine1-misc-plugins m17n-contrib
  m17n-db meld metacity mousetweaks nautilus nautilus-dropbox nautilus-sendto nautilus-share network-manager-gnome notify-osd nvidia-settings obex-data-server onboard openoffice.org-base-core openoffice.org-calc
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-hyphenation-en-us openoffice.org-impress
  openoffice.org-math openoffice.org-thesaurus-en-us openoffice.org-writer openprinting-ppds opera perlmagick phonon-backend-xine pidgin pidgin-libnotify pidgin-otr pnm2ppa policykit-1-gnome poppler-utils pxljr
  python-aptdaemon-gtk python-cairo python-desktopcouch python-desktopcouch-records python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gtk2 python-gtkhtml2
  python-gtksourceview2 python-ibus python-kde4 python-launchpad-integration python-notify python-pyatspi python-qt4 python-rsvg python-sexy python-ubuntuone-client python-uno python-virtkey python-vte python-webkit rhythmbox
  same-gnome screensaver-default-images seahorse software-center software-properties-gtk splix ssh-askpass-gnome synaptic system-config-printer-gnome telepathy-haze tomboy totem totem-mozilla totem-plugins transmission-gtk
  tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntuone-client ubuntuone-client-gnome unetbootin update-manager update-notifier usb-creator-gtk vim-gtk vinagre vino wimpiggy x11-apps x11-utils xchat
  xdg-user-dirs-gtk xorg xpra xsane xscreensaver-data xscreensaver-gl xsplash xterm xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity
The following packages will be DOWNGRADED:
  fontconfig-config
0 upgraded, 0 newly installed, 1 downgraded, 384 to remove and 0 not upgraded.
Need to get 51.6kB of archives.
After this operation, 1,595MB disk space will be freed.
Do you want to continue [Y/n]?
```

Turns out, the answer was to downgrade both packages on a single line:

```
$ apt-get install libfontconfig1=2.6.0-1ubuntu12 fontconfig-config=2.6.0-1ubuntu12
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be DOWNGRADED:
  fontconfig-config libfontconfig1
0 upgraded, 0 newly installed, 2 downgraded, 0 to remove and 0 not upgraded.
Need to get 176kB of archives.
After this operation, 12.3kB disk space will be freed.
Do you want to continue [Y/n]? 
```

So... YAY!

---


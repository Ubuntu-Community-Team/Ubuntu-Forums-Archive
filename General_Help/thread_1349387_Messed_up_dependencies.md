---
title: "Messed up dependencies"
date: 2009-12-08
forum: General Help
---

### Post by carstenbn on 2009-12-08
Hello,

I wanted to install Inkscape 0.47 but couldn't find it anywhere. Decided to grab it from packages.debian.org. The .deb specified some dependencies were missing*:

> libgconf, libdbus, libxml, gconf2-common(and I noticed they WERE installed but that didn't satisfy the software apparently.)

So I went ahead and installed these, until gconf2-common gave me an error message saying dependencies were messed up. Had already been told that, and fixed it with apt-get install -f.

However, this time the list of packages to be remove is basically much of the software that I always use:

> akonadi-kde apturl at-spi bluefish bluez-gnome brasero cheese
  compizconfig-backend-gconf dolphin epiphany-browser-data epiphany-extensions
  epiphany-gecko epiphany-webkit evince evolution-rss exaile f-spot file-roller
  firefox-3.5-gnome-support firefox-3.7-gnome-support gcalctool gconf2 gdebi gdm
  gedit gksu gnome-app-install gnome-do gnome-do-plugins gnome-games-data
  gnome-keyring gnome-media gnome-media-common gnome-mount gnome-orca
  gnome-power-manager gnome-screensaver gnome-system-monitor gnome-system-tools
  gnome-web-photo gparted gstreamer0.10-gnomevfs gstreamer0.10-plugins-good
  gucharmap gufw gvfs gvfs-backends inkscape jockey-gtk kdebase-bin kdebase-data
  kdebase-runtime kdebase-runtime-bin-kde4 kdenlive kfind khelpcenter4 kmail
  konqueror konqueror-nsplugins libbonoboui2-0 libbrasero-media0 libcamel1.2-14
  libcryptui0 libebook1.2-9 libecal1.2-7 libedataserver1.2-11 libevolution3.0-cil
  libgail-gnome-module libgconf2-4 libgconf2-ruby libgconf2-ruby1.8
  libgconf2.0-cil libgksu2-0 libgnome-desktop-2-7 libgnome-media0
  libgnome-vfs2.0-cil libgnome2-0 libgnome2-common libgnome2-gconf-perl
  libgnome2-perl libgnome2-ruby libgnome2-ruby1.8 libgnome2-vfs-perl
  libgnome2.0-cil libgnomedesktop2.20-cil libgnomekbd-common libgnomekbd3
  libgnomekbdui3 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgnomevfs2-ruby libgnomevfs2-ruby1.8 libgoffice-0-6
  libgoffice-gtk-0-6 libgsf-gnome-1-114 libgweather-common libgweather1
  libkdepim4 libkleo4 libkonq5 libkpgp4 libksieve4 libmaildir4 libmbca0
  libmetacity0 libmimelib4 libpanel-applet2-0 libpanel-applet2-ruby
  libpanel-applet2-ruby1.8 libtotem-plparser12 metacity-common miro
  network-manager-gnome notification-daemon onboard openoffice.org-gtk phonon
  phonon-backend-gstreamer pidgin pidgin-libnotify pitivi policykit-gnome
  python-gconf python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-pyatspi ruby-gnome2 seahorse seahorse-plugins seamonkey-gnome-support
  shutter software-properties-gtk soundconverter spicebird-gnome-support
  system-config-printer-gnome thunderbird-3.1-gnome-support totem-common
  totem-gstreamer totem-mozilla totem-plugins ubufox ufraw update-manager
  update-notifier vinagre xchat xchat-common xfce4-session xubuntu-desktop
  xulrunner-1.9-gnome-support xulrunner-1.9.1-gnome-support
  xulrunner-1.9.3-gnome-support yelp

(After this operation, 490MB disk space will be freed.)Which, of course, makes me nervous and suspicious. Must have messed something up badly, and I'm not an expert with this system so basically pretty clueless at this point.

Nothing can be installed as of now because the package manager demands that I apt-get install -f first.

Help??? :-k


* The inkscape deb specified libgconf, which in turn wanted me to get libdbus and libxml2, and one of those also requested gconf2_common (so I downloaded all of these from packages.debian.oorg unstable distribution)

---

### Post by Zorael on 2009-12-08
Likely versioning conflicts if you added out-of-repo packages. Try using aptitude instead of apt; it should tell you *why* stuff has to be removed.
```
$ sudo aptitude install -fPvv
```

Just out of curiosity; the Inkscape in Karmic main, isn't it v0.47?
```
$ apt-cache policy inkscape
inkscape:
  Installed: (none)
  Candidate: 0.47~pre4-0ubuntu1
  Version table:
     0.47~pre4-0ubuntu1 0
        500 http://se.archive.ubuntu.com karmic/main Packages
```

---

### Post by snowpine on 2009-12-08
Hi Carstenbn, please do not install Debian packages in Ubuntu. :) The two systems are similiar, but not identical.

Ubuntu is a "stable" distro, so assuming you're using Karmic, you'll get 0.47, the stable version of Inkscape as of October 2009 (that's what the 9.10 stands for).

If for some reason 1-month-old software is too "outdated" for you, I'd recommend getting Inkscape directly from [www.inkscape.org](www.inkscape.org) rather than trying to use a .deb packaged for a different Linux distribution. Obviously you will lose the stability of using only tested packages from the Ubuntu repository.

Good luck!

---

### Post by carstenbn on 2009-12-08
Ah, thanks for the useful information guys :) looks like this is enough to move forward with. I did go ahead and remove all that software, and now it seems no application is associated with opening .deb files... any takers? 

:mad: I should Google some more before making choices...

---


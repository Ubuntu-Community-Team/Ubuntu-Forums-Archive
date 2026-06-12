---
title: "Frustration with Audacity"
date: 2006-05-26
forum: General Help
---

### Post by Rippy on 2006-05-26
Ok, I've got a near-fresh install of Ubuntu that I wan to install Audacity on. I try to install it and I get an error: apparently it needs a newer version of the library libwxgtk to run. I search that in the package manager and find nothing, so I google it and find a debian file for it. I download it.

Then THAT needs 3 or so other libraries:
libc6
libgcc1
libstdc++6

I'm willing to bet that one or more of those libraries depend on even more libraries.

I guess what I'm asking is, is there any easier way than downloading and installing every freakin' library like that?

(note: when trying to add it in the package manager, it says audacity has "unresolved dependencies" and basically doesn't allow it.)

---

### Post by localzuk on 2006-05-26
How are you trying to install audacity? Also, have you got all the repositories enabled as per [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) ?

---

### Post by johnc4510 on 2006-05-26
Have you enabled the universe and multiverse repositories in Synaptic?

---

### Post by Rippy on 2006-05-26
crap....

Ok, I followed the instructions in the link you posted. (I'd done it before, but then re-installed, so I forgot to do it again). However, my desperate tinkering lead to one broken package: libstdc++6

It also says that, to remove it, the following needs to be removed:
Pretty much everything on my hard disk. openoffice, firefox, gaim, and all the things i've never even heard of.

I have no idea if it's going to RE-install those (as you've probably realised, I'm a linux/ubuntu idiot). So I'm reluctant to move ahead. Either way, after adding the repositories, audacity still gives me an error when trying to add it through the package manager.

---

### Post by johnc4510 on 2006-05-26
Try this in terminal:
sudo apt-get -f install

---

### Post by Rippy on 2006-05-26
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  acpi-support alien apt apt-utils aptitude aspell aspell-en audacity
  base-config bluez-cups cupsys cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data debhelper dselect dvd+rw-tools evince firefox
  firefox-gnome-support foomatic-db-gimp-print foomatic-db-hpijs freeglut3
  gaim gdm gedit gksu gnome-app-install gnome-cups-manager gnome-games
  gnome-media gnome-netstatus-applet gnome-spell gnome-system-monitor
  gnome-volume-manager gnomemeeting groff-base gs-common gs-esp
  gstreamer0.8-misc gstreamer0.8-vorbis hpijs hplip-base hplip-data html2text
  hwdb-client ijsgimpprint language-selector language-support-en libaspell15
  libdjvulibre15 libgc1c2 libgksu1.2-0 libgksuui1.0-0 libgl1-mesa
  libgl1-mesa-dri libgle3 libglu1-mesa libglut3 libgnomecupsui1.0-1
  libgtkspell0 libid3-3.8.3c2 libmusicbrainz2c2 libmusicbrainz4c2
  libmyspell3c2 libopenal0 libopenh323-1.15.3c2 libpoppler0c2
  libpoppler0c2-glib libpt-1.8.3c2 libpt-plugins-alsa libpt-plugins-v4l
  libpt-plugins-v4l2 libsmpeg0c2 libstdc++6 libstlport4.6c2 libwpd8c2
  libwvstreams4.0c2-base libwvstreams4.0c2-extras libxplc0.3.11c2 lshw man-db
  mesa-utils mozilla-firefox-locale-en-gb notification-daemon openoffice.org2
  openoffice.org2-base openoffice.org2-calc openoffice.org2-common
  openoffice.org2-core openoffice.org2-draw openoffice.org2-evolution
  openoffice.org2-gnome openoffice.org2-impress openoffice.org2-l10n-en-us
  openoffice.org2-math openoffice.org2-writer pnm2ppa
  powermanagement-interface python-apt python-gnome2-extras python-id3lib
  python-musicbrainz python-uno python2.4-apt python2.4-gnome2-extras
  python2.4-id3lib python2.4-musicbrainz rhythmbox rss-glx serpentine
  sound-juicer synaptic telnet toshset totem totem-gstreamer ubuntu-desktop
  ubuntu-minimal ubuntu-standard update-manager update-notifier w3m wvdial
  x-window-system-core xbase-clients xdriinfo xscreensaver-gl xvncviewer yelp
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libstdc++6 (due to apt)
0 upgraded, 0 newly installed, 129 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 464MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'

There's the result. I'm guessing accepting would NOT be a good idea?

---

### Post by johnc4510 on 2006-05-26
No, but this is beyond me. Sorry

---

### Post by Rippy on 2006-05-26
Alright, I appreciate the help anyway.

---

### Post by Scunizi on 2006-05-26
This may be a stupid question, but when you tried to do the install, did you do it from synaptic? or download a deb from someplace else?  I did it from synaptic and it all works..  The one library file you're having a problem with,  instead of uninstalling it, will synaptic simply re-install it?

---


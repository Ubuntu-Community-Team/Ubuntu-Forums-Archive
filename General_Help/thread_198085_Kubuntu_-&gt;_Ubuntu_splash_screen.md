---
title: "Kubuntu -&gt; Ubuntu splash screen"
date: 2006-06-16
forum: General Help
---

### Post by Owdy on 2006-06-16
User installed Kubuntu. Then he installed Gnome and ubuntu-desktop and removed almost all kde stuff, included kubuntu-desktop.

Now he has gnome and ubuntu, but booting usplash image is still blue Kubuntu. How to change that to Ubuntu version?

---

### Post by bruce89 on 2006-06-16
```
sudo aptitude purge kubuntu-desktop
``` might work, but it probably won't, as kubuntu-desktop would have had to be installed by aptitude in the first place.  Otherwise ```
sudo apt-get remove adept akregator amarok amarok-xine ark arts artsbuilder avahi-daemon bogofilter bogofilter-bdb bogofilter-common debtags enscript flac gtk2-engines-gtk-qt gwenview imagemagick k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kitchensync klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpersonalizer kpf kppp krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt latex-xft-fonts libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-core4 libavahi-qt3-1 libdaemon0 libdbus-qt-1-1c2 libflac++5c2 libgadu3 libgpgme11 libgsl0 libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmodplug0c2 libmpcdec3 libnss-mdns liboggflac3 libopenexr2c2a libpcre3 libpoppler1-qt libpythonize0 libqt-perl libqt3-mt librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp2c2a libxcomposite1 libxine-main1 libxvmc1 menu-xdg openoffice.org-kde perl-suid poster postfix procmail psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert vorbis-tools wlassistant
``` will remove Kubuntu. (from [http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php))

---

### Post by Neo Ex on 2006-06-16
I think (I'm not sure!) you need to remove the kubuntu-artwork-usplash package.

---

### Post by bruce89 on 2006-06-16
There will be remnants of Kubuntu lying around, so if the above command is executed, that will remove them, if that's what is wanted.

---

### Post by Ramses de Norre on 2006-06-16
You can configure which splash is used with ```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by Owdy on 2006-06-17
[quote=Ramses de Norre]You can configure which splash is used with ```
sudo update-alternatives --config usplash-artwork.so
```[/quote]

```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.
```

---


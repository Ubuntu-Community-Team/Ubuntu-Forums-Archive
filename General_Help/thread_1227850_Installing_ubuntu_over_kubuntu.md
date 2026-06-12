---
title: "Installing ubuntu over kubuntu"
date: 2009-07-31
forum: General Help
---

### Post by Zoyberk on 2009-07-31
hello,

I would like to replace me Kubuntu whit Ubuntu, i have quite lot of data and no place to backup so i cant clean install.

I know there is command to install Gnome desktop, but will then this be ubuntu or onley Kubuntu whit Gnome? and if this is like Ubuntu, then how to completely remove all KDE stuff and leave only my data.

---

### Post by NETabuse on 2009-07-31
Not sure actually, are the sources between kubuntu and ubuntu different, i would suspect so. I did the reverse of what you mentioned and installed kde on ubuntu, it actually switched my boot spalsh screen on me and now apparently I run kubuntu :) 

Anyway, if you want, you can backup your /home/zoyberk  directory to an external disc, then wipe and re-install your system, then restoring your zoyberk directory to the new install will revert most of your settings nad personal documents. 

I sometimes like to just backup my data when i do a os migration, so i leave all the .xxx directories out of my backup. it's good to just start fresh sometimes.

Lastly, if you want a bit more of a complete migration and hang onto things you installed, you can use dpkg to export the list of packages you have installed, then re-import them to your new setup after re-installing a base system, and then add the packages you had in your old setup under the new systems setup,,, of course you're really on a bit of a dodgy one with that as if kbuntu and ubuntu have differences in package names etc, might not go so smoothly.  You may have to cherry pick packages from your export, and repair names that are different , so it won't be devoid of effort.

Anyway, not a difinitive answer for your question, but just some thoughts on the area.

---

### Post by wojox on 2009-07-31
Good site:

[http://psychocats.net/ubuntu/kdegnome](http://psychocats.net/ubuntu/kdegnome)

Scroll down to the bottom.

---

### Post by Zoyberk on 2009-07-31
thanks for answer,
..i was thinking about clean install, but just not felling backing up whole sistem.
I tought of installing gnome and then deleting kde too, but want to see some high thoughts on that since i dont want to screw up whole system agen XD

---

### Post by Zoyberk on 2009-07-31
> **wojox said:**
> Good site:

[http://psychocats.net/ubuntu/kdegnome](http://psychocats.net/ubuntu/kdegnome)

Scroll down to the bottom.

Thanks for that, but if remove kde after installing gnome is that copletly the same as clean install ubuntu or difrent?

---

### Post by Zoyberk on 2009-07-31
Installed Gnome, all work perfect, except i cant set up gdm as loogin screen.
I tried pkg-reconfigure gdm and it didnt work, also tried first install gdm and then do that and id didnt work.
 any sugestions on that? XD

And if i now/ and how delete all what is kde is it safe? or i must set up gdm insted of kdm first?

:D:D

---

### Post by egalvan on 2009-07-31
> **NETabuse said:**
> Not sure actually, are the sources between kubuntu and ubuntu different, i would suspect so.

If you are talking about the repositories, then no,  they are the same...


>  I did the reverse of what you mentioned and installed kde on ubuntu, it actually switched my boot spalsh screen on me and now apparently I run kubuntu :) 

No, that is only the splash screen. You can choose what to boot into
KDE or Gnome or whatever by using the boot options available on the log-in screen.

Install 'startupmanager' (available via Synaptic) to easily change splash screens and other options.

> **Zoyberk said:**
> Installed Gnome, all work perfect, **except i cant set up gdm as loogin screen.**
I tried pkg-reconfigure gdm and it didnt work, also tried first install gdm and then do that and id didnt work.
 any sugestions on that?


Again, 'startupmanager' is one easy answer to this.


And I run Gnome/KDE on ALL my Ubuntu machines.
It bloats the menus, and the hard drive has more installed,
but otherwise no problems.
I just pick what I want to boot into at the boot screen.

Gnome apps run in KDE, and KDE apps run in Gnome.

Then their is XFCE, also installed on a couple of my older lappies,
and a couple of old Dell Optiplex's.

And Puppy, to make four.

---

### Post by slakkie on 2009-07-31
> **Zoyberk said:**
> Installed Gnome, all work perfect, except i cant set up gdm as loogin screen.
I tried pkg-reconfigure gdm and it didnt work, also tried first install gdm and then do that and id didnt work.
 any sugestions on that? XD

And if i now/ and how delete all what is kde is it safe? or i must set up gdm insted of kdm first?

:D:D

```

# Stop KDM
/etc/init.d/kdm stop
# Change your default desktop manager:
echo $(which gdm) | sudo tee /etc/X11/default-display-manager
# Start gdm
/etc/init.d/gdm start

```

---

### Post by Zoyberk on 2009-07-31
ok, setuped up gdm and ubuntu fully working, now just need to compleatly remove all kde stuff and apps, leaving that for tomorow.

Thanks for help XD

---

### Post by theozzlives on 2009-07-31
```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde
```

---

### Post by Zoyberk on 2009-08-02
removed KDE and all working great =)

Thanks to all for help XD

---


---
title: "How to remove Ubuntu Gui!"
date: 2010-04-19
forum: General Help
---

### Post by waloshin on 2010-04-19
apt-get --purge remove ubuntu-desktop
Reading package lists...
Building dependency tree...
Reading state information...
Package ubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have installed Ubuntu desktop on Ubuntu Server to get Boinc manager running. Now I want to remove Ubuntu-desktop.

---

### Post by waloshin on 2010-04-19
Bump

---

### Post by lovinglinux on 2010-04-19
Please don't bump your thread so fast. This is not IM. It is recommended that you wait until a day before bumping.

The ubuntu-desktop is a metapackage, which means when you install it, it also install all dependencies required by the Ubuntu Desktop. Nevertheless, removing it doesn't remove any of the dependencies. You will have to remove all ubuntu-desktop packages manually.

See [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

That tutorial is for removing ubuntu-desktop after installing kubuntu-desktop, but it should work too for your situation.

---

### Post by jerome1232 on 2010-04-19
Should you ever temporarily need a gui in the future it would be alot easier to install a small window manager and xorg instead of the ubuntu-desktop meta package. They won't pull in thousands of dependencies with them.

Just for future reference.

---

### Post by lovinglinux on 2010-04-19
> **jerome1232 said:**
> Should you ever temporarily need a gui in the future it would be alot easier to install a small window manager and xorg instead of the ubuntu-desktop meta package. They won't pull in thousands of dependencies with them.

Just for future reference.

+1

At least install ubuntu-minimal or kde-minimal, not the whole desktop.

---

### Post by waloshin on 2010-04-19
> **lovinglinux said:**
> Please don't bump your thread so fast. This is not IM. It is recommended that you wait until a day before bumping.

The ubuntu-desktop is a metapackage, which means when you install it, it also install all dependencies required by the Ubuntu Desktop. Nevertheless, removing it doesn't remove any of the dependencies. You will have to remove all ubuntu-desktop packages manually.

See [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

That tutorial is for removing ubuntu-desktop after installing kubuntu-desktop, but it should work too for your situation.

So will the core server operating system still be intact? Apache, mysql, webmin...

---

### Post by lovinglinux on 2010-04-19
> **waloshin said:**
> So will the core server operating system still be intact? Apache, mysql, webmin...

I think so, but I never tried this on a server. To make sure, you could install a server on a VM and run that command.

---

### Post by lavinog on 2010-04-19
There was a trick to mark all packages for removal, then mark ubuntu-server for installation to keep the packages needed.
The problem is that now there seems to be a safety to prevent users from marking required packages for removal, so I don't know if this works anymore.

Maybe a simple script could be make a list of all packages installed that are not required by the metapackage

---

### Post by waloshin on 2010-04-19
> **lovinglinux said:**
> Please don't bump your thread so fast. This is not IM. It is recommended that you wait until a day before bumping.

The ubuntu-desktop is a metapackage, which means when you install it, it also install all dependencies required by the Ubuntu Desktop. Nevertheless, removing it doesn't remove any of the dependencies. You will have to remove all ubuntu-desktop packages manually.

See [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

That tutorial is for removing ubuntu-desktop after installing kubuntu-desktop, but it should work too for your situation.

Funny thing is all this did was uninstall Ubuntu and install Kubuntu.

---

### Post by lovinglinux on 2010-04-19
> **waloshin said:**
> Funny thing is all this did was uninstall Ubuntu and install Kubuntu.

I guess I wasn't clear enough. That tutorial is for doing exactly that. In your case, you should not run the last part of the command which is:

```
&& sudo apt-get install kubuntu-desktop
```

The part above, located at the end is what installed kubuntu-desktop. So now, use this:

```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig
```

This was obtained from [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome), without the last command.

---

### Post by waloshin on 2010-04-20
Ok i have done that and Kubuntu is unistalled , but now mysql doesnt want to start. 

I have tried: /etc/init.d/mysql start

And also tried through webmin.

Webmin also gives me this error: 

Click this button to start the MySQL database server on your system with the command /etc/init.d/mysql start >/dev/null 2>&1 &. This Webmin module cannot administer the database until it is started.

Also when I reboot the server it hangs on:

*starting Apparmor profiles

---

### Post by lovinglinux on 2010-04-20
> **waloshin said:**
> Ok i have done that and Kubuntu is unistalled , but now mysql doesnt want to start. 

I have tried: /etc/init.d/mysql start

And also tried through webmin.

Webmin also gives me this error: 

Click this button to start the MySQL database server on your system with the command /etc/init.d/mysql start >/dev/null 2>&1 &. This Webmin module cannot administer the database until it is started.

Also when I reboot the server it hangs on:

*starting Apparmor profiles

Install Kubuntu again. As I said, I never done this on a server, so I still suggest you test those things on a VM before applying to your server.

---

### Post by 3rdalbum on 2010-04-20
> **waloshin said:**
> Ok i have done that and Kubuntu is unistalled , but now mysql doesnt want to start. 

I have tried: /etc/init.d/mysql start

If you're using Ubuntu 9.10 or later, then this command won't work because of the transition to Upstart.

You'd want to use:

```
sudo service mysql start
```

---


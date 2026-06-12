---
title: "Any way to use dpkg to rollback recently installed packages?"
date: 2010-05-30
forum: General Help
---

### Post by cryptotheslow on 2010-05-30
Hi,

Using Ubuntu Lucid with Gnome desktop.

I was just playing around trying to find a media player I liked and installed Bangarang via the Software Centre. This took an absolute age and now I realise why - it has basically installed the entire KDE environment and associated lib packages as well.

I have found /var/log/dpkg.log shows what has been installed and of course I can wade through that to make a list of all the packages and uninstall them all via Synaptic. But that will take a long time to do.

Is there anyway to somehow automate rolling back any package changes since a certain time?

I've checked the man for dpkg and I can't see any mention of anything like this.

Any ideas?

Thanks

---

### Post by gaussian on 2010-05-30
> **cryptotheslow said:**
> Hi,

Using Ubuntu Lucid with Gnome desktop.

I was just playing around trying to find a media player I liked and installed Bangarang via the Software Centre. This took an absolute age and now I realise why - it has basically installed the entire KDE environment and associated lib packages as well.

I have found /var/log/dpkg.log shows what has been installed and of course I can wade through that to make a list of all the packages and uninstall them all via Synaptic. But that will take a long time to do.

Is there anyway to somehow automate rolling back any package changes since a certain time?

I've checked the man for dpkg and I can't see any mention of anything like this.

Any ideas?

Thanks

First thing to try:
Go to command line (open terminal):
1) sudo apt-get remove bangarang 
Should tell you about automatically installed packages being no longer needed.
2) sudo apt-get autoremove


More hardcore way (if the first does not work):
1) copy /var/log/dpkg.log somewhere and edit so that each line contains only name of a package you want to remove. Call the file toremove.txt
2) sudo apt-get remove `cat toremove.txt`

Read carefully the list of packages in each case that apt-get wants to remove.

---

### Post by cryptotheslow on 2010-05-30
Thanks for the reply :)

Option 1 only gave 1 other package to auto-remove (as below)

Looks like I am back to manually going through the dpkg log to compile a list of packages to remove and then feed it into your option 2.

Should speed things up a little... and lesson learnt.... use Synaptic to install new packages so I get to see the dependencies before committing. Would be nice if the Software Centre popped up a message along the lines of "This application is intended for use with the KDE desktop environment - you do not currently have this installed - are you sure you want to proceed?" (Yes/No) type question in these cases.

In fact I think it may be less effort and time to clean install Lucid than wade through that log to work out what to remove. Thankfully I separated out /home to its own partition on the last install.

```
graham@gt-desktop:~$ sudo apt-get remove bangarang
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkcddb4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  bangarang
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,499kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162233 files and directories currently installed.)
Removing bangarang ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
graham@gt-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libkcddb4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 725kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162174 files and directories currently installed.)
Removing libkcddb4 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
graham@gt-desktop:~$ 

```

---

### Post by JustinR on 2010-05-30
If you search on Google for Pyschocats, an ubuntu oriented website about desktop environments, there's a code to remove KDE. Which will remove everything that media player installed.

Much easier than reinstalling Ubuntu.

Edit:

```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint freespacenotifier gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 icoutils ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kbluetooth kcalc kcm-gtk kcm-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knm-runtime knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libattica0 libaudio2 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libepub0 libexiv2-6 libflac++6 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkcddb4 libkdcraw8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-8 libkfontinst4 libkipi7 libkleo4 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblastfm0 libmimelib4 libmng1 libmodplug0c2 libmpcdec3 libmsn0.3 libmysqlclient16 libokularcore1 libotr2 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4 libprocessui4 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libtag-extras1 libtaskmanager4 libvncserver0 libweather-ion4 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-message-indicator plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip quassel quassel-data shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-nepomuk && sudo apt-get install ubuntu-desktop
```

---

### Post by cryptotheslow on 2010-05-30
I have no idea what version of Ubuntu that code was intended for and have no way of knowing if that remove list is sane or not. I appreciate the help 100% but there is no way I am blindly going to copy/paste an apt-get remove like that.

I'm back to weighing up the time required to clean install vs wading through a few thousand lines of dpkg log to uninstall this mess.

I'm leaning towards clean install right now.

---

### Post by JustinR on 2010-05-30
I told you the website. [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Its the code to remove KDE, check it yourself.

The code is designed for Ubuntu 10.04. There are also versions for 9.10 and previous.

Its against the Code of Conduct terms of the Ubuntu forum to post malicious codes, no exceptions. I don't plan on breaking that rule any time soon. I've used the code myself with no problems.

---

### Post by gaussian on 2010-05-30
Also, unless you 
1) have a very small hard drive 
or
2) want to be a purist for some reason and don't want to have any of "KDE stuff polluting your computer";
then the best thing might just be leave the packages installed. You might find that you will enjoy some of the KDE programs. E.g. my personal preference was to run Gnome, although lately I have been gravitating towards using LXDE. I still keep full Gnome and most of KDE installed on my computers. K3B and Digikam (IMHO) are two programs that are much better than their non-KDE alternatives. Amarok used to be also a killer program, but I gave up on it when they went to version 2.0 with a fresh code-base (and Rhythmbox and Banshee advanced).

I know this is OT, but this might be the easiest long run solution.

---

### Post by ezsit on 2010-05-30
+1
> ...the best thing might just be leave the packages installed.

If you are not starving for hard drive space, just leave the KDE stuff there. It doesn't hurt anything, doesn't take up resources other than hard drive space, and doesn't harm or degrade your system performance in the slightest way.

---

### Post by rhd on 2010-05-31
Did you install all of the packages on the same day? You can use this grep/sed/xargs pipeline to give you a list of all packages you installed on one day:
```
grep -E "$INSTALLDATE [0-9: ]* status installed" /var/log/dpkg.log | sed  "s_$INSTALLDATE [0-9: ]* status installed__"  | sed 's_[a-z0-9.\-]*$__' | xargs

```But replace "$INSTALLDATE" with the day you installed the packages in YYYY-MM-DD format. Then, conceivably, you could pipe it to [FONT=Courier New]apt-get purge.:)
[/FONT]

---

### Post by gaussian on 2010-05-31
Also fairly simple solution that accomplishes most of this: remove one of the key libraries of KDE and let APT remove everything that depends on it. Just pay attention that you don't remove anything else.

On my little EEE I would get rid of most of KDE with:
```

sudo apt-get remove kdelibs-bin
sudo apt-get autoremove

```

---

### Post by cryptotheslow on 2010-05-31
> **rhd said:**
> Did you install all of the packages on the same day? You can use this grep/sed/xargs pipeline to give you a list of all packages you installed on one day:
```
grep -E "$INSTALLDATE [0-9: ]* status installed" /var/log/dpkg.log | sed  "s_$INSTALLDATE [0-9: ]* status installed__"  | sed 's_[a-z0-9.\-]*$__' | xargs

```But replace "$INSTALLDATE" with the day you installed the packages in YYYY-MM-DD format. Then, conceivably, you could pipe it to [FONT=Courier New]apt-get purge.:)
[/FONT]

That nearly works :D But it's not quite right as a package list to purge as it picks up things like hicolor-icon-theme, man-db and desktop-file-utils which from the log appear to just be being triggered rather than installed:

```
2010-05-30 20:53:48 trigproc man-db 2.5.7-2 2.5.7-2
2010-05-30 20:53:51 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-05-30 20:53:51 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
```

That said, it is a really useful starting point that will only take a few minutes to tidy up :D

Many thanks for everyone's help :D


The complete output, if it is of any use:
```
graham@gt-desktop:~$ grep -E "$2010-05-30 [0-9: ]* status installed" /var/log/dpkg.log | sed  "s_$2010-05-30 [0-9: ]* status installed__"  | sed 's_[a-z0-9.\-]*$__' | xargs
2 hicolor-icon-theme 2 desktop-file-utils 2 python-gmenu 2 man-db 2 python-support 2 libid3-3.8.3c2a 2 tagtool 2 libc-bin 2 hicolor-icon-theme 2 man-db 2 desktop-file-utils 2 python-gmenu 2 python-support 2 libcddb2 2 libdvbpsi5 2 libebml0 2 libiso9660-7 2 liblua5.1-0 2 libmatroska0 2 libsdl-image1.2 2 libtar 2 libvcdinfo0 2 vlc-data 2 libvlccore2 2 libvlc2 2 libupnp3 1: 2 vlc-nox 2 libxcb-keysyms1 2 vlc 2 vlc-plugin-pulse 2 libc-bin 2 vlc-plugin-pulse 2 vlc 2 vlc-nox 2 libcddb2 2 libdvbpsi5 2 libmatroska0 2 libebml0 2 libvcdinfo0 2 libiso9660-7 2 liblua5.1-0 2 libsdl-image1.2 2 libtar 2 libupnp3 1: 2 libvlc2 2 libvlccore2 2 libxcb-keysyms1 2 vlc-data 2 man-db 2 desktop-file-utils 2 python-gmenu 2 libc-bin 2 hicolor-icon-theme 2 python-support 2 man-db 2 hicolor-icon-theme 2 shared-mime-info 2 desktop-file-utils 2 python-gmenu 2 fontconfig 2 python-support 2 libattica0 2 libdbusmenu-qt2 2 libqt4-script 4: 2 libqt4-designer 4: 2 libphonon4 4: 2 libpolkit-qt-1-0 2 libqt4-sql 4: 2 libqt4-qt3support 4: 2 libqt4-svg 4: 2 libqt4-xmlpatterns 4: 2 libqt4-webkit 4: 2 libclucene0ldbl 2 libiodbc2 2 soprano-daemon 2.4.2+ 2 libsoprano4 2.4.2+ 2 libexiv2-6 2 libstreams0 2 libstreamanalyzer0 2 kdelibs5-data 4: 2 shared-desktop-ontologies 2 libqca2 2 libqt4-opengl 4: 2 libssh-4 2 kdebase-runtime-data 4: 2 oxygen-icon-theme 4: 2 libxine1-bin 2 libxine1-misc-plugins 2 libxcb-shape0 2 libxcb-shm0 2 libxcb-xv0 2 libxine1-x 2 libxine1-console 2 libxine1 2 phonon-backend-xine 4: 2 phonon 4: 2 exiv2 2 libboost-program-options1.40.0 2 libakonadiprivate1 2 kdepimlibs-data 4: 2 libqt4-assistant 4: 2 libqt4-help 4: 2 libqt4-scripttools 4: 2 libqt4-test 4: 2 python-sip 2 python-qt4 2 icoutils 2 libkephal4 4: 2 libqimageblitz4 1: 2 libsolidcontrolifaces4 4: 2 libplasma-geolocation-interface4 4: 2 mysql-common 2 libmysqlclient16 2 mysql-server-core-5.1 2 mysql-client-core-5.1 2 libqt4-sql-mysql 4: 2 akonadi-server 2 ksysguardd 4: 2 libpackagekit-qt-12 2 libpackagekit-glib2-12 2 python-packagekit 2 ttf-dejavu-extra 2 ttf-dejavu 2 virtuoso-nepomuk 2 python-packagekit 2 python-central 2 packagekit-backend-apt 2 packagekit-backend-apt 2 python-central 2 packagekit 2 kdelibs-bin 4: 2 kdelibs5 4: 2 libplasma3 4: 2 plasma-scriptengine-javascript 4: 2 kdepimlibs5 4: 2 libkfontinst4 4: 2 libkscreensaver5 4: 2 libkworkspace4 4: 2 libplasmagenericshell4 4: 2 libprocesscore4 4: 2 libprocessui4 4: 2 libsolidcontrol4 4: 2 libplasma-applet-system-monitor4 4: 2 libplasmaclock4 4: 2 libksgrd4 4: 2 libtaskmanager4 4: 2 libweather-ion4 4: 2 kdebase-runtime 4: 2 libkcddb4 4: 2 bangarang 2 python-kde4 4: 2 kdesudo 2 gdebi-kde 2 plasma-dataengines-workspace 4: 2 kdepim-runtime 4: 2 plasma-widgets-workspace 4: 2 kdebase-workspace-data 4: 2 kdebase-workspace-kgreet-plugins 4: 2 polkit-kde-1 2 kdebase-workspace-bin 4: 2 update-manager-kde 1: 2 update-manager-kde 1: 2 gdebi-kde 2 python-central 2 install-package 2 software-properties-kde 2 software-properties-kde 2 python-central 2 kpackagekit 2 kubuntu-debug-installer 2 libc-bin 2 python-support 2 man-db 2 hicolor-icon-theme 2 desktop-file-utils 2 python-gmenu 2 python-support 2 libdiscid0 2 libmusicbrainz3-6 2 liblzo2-2 2 libopenal1 1: 2 libsvga1 1: 2 mplayer 2:1.0~rc3+ 2 gnome-mplayer 2 libc-bin

```

---


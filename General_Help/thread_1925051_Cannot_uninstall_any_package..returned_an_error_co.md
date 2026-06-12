---
title: "Cannot uninstall any package..returned an error code (1)"
date: 2012-02-13
forum: General Help
---

### Post by geosparovany2 on 2012-02-13
Hi all....First of all,sorry for my english...Everytime i update my packages i see this error


 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.6+7ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i tried to clean the broken packeges but i didnt succeed...these 2 packages are broken (x11-common && xorg)

as when i type 
$ sudo dpkg --configure -a

this message came to me...

dpkg: error processing x11-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on x11-common; however:
  Package x11-common is not configured yet.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 x11-common
 xorg

WHEN I TYPE THIS COMMAND
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 0 B/56.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 335493 files and directories currently installed.)
Preparing to replace x11-common 1:7.6+7ubuntu7 (using .../x11-common_1%3a7.6+7ubuntu7_i386.deb) ...
/etc/lsb-base-logging.sh: 3: NextSubscriptionId: not found
invoke-rc.d: initscript x11-common, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/etc/lsb-base-logging.sh: 3: NextSubscriptionId: not found
invoke-rc.d: initscript x11-common, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.6+7ubuntu7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              /etc/lsb-base-logging.sh: 3: NextSubscriptionId: not found
invoke-rc.d: initscript x11-common, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.6+7ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now i cannot uninstall any package and cannot upgrade some packages beacause of these 2 packages...any help plz?

---

### Post by Gremlinzzz on 2012-02-13
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

---

### Post by geosparovany2 on 2012-02-13
> **Gremlinzzz said:**
> sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

the same message came to me again :(

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0 B/56.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 335493 files and directories currently installed.)
Preparing to replace x11-common 1:7.6+7ubuntu7 (using .../x11-common_1%3a7.6+7ubuntu7_i386.deb) ...
/etc/lsb-base-logging.sh: 3: NextSubscriptionId: not found
invoke-rc.d: initscript x11-common, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/etc/lsb-base-logging.sh: 3: NextSubscriptionId: not found
invoke-rc.d: initscript x11-common, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.6+7ubuntu7_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              /etc/lsb-base-logging.sh: 3: NextSubscriptionId: not found
invoke-rc.d: initscript x11-common, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.6+7ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jerrrys on 2012-02-13
dpkg: error processing x11-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.

Did you do that?

---

### Post by Gremlinzzz on 2012-02-13
Did you try installing the packages togetter? if so try one at a time

---

### Post by Gremlinzzz on 2012-02-13
When i look for solutions i keep seeing go to install folder and manually remove the files/packages
[http://ubuntuforums.org/showthread.php?t=240699](http://ubuntuforums.org/showthread.php?t=240699)
don't think id try it

---

### Post by HiImTye on 2012-02-13
> Preparing to replace [COLOR=Red]x11-common[/COLOR] 1:7.6+7ubuntu7 (using .../x11-common_1%3a7.6+7ubuntu7_i386.deb) ...```
sudo apt-get remove --purge [COLOR=Red]x11-common[/COLOR]
```do this for whatever the other package is that it will complain about when you do another:
```
sudo apt-get install -f
```then reinstall them:
```
sudo apt-get install [COLOR=Red]x11-common[/COLOR] other-package-name
```

---

### Post by geosparovany2 on 2012-02-13
> **HiImTye said:**
> ```
sudo apt-get remove --purge [COLOR=Red]x11-common[/COLOR]
```do this for whatever the other package is that it will complain about when you do another:
```
sudo apt-get install -f
```then reinstall them:
```
sudo apt-get install [COLOR=Red]x11-common[/COLOR] other-package-name
```
[B]
If i remove x11-common, all these packages will be removed also...is it ok?...i am afraid that this will bring the system[/B] **down**

acpi-support* aisleriot* akonadi-server* akregator* amor* amule* appmenu-qt*
  aptoncd* apturl* ark* at-spi2-core* audacious* bamfdaemon* banshee*
  banshee-extension-soundmenu* blogilo* bomber* bovo* brasero* caja* cantor*
  caribou* cervisia* chmsee* chromium-browser* chromium-browser-l10n*
  chromium-codecs-ffmpeg* codeblocks* compiz* compiz-core* compiz-gnome*
  compiz-plugins-default* compiz-plugins-main-default*
  compizconfig-backend-gconf* cvsservice* dolphin* dragonplayer* dvipng*
  ekiga* empathy* epiphany-browser* epiphany-extensions* evince* evolution*
  evolution-data-server* evolution-plugins* filelight* firefox*
  firefox-globalmenu* firefox-gnome-support* freespacenotifier* gdm*
  gecko-mediaplayer* gedit* gedit-plugins* ghostscript-x* gimp* gimp-help-en*
  ginn* gir1.2-caribou-1.0* gir1.2-gkbd-3.0* gir1.2-mutter-3.0* gir1.2-rb-3.0*
  gir1.2-totem-1.0* gir1.2-webkit-3.0* gir1.2-wnck-3.0* glines* gnobots2*
  gnome* gnome-applets* gnome-contacts* gnome-control-center* gnome-core*
  gnome-games* gnome-media* gnome-mplayer* gnome-online-accounts* gnome-panel*
  gnome-screensaver* gnome-search-tool* gnome-session* gnome-session-bin*
  gnome-session-fallback* gnome-settings-daemon* gnome-shell*
  gnome-shell-extensions-common* gnome-shell-extensions-dock*
  gnome-shell-extensions-user-theme* gnome-shell-extensions-weather*
  gnome-sushi* gnome-system-monitor* gnome-terminal* gnome-tweak-tool*
  gnome-user-guide* gnome-web-photo* gnomine* gnotravex* gnotski* gnuplot*
  gnuplot-x11* goldendict* google-chrome-stable* graphviz* groff* gsfonts-x11*
  gspiceui* gthumb* gvfs* gvfs-backends* gvfs-bin* gvfs-fuse* gwenview*
  hamster-applet* hotot* iagno* indicator-appmenu* indicator-datetime*
  indicator-power* indicator-session* indicator-sound* inxi* jovie* juk* k3b*
  kaccessible* kaddressbook* kajongg* kalarm* kalgebra* kalgebra-common*
  kalzium* kamera* kanagram* kapman* kapptemplate* kate* katepart* katomic*
  kbattleship* kblackbox* kblocks* kbounce* kbreakout* kbruch* kcachegrind*
  kcalc* kcharselect* kcolorchooser* kde-baseapps* kde-baseapps-bin*
  kde-config-cddb* kde-config-cron* kde-full* kde-plasma-desktop*
  kde-plasma-netbook* kde-runtime* kde-standard* kde-window-manager*
  kde-workspace* kde-workspace-bin* kde-workspace-kgreet-plugins*
  kdeaccessibility* kdeadmin* kdeartwork* kdeartwork-style*
  kdeartwork-theme-window* kdebase-runtime* kdeedu* kdegames* kdegraphics*
  kdegraphics-mobipocket* kdegraphics-thumbnailers* kdelibs-bin*
  kdelibs5-plugins* kdemultimedia* kdemultimedia-kio-plugins* kdenetwork*
  kdenetwork-filesharing* kdepasswd* kdepim* kdepim-groupware*
  kdepim-kresources* kdepim-runtime* kdepim-strigi-plugins* kdepim-wizards*
  kdepimlibs-kio-plugins* kdeplasma-addons* kdesdk* kdesdk-dolphin-plugins*
  kdesdk-kio-plugins* kdesdk-misc* kdetoys* kdeutils* kdewebdev* kdf*
  kdiamond* kdm* kdoctools* kfilereplace* kfind* kfourinline* kgamma*
  kgeography* kget* kgoldrunner* kgpg* khangman* khelpcenter4* kig* kigo*
  killbots* kimagemapeditor* kinfocenter* kiriki* kjots* kjumpingcube*
  klettres* klickety* klines* klinkstatus* klipper* kmag* kmahjongg* kmail*
  kmines* kmix* kmousetool* kmouth* kmplot* kmtrace* knetwalk* knode* knotes*
  kolf* kollision* kolourpaint4* kommander* kompare* konq-plugins* konqueror*
  konqueror-nsplugins* konquest* konsolekalendar* kontact* kopete*
  kopete-message-indicator* korganizer* kpartloader* kpat* kppp* krdc*
  kremotecontrol* kreversi* krfb* krosspython* kruler* ksaneplugin* kscd*
  kscreensaver* kscreensaver-xsavers* kshisen* ksirk* ksnapshot* kspaceduel*
  ksquares* kstars* ksudoku* ksysguard* ksystemlog* kteatime* ktimer*
  ktimetracker* ktouch* ktron* ktuberling* kturtle* ktux* kubrick*
  kubuntu-debug-installer* kuiviewer* kuser* kwalletmanager* kwordquiz*
  latex-beamer* latex-xcolor* libakonadi-calendar4* libakonadi-contact4*
  libakonadi-kcal4* libakonadi-kde4* libakonadi-kmime4* libaudio2*
  libavogadro1* libbamf0* libbamf3-0* libbonoboui2-0* libcairo2-dev*
  libcalendarsupport4* libcanberra-pulse* libcaribou0* libcodeblocks0*
  libcompizconfig0* libcompoundviewer4* libdbusmenu-qt2* libdconf-qt0*
  libeventviews4* libevolution* libgail-dev* libgnome2-perl*
  libgnome2-wnck-perl* libgnomekbd7* libgnomeui-0* libgoa-1.0-0*
  libgrantlee-gui0* libgtk2.0-dev* libice-dev* libice6*
  libincidenceeditorsng4* libindicate-qt1* libk3b6* libkabc4*
  libkastencontrollers4* libkastencore4* libkastengui4* libkateinterfaces4*
  libkatepartinterfaces4* libkblog4* libkcal4* libkcalcore4* libkcalutils4*
  libkcddb4* libkcmutils4* libkdcraw20* libkde3support4* libkdecorations4*
  libkdegames5a* libkdepim4* libkdepimdbusinterfaces4* libkdeui5*
  libkdewebkit5* libkdgantt2* libkdnssd4* libkeduvocdocument4* libkemoticons4*
  libkephal4abi1* libkexiv2-10* libkfile4* libkggzgames4* libkholidays4*
  libkhtml5* libkidletime4* libkio5* libkipi8* libkjsembed4* libkldap4*
  libkleo4* libkmahjongglib4* libkmanagesieve4* libkmediaplayer4*
  libknewstuff2-4* libknewstuff3-4* libknotifyconfig4* libkonq-common*
  libkonq5abi1* libkonqsidebarplugin4a* libkontactinterface4* libkopete4*
  libkparts4* libkpgp4* libkpimidentities4* libkpimtextedit4* libkpimutils4*
  libkprintutils4* libkresources4* libkrosscore4* libkrossui4* libksane0*
  libkscreensaver5* libksieveui4* libksignalplotter4* libktexteditor4*
  libktnef4* libktorrent3* libkunitconversion4* libkwineffects1abi2*
  libkworkspace4* libkxmlrpcclient4* liblightdm-gobject-1-0* libmailcommon4*
  libmailtransport4* libmarblewidget12* libmate* libmatecanvas*
  libmatecomponentui* libmatekbd* libmatepanelapplet* libmateui*
  libmessagecomposer4* libmessagecore4* libmessagelist4* libmessageviewer4*
  libmicroblog4* libmutter0* libnepomuk4* libnepomukquery4a* libnepomukutils4*
  liboktetagui4* liboktetakastencontrollers4* liboktetakastencore4*
  liboktetakastengui4* libokularcore1* libpango1.0-dev* libphonon4*
  libplasma3* libplasmaclock4abi2* libplasmagenericshell4* libpolkit-qt-1-1*
  libpoppler-qt4-3* libprison0* libprocessui4a* libqapt-runtime*
  libqimageblitz4* libqt4-declarative* libqt4-designer* libqt4-help*
  libqt4-opengl* libqt4-qt3support* libqt4-scripttools* libqt4-svg*
  libqtbamf1* libqtdee2* libqtgconf1* libqtgui4* libqtwebkit4*
  libreoffice-base* libreoffice-base-core* libreoffice-calc*
  libreoffice-common* libreoffice-core* libreoffice-draw*
  libreoffice-emailmerge* libreoffice-gnome* libreoffice-gtk*
  libreoffice-help-en-gb* libreoffice-help-en-us* libreoffice-impress*
  libreoffice-java-common* libreoffice-l10n-ar* libreoffice-l10n-en-gb*
  libreoffice-l10n-en-za* libreoffice-math* libreoffice-style-tango*
  libreoffice-writer* librhythmbox-core4* libscience4* libseed-gtk3-0*
  libsm-dev* libsm6* libsolid4* libsolidcontrol4abi2* libsyndication4*
  libtaskmanager4abi2* libtemplateparser4* libthunarx-2-0* libtotem0*
  libweather-ion6* libwebkitgtk-1.0-0* libwebkitgtk-3.0-0* libwnck-3-0*
  libwnck22* libwxgtk2.8-0* libxaw7* libxfce4ui-1-0* libxine1* libxine1-x*
  libxklavier16* libxmu6* libxres1* libxss1* libxt6* libxtst6* libxvmc1*
  libxxf86dga1* libyelp0* liferea* lmodern* lokalize* lskat* lyx* marble*
  marble-plugins* mate-control-center* mate-file-manager* mate-keyring*
  mate-media* mate-notification-daemon* mate-panel* mate-session-manager*
  mate-settings-daemon* mate-terminal* mate-utils* mate-vfs*
  mate-window-manager* me-tv* metacity* mint-meta-codecs* mint-meta-core*
  mint-meta-gnome* mint-meta-gnome-dvd* mint-meta-mate* mint-meta-mgse*
  mintdesktop* mintinstall* mintmenu* mintnanny* mintwelcome* miro*
  mountmanager* mousetweaks* mplayer* mutter* mythes-en-au* mythes-en-us*
  nautilus* nautilus-sendto* nautilus-sendto-empathy* nautilus-share*
  notify-osd* okteta* okular* openoffice.org-common* orage* palapeli* parley*
  pgf* phonon* phonon-backend-gstreamer* pidgin* pinentry-qt4*
  plasma-containments-addons* plasma-dataengines-addons*
  plasma-dataengines-workspace* plasma-desktop* plasma-netbook*
  plasma-runners-addons* plasma-scriptengine-javascript*
  plasma-scriptengine-superkaramba* plasma-wallpapers-addons*
  plasma-widget-folderview* plasma-widget-lancelot*
  plasma-widget-message-indicator* plasma-widget-networkmanagement*
  plasma-widgets-addons* plasma-widgets-workspace* polkit-kde-1*
  printer-applet* prosper* pulseaudio* pulseaudio-esound-compat*
  pulseaudio-module-bluetooth* pulseaudio-module-gconf* pulseaudio-module-x11*
  pulseaudio-utils* python-avogadro* python-compizconfig* python-gnome2*
  python-kde4* python-mate* python-qt4* python-qt4-sql* python-uno*
  python-virtkey* python-webkit* python-wnck* qapt-batch* qbittorrent*
  qt-at-spi* qtoctave* rhythmbox* rhythmbox-plugin-cdrecorder*
  rhythmbox-plugins* rocs* screenlets* screenlets-pack-all*
  shiki-colors-metacity-theme* shiki-wise-theme* shotwell* shutter* skype*
  smplayer* smplayer-themes* smplayer-translations* sni-qt* step*
  sun-java6-plugin* svgpart* sweeper* system-config-printer-kde*
  systemsettings* texlive-base* texlive-binaries* texlive-extra-utils*
  texlive-font-utils* texlive-fonts-recommended* texlive-generic-extra*
  texlive-generic-recommended* texlive-latex-base* texlive-latex-extra*
  texlive-latex-recommended* texlive-luatex* texlive-pictures*
  texlive-pstricks* texlive-science* thunar* thunar-volman* thunderbird*
  thunderbird-globalmenu* thunderbird-gnome-support* thunderbird-locale-ar*
  thunderbird-locale-en* thunderbird-locale-en-gb* thunderbird-locale-en-us*
  tipa* totem* totem-mozilla* totem-plugins* totem-plugins-extra*
  ttf-mscorefonts-installer* ubuntu-tweak* umbrello* unetbootin* unity*
  unity-greeter* vino* virtualbox-4.1* vlc* wine1.3* winetricks*
  x-ttcidfont-conf* x11-apps* x11-common* x11-session-utils* x11-utils*
  x11-xkb-utils* x11-xserver-utils* xfce4* xfce4-appfinder* xfce4-mixer*
  xfce4-panel* xfce4-session* xfce4-settings* xfce4-utils* xfdesktop4*
  xfonts-base* xfonts-encodings* xfonts-mathml* xfonts-scalable*
  xfonts-terminus* xfonts-utils* xfwm4* xfwm4-themes* xinit* xorg* xplanet*
  xscreensaver* xscreensaver-data* xscreensaver-gl* xserver-common*
  xserver-xorg* xserver-xorg-core* xserver-xorg-input-all*
  xserver-xorg-input-evdev* xserver-xorg-input-mouse*
  xserver-xorg-input-synaptics* xserver-xorg-input-vmmouse*
  xserver-xorg-input-wacom* xserver-xorg-video-all* xserver-xorg-video-ati*
  xserver-xorg-video-cirrus* xserver-xorg-video-fbdev*
  xserver-xorg-video-geode* xserver-xorg-video-intel*
  xserver-xorg-video-mach64* xserver-xorg-video-mga*
  xserver-xorg-video-neomagic* xserver-xorg-video-nouveau*
  xserver-xorg-video-openchrome* xserver-xorg-video-qxl*
  xserver-xorg-video-r128* xserver-xorg-video-radeon* xserver-xorg-video-s3*
  xserver-xorg-video-savage* xserver-xorg-video-siliconmotion*
  xserver-xorg-video-sis* xserver-xorg-video-sisusb* xserver-xorg-video-tdfx*
  xserver-xorg-video-trident* xserver-xorg-video-vesa*

---

### Post by Gremlinzzz on 2012-02-14
sudo apt-get install <package> --reinstall


Synaptic Package Manager has reinstall so i thought it would be worth a shot

---

### Post by HiImTye on 2012-02-14
> **geosparovany2 said:**
> [B]
If i remove x11-common, all these packages will be removed also...is it ok?...i am afraid that this will bring the system[/B] **down**

acpi-support* aisleriot* akonadi-server* akregator* amor* amule* appmenu-qt*
  aptoncd* apturl* ark* at-spi2-core* audacious* bamfdaemon* banshee*
  banshee-extension-soundmenu* blogilo* bomber* bovo* brasero* caja* cantor*
  caribou* cervisia* chmsee* chromium-browser* chromium-browser-l10n*
  chromium-codecs-ffmpeg* codeblocks* compiz* compiz-core* compiz-gnome*
  compiz-plugins-default* compiz-plugins-main-default*
  compizconfig-backend-gconf* cvsservice* dolphin* dragonplayer* dvipng*
  ekiga* empathy* epiphany-browser* epiphany-extensions* evince* evolution*
  evolution-data-server* evolution-plugins* filelight* firefox*
  firefox-globalmenu* firefox-gnome-support* freespacenotifier* gdm*
  gecko-mediaplayer* gedit* gedit-plugins* ghostscript-x* gimp* gimp-help-en*
  ginn* gir1.2-caribou-1.0* gir1.2-gkbd-3.0* gir1.2-mutter-3.0* gir1.2-rb-3.0*
  gir1.2-totem-1.0* gir1.2-webkit-3.0* gir1.2-wnck-3.0* glines* gnobots2*
  gnome* gnome-applets* gnome-contacts* gnome-control-center* gnome-core*
  gnome-games* gnome-media* gnome-mplayer* gnome-online-accounts* gnome-panel*
  gnome-screensaver* gnome-search-tool* gnome-session* gnome-session-bin*
  gnome-session-fallback* gnome-settings-daemon* gnome-shell*
  gnome-shell-extensions-common* gnome-shell-extensions-dock*
  gnome-shell-extensions-user-theme* gnome-shell-extensions-weather*
  gnome-sushi* gnome-system-monitor* gnome-terminal* gnome-tweak-tool*
  gnome-user-guide* gnome-web-photo* gnomine* gnotravex* gnotski* gnuplot*
  gnuplot-x11* goldendict* google-chrome-stable* graphviz* groff* gsfonts-x11*
  gspiceui* gthumb* gvfs* gvfs-backends* gvfs-bin* gvfs-fuse* gwenview*
  hamster-applet* hotot* iagno* indicator-appmenu* indicator-datetime*
  indicator-power* indicator-session* indicator-sound* inxi* jovie* juk* k3b*
  kaccessible* kaddressbook* kajongg* kalarm* kalgebra* kalgebra-common*
  kalzium* kamera* kanagram* kapman* kapptemplate* kate* katepart* katomic*
  kbattleship* kblackbox* kblocks* kbounce* kbreakout* kbruch* kcachegrind*
  kcalc* kcharselect* kcolorchooser* kde-baseapps* kde-baseapps-bin*
  kde-config-cddb* kde-config-cron* kde-full* kde-plasma-desktop*
  kde-plasma-netbook* kde-runtime* kde-standard* kde-window-manager*
  kde-workspace* kde-workspace-bin* kde-workspace-kgreet-plugins*
  kdeaccessibility* kdeadmin* kdeartwork* kdeartwork-style*
  kdeartwork-theme-window* kdebase-runtime* kdeedu* kdegames* kdegraphics*
  kdegraphics-mobipocket* kdegraphics-thumbnailers* kdelibs-bin*
  kdelibs5-plugins* kdemultimedia* kdemultimedia-kio-plugins* kdenetwork*
  kdenetwork-filesharing* kdepasswd* kdepim* kdepim-groupware*
  kdepim-kresources* kdepim-runtime* kdepim-strigi-plugins* kdepim-wizards*
  kdepimlibs-kio-plugins* kdeplasma-addons* kdesdk* kdesdk-dolphin-plugins*
  kdesdk-kio-plugins* kdesdk-misc* kdetoys* kdeutils* kdewebdev* kdf*
  kdiamond* kdm* kdoctools* kfilereplace* kfind* kfourinline* kgamma*
  kgeography* kget* kgoldrunner* kgpg* khangman* khelpcenter4* kig* kigo*
  killbots* kimagemapeditor* kinfocenter* kiriki* kjots* kjumpingcube*
  klettres* klickety* klines* klinkstatus* klipper* kmag* kmahjongg* kmail*
  kmines* kmix* kmousetool* kmouth* kmplot* kmtrace* knetwalk* knode* knotes*
  kolf* kollision* kolourpaint4* kommander* kompare* konq-plugins* konqueror*
  konqueror-nsplugins* konquest* konsolekalendar* kontact* kopete*
  kopete-message-indicator* korganizer* kpartloader* kpat* kppp* krdc*
  kremotecontrol* kreversi* krfb* krosspython* kruler* ksaneplugin* kscd*
  kscreensaver* kscreensaver-xsavers* kshisen* ksirk* ksnapshot* kspaceduel*
  ksquares* kstars* ksudoku* ksysguard* ksystemlog* kteatime* ktimer*
  ktimetracker* ktouch* ktron* ktuberling* kturtle* ktux* kubrick*
  kubuntu-debug-installer* kuiviewer* kuser* kwalletmanager* kwordquiz*
  latex-beamer* latex-xcolor* libakonadi-calendar4* libakonadi-contact4*
  libakonadi-kcal4* libakonadi-kde4* libakonadi-kmime4* libaudio2*
  libavogadro1* libbamf0* libbamf3-0* libbonoboui2-0* libcairo2-dev*
  libcalendarsupport4* libcanberra-pulse* libcaribou0* libcodeblocks0*
  libcompizconfig0* libcompoundviewer4* libdbusmenu-qt2* libdconf-qt0*
  libeventviews4* libevolution* libgail-dev* libgnome2-perl*
  libgnome2-wnck-perl* libgnomekbd7* libgnomeui-0* libgoa-1.0-0*
  libgrantlee-gui0* libgtk2.0-dev* libice-dev* libice6*
  libincidenceeditorsng4* libindicate-qt1* libk3b6* libkabc4*
  libkastencontrollers4* libkastencore4* libkastengui4* libkateinterfaces4*
  libkatepartinterfaces4* libkblog4* libkcal4* libkcalcore4* libkcalutils4*
  libkcddb4* libkcmutils4* libkdcraw20* libkde3support4* libkdecorations4*
  libkdegames5a* libkdepim4* libkdepimdbusinterfaces4* libkdeui5*
  libkdewebkit5* libkdgantt2* libkdnssd4* libkeduvocdocument4* libkemoticons4*
  libkephal4abi1* libkexiv2-10* libkfile4* libkggzgames4* libkholidays4*
  libkhtml5* libkidletime4* libkio5* libkipi8* libkjsembed4* libkldap4*
  libkleo4* libkmahjongglib4* libkmanagesieve4* libkmediaplayer4*
  libknewstuff2-4* libknewstuff3-4* libknotifyconfig4* libkonq-common*
  libkonq5abi1* libkonqsidebarplugin4a* libkontactinterface4* libkopete4*
  libkparts4* libkpgp4* libkpimidentities4* libkpimtextedit4* libkpimutils4*
  libkprintutils4* libkresources4* libkrosscore4* libkrossui4* libksane0*
  libkscreensaver5* libksieveui4* libksignalplotter4* libktexteditor4*
  libktnef4* libktorrent3* libkunitconversion4* libkwineffects1abi2*
  libkworkspace4* libkxmlrpcclient4* liblightdm-gobject-1-0* libmailcommon4*
  libmailtransport4* libmarblewidget12* libmate* libmatecanvas*
  libmatecomponentui* libmatekbd* libmatepanelapplet* libmateui*
  libmessagecomposer4* libmessagecore4* libmessagelist4* libmessageviewer4*
  libmicroblog4* libmutter0* libnepomuk4* libnepomukquery4a* libnepomukutils4*
  liboktetagui4* liboktetakastencontrollers4* liboktetakastencore4*
  liboktetakastengui4* libokularcore1* libpango1.0-dev* libphonon4*
  libplasma3* libplasmaclock4abi2* libplasmagenericshell4* libpolkit-qt-1-1*
  libpoppler-qt4-3* libprison0* libprocessui4a* libqapt-runtime*
  libqimageblitz4* libqt4-declarative* libqt4-designer* libqt4-help*
  libqt4-opengl* libqt4-qt3support* libqt4-scripttools* libqt4-svg*
  libqtbamf1* libqtdee2* libqtgconf1* libqtgui4* libqtwebkit4*
  libreoffice-base* libreoffice-base-core* libreoffice-calc*
  libreoffice-common* libreoffice-core* libreoffice-draw*
  libreoffice-emailmerge* libreoffice-gnome* libreoffice-gtk*
  libreoffice-help-en-gb* libreoffice-help-en-us* libreoffice-impress*
  libreoffice-java-common* libreoffice-l10n-ar* libreoffice-l10n-en-gb*
  libreoffice-l10n-en-za* libreoffice-math* libreoffice-style-tango*
  libreoffice-writer* librhythmbox-core4* libscience4* libseed-gtk3-0*
  libsm-dev* libsm6* libsolid4* libsolidcontrol4abi2* libsyndication4*
  libtaskmanager4abi2* libtemplateparser4* libthunarx-2-0* libtotem0*
  libweather-ion6* libwebkitgtk-1.0-0* libwebkitgtk-3.0-0* libwnck-3-0*
  libwnck22* libwxgtk2.8-0* libxaw7* libxfce4ui-1-0* libxine1* libxine1-x*
  libxklavier16* libxmu6* libxres1* libxss1* libxt6* libxtst6* libxvmc1*
  libxxf86dga1* libyelp0* liferea* lmodern* lokalize* lskat* lyx* marble*
  marble-plugins* mate-control-center* mate-file-manager* mate-keyring*
  mate-media* mate-notification-daemon* mate-panel* mate-session-manager*
  mate-settings-daemon* mate-terminal* mate-utils* mate-vfs*
  mate-window-manager* me-tv* metacity* mint-meta-codecs* mint-meta-core*
  mint-meta-gnome* mint-meta-gnome-dvd* mint-meta-mate* mint-meta-mgse*
  mintdesktop* mintinstall* mintmenu* mintnanny* mintwelcome* miro*
  mountmanager* mousetweaks* mplayer* mutter* mythes-en-au* mythes-en-us*
  nautilus* nautilus-sendto* nautilus-sendto-empathy* nautilus-share*
  notify-osd* okteta* okular* openoffice.org-common* orage* palapeli* parley*
  pgf* phonon* phonon-backend-gstreamer* pidgin* pinentry-qt4*
  plasma-containments-addons* plasma-dataengines-addons*
  plasma-dataengines-workspace* plasma-desktop* plasma-netbook*
  plasma-runners-addons* plasma-scriptengine-javascript*
  plasma-scriptengine-superkaramba* plasma-wallpapers-addons*
  plasma-widget-folderview* plasma-widget-lancelot*
  plasma-widget-message-indicator* plasma-widget-networkmanagement*
  plasma-widgets-addons* plasma-widgets-workspace* polkit-kde-1*
  printer-applet* prosper* pulseaudio* pulseaudio-esound-compat*
  pulseaudio-module-bluetooth* pulseaudio-module-gconf* pulseaudio-module-x11*
  pulseaudio-utils* python-avogadro* python-compizconfig* python-gnome2*
  python-kde4* python-mate* python-qt4* python-qt4-sql* python-uno*
  python-virtkey* python-webkit* python-wnck* qapt-batch* qbittorrent*
  qt-at-spi* qtoctave* rhythmbox* rhythmbox-plugin-cdrecorder*
  rhythmbox-plugins* rocs* screenlets* screenlets-pack-all*
  shiki-colors-metacity-theme* shiki-wise-theme* shotwell* shutter* skype*
  smplayer* smplayer-themes* smplayer-translations* sni-qt* step*
  sun-java6-plugin* svgpart* sweeper* system-config-printer-kde*
  systemsettings* texlive-base* texlive-binaries* texlive-extra-utils*
  texlive-font-utils* texlive-fonts-recommended* texlive-generic-extra*
  texlive-generic-recommended* texlive-latex-base* texlive-latex-extra*
  texlive-latex-recommended* texlive-luatex* texlive-pictures*
  texlive-pstricks* texlive-science* thunar* thunar-volman* thunderbird*
  thunderbird-globalmenu* thunderbird-gnome-support* thunderbird-locale-ar*
  thunderbird-locale-en* thunderbird-locale-en-gb* thunderbird-locale-en-us*
  tipa* totem* totem-mozilla* totem-plugins* totem-plugins-extra*
  ttf-mscorefonts-installer* ubuntu-tweak* umbrello* unetbootin* unity*
  unity-greeter* vino* virtualbox-4.1* vlc* wine1.3* winetricks*
  x-ttcidfont-conf* x11-apps* x11-common* x11-session-utils* x11-utils*
  x11-xkb-utils* x11-xserver-utils* xfce4* xfce4-appfinder* xfce4-mixer*
  xfce4-panel* xfce4-session* xfce4-settings* xfce4-utils* xfdesktop4*
  xfonts-base* xfonts-encodings* xfonts-mathml* xfonts-scalable*
  xfonts-terminus* xfonts-utils* xfwm4* xfwm4-themes* xinit* xorg* xplanet*
  xscreensaver* xscreensaver-data* xscreensaver-gl* xserver-common*
  xserver-xorg* xserver-xorg-core* xserver-xorg-input-all*
  xserver-xorg-input-evdev* xserver-xorg-input-mouse*
  xserver-xorg-input-synaptics* xserver-xorg-input-vmmouse*
  xserver-xorg-input-wacom* xserver-xorg-video-all* xserver-xorg-video-ati*
  xserver-xorg-video-cirrus* xserver-xorg-video-fbdev*
  xserver-xorg-video-geode* xserver-xorg-video-intel*
  xserver-xorg-video-mach64* xserver-xorg-video-mga*
  xserver-xorg-video-neomagic* xserver-xorg-video-nouveau*
  xserver-xorg-video-openchrome* xserver-xorg-video-qxl*
  xserver-xorg-video-r128* xserver-xorg-video-radeon* xserver-xorg-video-s3*
  xserver-xorg-video-savage* xserver-xorg-video-siliconmotion*
  xserver-xorg-video-sis* xserver-xorg-video-sisusb* xserver-xorg-video-tdfx*
  xserver-xorg-video-trident* xserver-xorg-video-vesa*
that is problematic, I would try Gremlinz' option

---


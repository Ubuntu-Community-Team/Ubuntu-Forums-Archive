---
title: "Cannot use Unity or Gnome desktops in Oneiric x86_64"
date: 2011-11-02
forum: General Help
---

### Post by cscj01 on 2011-11-02
I can only run Gnome Classic desktops.  If I choose anything other than Gnome Classic or Gnome Classic (no effects) at login, the menus never build.  I have waited quite a while for them to build, but they never do.  I have to do a hard Power Off to get out of it.  Any ideas?  Thanks.

---

### Post by Mark Phelps on 2011-11-03
What do you mean "the menus never build".  There are no menus to speak of in Unity (except for the top bar, when you click on items on the right). In 11.10, they removed the former Main Menu app.  So, if you're looking for that, it's not there anymore.

So, when you click on the Dash icon on the top-left of the screen, do you not get a new panel on the desktop?

---

### Post by kurt18947 on 2011-11-03
You could try tapping the left super/windows key or move the mouse cursor to the left monitor edge and see if anything appears.  As Marks said, the screen is pretty spartan when either Ubuntu or gnome 3 shell first load. The other possibility is that you need to install proprietary video drivers or your video system is simply not up to the task.  Gnome-classic or gnome-classic no effects are included in 11.10 in part to accommodate lower powered graphics systems.

---

### Post by vicshrike on 2011-11-03
What kind of computer is it?

---

### Post by cscj01 on 2011-11-03
Okay, I'll try to be a little clearer.  After I login, some things happen in Gnome 3 and in Unity.  But the system seems to hang in both instances before any thing of much use is displayed on the screen.

First, Unity:  If I login into Unity (Ubuntu as my choice), I have a background and a vertical stack of icons on the left side of my desktop.  This stack of icons is incomplete however, as the bottom of the stack shows partial icons.  At this point, I can move the cursor, but I cannot cause any actions to occur with the mouse or keyboard.  That is, if I click on any thing (right or left click), nothing happens.  If I move my cursor to any position on the screen, nothing happens.  I have left the desktop in this state for thirty plus minutes and I can get nothing to happen.  I have tried many combinations of keys (shortcuts), but nothing happens.

Secondly, Gnome 3:  If I login to Gnome 3 (Gnome as my choice), I get a panel at the top of my screen.  The word Applications is on the left side and there are icons in the middle and on the right of this panel.  Once again, at this point, I can get no response to mouse movement or clicks (right or left) or to keyboard presses (either single keys or combinations).  I have tried everything I can think of, but nothing happens.

As I said in my original post, I have to do a hard power off (press the power button on my PC and hold it until the machine shuts down) to get out of either environment.

Here's a little more information.  I upgraded from 11.04 to 11.10.  Gnome Classic (no effects) was my desktop in 11.04 because I couldn't get Unity to work then.  When I upgraded, gnome-session-fallbackup was installed.  I have read for people to use the Gnome Classic desktop, they had to install this after the fact.  It was there for me after upgrade.  After the upgrade, I re-booted and hit enter at login.  Since the default desktop was Unity, I got what I described earlier .  When I re-booted, I tried Gnome.  Again, I got what I described earlier.  Finally, I chose Gnome Classic, and things worked.

I have a Dell XPS 410 with 6GB of memory with an on-board Nvidia GEForce 7300 LE graphics controller and a dual-core pentium E6600 @ 2.4 GHz x 2.  My monitor is a Viewsonic VX2250 and I have two Western Digital Black drives; one 500 GB and a second with 1.5 TB capacity.  I have 2 DVD burners, a Sony and a Samsung.  My Video driver is the > Nvidia accelerated graphics driver (version current) [Recommended]

I hope this clears things up so someone can suggest something to fix my situation.  I know and like Gnome Classic, but I would like to try the other two environments.

---

### Post by Mark Phelps on 2011-11-03
Sorry, don't have a fix -- but do have a similar story ...

Installed 11.10 this weekend, spent two days doing customizing.  Somewhere along the line, mouse clicks stopped working (kind of like with you).  I could right-click and left-click, but I could not click on a window and drag it, and when I clicked on the top panel, that would not always work.

Figuring the batteries in my cordless mouse were too low, I replaced them -- no better.

So, I plugged it an old wired USB mouse and used it.  Figured my mouse had gone bad.

Borrowed the same mouse from another PC (like this mouse!) -- and it worked OK!  Did some more work.

Restarted 11.10, now the NEW borrowed mouse no longer worked.

SIGH ...

Plugged in the wired USB mouse, it worked OK.

Restarted 11.10 again (was making changes that required rebooting), NOW, the wired USB mouse no longer worked right!

Not only that, but the wired USB keyboard was acting up as well now.

Replaced the keyboard with an older, simpler model (have a gaming keyboard that I like), rebooted -- now OK.

Unplugged the wired USB mouse, rebooted. Cordless mouse then worked OK -- both of them.

Been four days now, and with the older keyboard in place, ALL the mice now work OK.

And, before you ask, I connected the (apparently) not working new USB keyboard to another PC -- and it works fine.

I have been using the gaming keyboard for years without problems, and have been using the cordless mouse for nearly two years, without problems -- until I installed 11.10.

---

### Post by cscj01 on 2011-11-04
bump

---

### Post by edwford on 2011-11-04
I too am having a similar issue under slightly different circumstances. I am running an old macbook with intel gma graphics and 2.16 ghz 3gb ram. I got gnome-shell installed, and fiddled around with it (custom themes/extensions), everything was working fine (including gnome-fallback and unity). Then I installed kubuntu-full. I decided it wasn't for me, mainly due to a lack of time to customise it to meet my needs. I then attempted to remove kubuntu through ubuntu software centre by uninstalling the parts tagged with "kubuntu-" at the beginning. Then proceeded to use some code from psychocats.net to remove kubuntu and rid my computer of it. ```
sudo apt-get remove akonadi-backend-mysql akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark bluedevil cdparanoia cdrdao docbook-xsl dolphin dragonplayer freespacenotifier gnupg-agent gnupg2 gpgsm gstreamer0.10-qapt gtk2-engines-oxygen gwenview ibus-qt4 icoutils jockey-kde k3b k3b-data kaccessible kaddressbook kamera kate kate-data katepart kcalc kde-baseapps-bin kde-baseapps-data kde-config-gtk kde-config-touchpad kde-runtime kde-runtime-data kde-wallpapers-default kde-window-manager kde-workspace kde-workspace-bin kde-workspace-data kde-workspace-kgreet-plugins kde-zeroconf kdebase-runtime kdegames-card-data kdegraphics-strigi-analyzer kdelibs-bin kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knotes konsole kontact kopete kopete-message-indicator korganizer kpat kppp ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-netbook-default-settings kubuntu-notification-helper kubuntu-web-shortcuts kvkbd kwalletmanager language-selector-kde libakonadi-calendar4 libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprotocolinternals1 libassuan0 libattica0 libbluedevil1 libboost-program-options1.46.1 libcalendarsupport4 libcln6 libclucene0ldbl libdebconf-kde0 libdiscid0 libdlrestrictions1 libdmtx0a libencode-locale-perl libepub0 libeventviews4 libfile-listing-perl libflac++6 libfont-afm-perl libgadu3 libgpgme++2 libgps19 libgrantlee-core0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libibus-qt1 libilmbase6 libincidenceeditorsng4 libindicate-qt1 libio-socket-ssl-perl libiodbc2 libk3b6 libkabc4 libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkde3support4 libkdecorations4 libkdecore5 libkdegames5a libkdepim4 libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2 libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-10 libkexiv2-data libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5 libkipi-data libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common libkonq5-templates libkonq5abi1 libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libksba8 libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent3 libkunitconversion4 libkwineffects1abi2 libkworkspace4 libkxmlrpcclient4 liblastfm0 libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmailcommon4 libmailtools-perl libmailtransport4 libmessagecomposer4 libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libmpcdec6 libmsn0.3 libmuonprivate1 libmusicbrainz3-6 libnepomuk4 libnepomukquery4a libnepomukutils4 libnet-http-perl libnet-ssleay-perl libntrack-qt4-1 libntrack0 libokularcore1 libopenexr6 libotr2 libphonon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi2 libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3 libprison0 libprocesscore4abi1 libprocessui4a libqalculate5 libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0 libqrencode3 libqt4-designer libqt4-help libqt4-qt3support libqt4-scripttools libqt4-sql-sqlite libqt4-test libqtassistantclient4 libqtglib-2.0-0 libqtgstreamer-0.10-0 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libqtwebkit4 libreoffice-kde libreoffice-style-oxygen libsolid4 libsolidcontrol4abi2 libsolidcontrolifaces4abi2 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1 libtaskmanager4abi2 libtemplateparser4 libthreadweaver4 libtimedate-perl liburi-perl libvirtodbc0 libweather-ion6 libwww-perl libwww-robotrules-perl libxml2-utils libxss1 libzip1 muon muon-installer muon-notifier muon-updater mysql-client-core-5.1 mysql-server-core-5.1 ntrack-module-libnl-0 odbcinst odbcinst1debian2 okular okular-extra-backends oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete partitionmanager phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text printer-applet python-kde4 python-pyudev python-qt4 python-qt4-dbus python-sip qapt-batch qapt-deb-installer quassel quassel-data rekonq shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings update-manager-kde usb-creator-kde userconfig virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common && sudo apt-get install ubuntu-desktop 
```
Now the gnome-shell won't load. I managed to make unity work by typing the following into the terminal ```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```
I also only have the top left workspace available on unity's "Workspaces" (despite ccsm saying I have 4 in a 2x2 formation). I've tried reinstalling compiz gnome-shell gnome-fallback and a fair few other things via synaptic to no avail. My unity login has adopted the themes I used in my gnome-shell login. I'm considering making a backup of my home folder and reinstalling my OS from scratch. Though I don't have a cd and couldn't get ubuntu-gnome-shell-remix to boot from USB (after making it on my OSX partition as per ubuntus install via usb on a mac instructions)

---

### Post by cscj01 on 2011-11-10
I was able to bring up Gnome 3 2D and Gnome 3 by running Compiz Configurations Setting Manager, choosing Preferences, the Plugin List tab, un-checking Automatic plugin sorting, and moving unityshell from the disabled list to the enabled list.  However, I had many instances when the system would lockup doing some task or running some program.  I finally became frustrated with it and went back to Gnome Classic.  I did not try Unity.  I may do that later.  I suppose I can mark this thread as solved since I can now log into those environments.

---


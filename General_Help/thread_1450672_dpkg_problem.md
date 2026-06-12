---
title: "dpkg problem"
date: 2010-04-09
forum: General Help
---

### Post by dragoi on 2010-04-09
Hi, I am using Ubuntu 9.04 and yesterday I deleted the dpkg file from /usr/bin/ and now I cant seem to find it anywhere to download it from, probably need to get it from someone that's using the same version of ubuntu, but I dont know someone using it.

The problem is that I get this error when using the command "apt-get -f install": E: Sub-process /usr/bin/dpkg returned an error code (100)

---

### Post by sisco311 on 2010-04-09
please post the output of:
```
ls -al /var/cache/apt/archives/dpkg*
```
and
```
uname -a
```

---

### Post by dragoi on 2010-04-09
What appears after the 19:32 is with red.

```
-rw-r--r-- 1 root root 2172196 2010-01-08 19:32 /var/cache/apt/archives/dpkg_1.15.5.6_i386.deb
-rw-r--r-- 1 root root  765234 2010-01-08 19:32 /var/cache/apt/archives/dpkg-dev_1.15.5.6_all.deb
```

and

```
Linux [blabla].kimsufi.com 2.6.31.5-grsec-xxxx-grs-ipv4-32 #2 SMP Thu Nov 5 12:35:58 UTC 2009 i686 GNU/Linux
```

---

### Post by sisco311 on 2010-04-09
> **dragoi said:**
> What appears after the 19:32 is with red.

```
-rw-r--r-- 1 root root 2172196 2010-01-08 19:32 /var/cache/apt/archives/dpkg_1.15.5.6_i386.deb
-rw-r--r-- 1 root root  765234 2010-01-08 19:32 /var/cache/apt/archives/dpkg-dev_1.15.5.6_all.deb
```

and

```
Linux [blabla].kimsufi.com 2.6.31.5-grsec-xxxx-grs-ipv4-32 #2 SMP Thu Nov 5 12:35:58 UTC 2009 i686 GNU/Linux
```

That's good, you have a "backup" of the file on your system! :)

create a new directory in /tmp & copy the deb file there:
```
mkdir /tmp/dpkg
cp /var/cache/apt/archives/dpkg_1.15.5.6_i386.deb /tmp/dpkg

```

cd into the new directory and extract the deb file:
```
cd /tmp/dpkg
ar x dpkg*.deb
tar xfvz data.tar.gz

```

copy the file to its location:
```
sudo cp ./usr/bin/dpkg /usr/bin
```

update & reinstall dpkg:
```
sudo apt-get update
sudo apt-get install --reinstall dpkg
```

---

### Post by dragoi on 2010-04-09
After the 

```
ar x dpkg*.deb
```

I get

```
ar: dpkg*.deb: No such file or directory
```

---

### Post by sisco311 on 2010-04-09
Are you sure you are in the correct directory?

you can print the current working directory with 
```
pwd
```
and list the files in it with 
```
ls
```

You can use your file manager to create the directory & copy the file in it.

---

### Post by dragoi on 2010-04-09
Seems I have some other erros, after this command
```
sudo apt-get install --reinstall dpkg
```
I get
```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

And after I try
```
apt-get -f install
```
I get this at the end
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This last error is what made me delete the dpkg file in first place.

---

### Post by sisco311 on 2010-04-09
Please post the whole output of the commands, not just the last line.

---

### Post by dragoi on 2010-04-09
Ok, after first command:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  dpkg: Breaks: konqueror (<= 4:4.2.96-1) but 4:4.2.2-0ubuntu4 is to be installed
  kdebase-runtime: Depends: kdelibs5 (>= 4:4.3.4) but 4:4.2.2-0ubuntu5.2 is to be installed
                   Depends: libplasma3 (>= 4:4.3.4) but 4:4.2.2-0ubuntu5.2 is to be installed
                   Recommends: pmount but it is not going to be installed or
                               kfreebsd-gnu but it is not installable or
                               hurd but it is not installable
  kdelibs-bin: Depends: kdelibs5 (= 4:4.3.4-3) but 4:4.2.2-0ubuntu5.2 is to be installed
  kdeplasma-addons: Depends: plasma-widgets-addons (>= 4:4.3.4-1) but it is not going to be installed
                    Depends: plasma-runners-addons (>= 4:4.3.4-1) but it is not going to be installed
                    Depends: plasma-widget-lancelot (>= 4:4.3.4-1) but it is not going to be installed
                    Depends: plasma-wallpapers-addons (>= 4:4.3.4-1) but it is not going to be installed
  libkdecorations4: Depends: kdelibs5 (>= 4:4.3.4) but 4:4.2.2-0ubuntu5.2 is to be installed
                    Depends: libkephal4 (>= 4:4.3.4) but it is not going to be installed
  libknotificationitem-1-1: Depends: kdelibs5 (>= 4:4.3.4) but 4:4.2.2-0ubuntu5.2 is to be installed
  libkwineffects1: Depends: kdelibs5 (>= 4:4.3.4) but 4:4.2.2-0ubuntu5.2 is to be installed
                   Depends: libplasma3 (>= 4:4.3.4) but 4:4.2.2-0ubuntu5.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


And after the second command:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  bluez-gnome mobile-broadband-provider-info network-manager libmbca0 network-manager-gnome dnsmasq-base ppp
  libudev0 wpasupplicant raptor-utils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-server akregator gnokii-common google-gadgets-common google-gadgets-gst google-gadgets-qt
  google-gadgets-xul kaboom kaddressbook kde-window-manager kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdelibs5 kdelibs5-data kdepim-groupware kdepim-kresources kdepim-runtime
  kdepim-wizards kdepimlibs-data kdepimlibs5 kmail knotes kontact korganizer ksysguard ktimetracker
  libakonadiprivate1 libbluetooth3 libboost-program-options1.40.0 libcompress-raw-zlib-perl libcompress-zlib-perl
  libdbd-mysql-perl libdbi-perl libggadget-1.0-0a libggadget-qt-1.0-0a libgnokii5 libgpgme11 libgps19
  libio-compress-base-perl libio-compress-zlib-perl libkabcommon4 libkde4-ruby1.8 libkdepim4 libkephal4
  libkexiv2-7 libkfontinst4 libkleo4 libkontactinterfaces4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4
  libkworkspace4 liblancelot0 libmarble4 libmimelib4 libmysqlclient16 libncurses5 libncurses5-dbg libncurses5-dev
  libnepomukquery4 libnepomukqueryclient4 libnet-daemon-perl libpcsclite1 libperl5.10
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma-ruby libplasma-ruby1.8 libplasma3
  libplasmaclock4 libplrpc-perl libpolkit-qt0 libprocesscore4 libprocessui4 libqedje0a libqt4-ruby1.8
  libqtruby4shared2 libqzion0a libreadline6 libsmokekde4-2 libsmokeplasma2 libsmokeqt4-2 libsmokesoprano2
  libsolidcontrol4 libsolidcontrolifaces4 libtaskmanager4 libweather-ion4 libxklavier15 marble-data
  mysql-client-5.1 mysql-common mysql-server mysql-server-5.1 ncurses-bin oxygencursors perl perl-base
  perl-modules phonon plasma-dataengines-addons plasma-dataengines-workspace plasma-runners-addons
  plasma-scriptengine-googlegadgets plasma-scriptengine-javascript plasma-scriptengine-python
  plasma-scriptengine-qedje plasma-scriptengine-ruby plasma-scriptengine-superkaramba plasma-scriptengine-webkit
  plasma-scriptengines plasma-wallpapers-addons plasma-widget-lancelot plasma-widgets-addons
  plasma-widgets-workspace python-support xdg-utils
Suggested packages:
  xgnokii gnokii-cli hspell egroupware kleopatra clamav f-prot-installer kjots ktimeticker knode dbishell gpgsm
  gnupg2 pcscd tinyca perl-doc phonon-backend-gstreamer phonon-backend-vlc phonon-backend-mplayer
  plasma-scriptengine-kimono
Recommended packages:
  procmail mailx libhtml-template-perl
The following packages will be REMOVED
  kdebase-workspace-libs4+5 kdebluetooth kdeplasma-addons-data libkholidays4
The following NEW packages will be installed
  akonadi-server gnokii-common google-gadgets-common google-gadgets-gst google-gadgets-qt google-gadgets-xul
  kaboom kdebase-workspace-kgreet-plugins kdepim-groupware kdepim-runtime libboost-program-options1.40.0
  libdbd-mysql-perl libdbi-perl libggadget-1.0-0a libggadget-qt-1.0-0a libgnokii5 libgps19 libkabcommon4
  libkde4-ruby1.8 libkephal4 libkfontinst4 libkontactinterfaces4 libkscreensaver5 libksgrd4 libkworkspace4
  liblancelot0 libmarble4 libnepomukquery4 libnepomukqueryclient4 libnet-daemon-perl
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma-ruby libplasma-ruby1.8
  libplasmaclock4 libplrpc-perl libpolkit-qt0 libprocesscore4 libprocessui4 libqedje0a libqt4-ruby1.8
  libqtruby4shared2 libqzion0a libreadline6 libsmokekde4-2 libsmokeplasma2 libsmokeqt4-2 libsmokesoprano2
  libsolidcontrol4 libsolidcontrolifaces4 libtaskmanager4 libweather-ion4 libxklavier15 marble-data
  mysql-client-5.1 mysql-server mysql-server-5.1 oxygencursors plasma-dataengines-addons
  plasma-dataengines-workspace plasma-runners-addons plasma-scriptengine-googlegadgets
  plasma-scriptengine-javascript plasma-scriptengine-python plasma-scriptengine-qedje plasma-scriptengine-ruby
  plasma-scriptengine-superkaramba plasma-scriptengine-webkit plasma-scriptengines plasma-wallpapers-addons
  plasma-widget-lancelot plasma-widgets-addons plasma-widgets-workspace xdg-utils
The following packages will be upgraded:
  akregator kaddressbook kde-window-manager kdebase-workspace-bin kdebase-workspace-data kdelibs5 kdelibs5-data
  kdepim-kresources kdepim-wizards kdepimlibs-data kdepimlibs5 kmail knotes kontact korganizer ksysguard
  ktimetracker libakonadiprivate1 libbluetooth3 libcompress-raw-zlib-perl libcompress-zlib-perl libgpgme11
  libio-compress-base-perl libio-compress-zlib-perl libkdepim4 libkexiv2-7 libkleo4 libkpgp4 libksieve4
  libmimelib4 libmysqlclient16 libncurses5 libncurses5-dbg libncurses5-dev libpcsclite1 libperl5.10 libplasma3
  mysql-common ncurses-bin perl perl-base perl-modules phonon python-support
44 upgraded, 74 newly installed, 4 to remove and 1010 not upgraded.
64 not fully installed or removed.
Need to get 0B/165MB of archives.
After this operation, 207MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 134725 files and directories currently installed.)
Preparing to replace ksysguard 4:4.2.2-0ubuntu2 (using .../ksysguard_4%3a4.3.4-5_i386.deb) ...
Unpacking replacement ksysguard ...
dpkg: error processing /var/cache/apt/archives/ksysguard_4%3a4.3.4-5_i386.deb (--unpack):
 trying to overwrite '/usr/bin/setscheduler', which is also in package kdebase-workspace-bin 4:4.2.2-0ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/ksysguard_4%3a4.3.4-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by sisco311 on 2010-04-09
Try to upgrade first:
```
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get install -f
```

Post the error messages if any.

---

### Post by dragoi on 2010-04-09
So everything was almost good except this

```
sudo apt-get upgrade
```
It took a while and I got this
```
   &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring libpam0g &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
   &#9474;                                                                     &#9474;
   &#9474; Failure restarting some services for PAM upgrade                    &#9474;
   &#9474;                                                                     &#9474;
   &#9474; The following services could not be restarted for the PAM library   &#9474;
   &#9474; upgrade:                                                            &#9474;
   &#9474;                                                                     &#9474;
   &#9474; gdm                                                                 &#9474;
   &#9474;                                                                     &#9474;
   &#9474; You will need to start these manually by running                    &#9474;
   &#9474; '/etc/init.d/<service> start'.                                      &#9474;
   &#9474;                                                                     &#9474;

```
And at the end of the upgrade something like this
```
Processing triggers for menu ...
Errors were encountered while processing:
 libkwineffects1
 kdebase-runtime
 kdeplasma-addons
 kdelibs-bin
 libknotificationitem-1-1
 libkdecorations4

```

When I tried the last command you told me I got the same error

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  bluez-gnome mobile-broadband-provider-info network-manager libmbca0
  network-manager-gnome dnsmasq-base ppp libudev0 wpasupplicant raptor-utils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-server akregator gnokii-common google-gadgets-common
  google-gadgets-gst google-gadgets-qt google-gadgets-xul kaboom
  kaddressbook kde-window-manager kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-kgreet-plugins kdelibs5
  kdelibs5-data kdepim-groupware kdepim-kresources kdepim-runtime
  kdepim-wizards kdepimlibs-data kdepimlibs5 kmail knotes kontact korganizer
  ksysguard ktimetracker libakonadiprivate1 libbluetooth3
  libboost-program-options1.40.0 libdbd-mysql-perl libdbi-perl
  libggadget-1.0-0a libggadget-qt-1.0-0a libgnokii5 libgpgme11 libgps19
  libkabcommon4 libkde4-ruby1.8 libkdepim4 libkephal4 libkexiv2-7
  libkfontinst4 libkleo4 libkontactinterfaces4 libkpgp4 libkscreensaver5
  libksgrd4 libksieve4 libkworkspace4 liblancelot0 libmarble4 libmimelib4
  libmysqlclient16 libnepomukquery4 libnepomukqueryclient4
  libnet-daemon-perl libpcsclite1 libplasma-applet-system-monitor4
  libplasma-geolocation-interface4 libplasma-ruby libplasma-ruby1.8
  libplasma3 libplasmaclock4 libplrpc-perl libpolkit-qt0 libprocesscore4
  libprocessui4 libqedje0a libqt4-ruby1.8 libqtruby4shared2 libqzion0a
  libreadline6 libsmokekde4-2 libsmokeplasma2 libsmokeqt4-2 libsmokesoprano2
  libsolidcontrol4 libsolidcontrolifaces4 libtaskmanager4 libweather-ion4
  libxklavier15 marble-data mysql-client-5.1 mysql-common mysql-server
  mysql-server-5.1 oxygencursors phonon plasma-dataengines-addons
  plasma-dataengines-workspace plasma-runners-addons
  plasma-scriptengine-googlegadgets plasma-scriptengine-javascript
  plasma-scriptengine-python plasma-scriptengine-qedje
  plasma-scriptengine-ruby plasma-scriptengine-superkaramba
  plasma-scriptengine-webkit plasma-scriptengines plasma-wallpapers-addons
  plasma-widget-lancelot plasma-widgets-addons plasma-widgets-workspace
  python-support xdg-utils
Suggested packages:
  xgnokii gnokii-cli hspell egroupware kleopatra clamav f-prot-installer
  kjots ktimeticker knode dbishell gpgsm gnupg2 pcscd tinyca
  phonon-backend-gstreamer phonon-backend-vlc phonon-backend-mplayer
  plasma-scriptengine-kimono
Recommended packages:
  procmail mailx libhtml-template-perl
The following packages will be REMOVED
  kdebase-workspace-libs4+5 kdebluetooth kdeplasma-addons-data libkholidays4
The following NEW packages will be installed
  akonadi-server gnokii-common google-gadgets-common google-gadgets-gst
  google-gadgets-qt google-gadgets-xul kaboom
  kdebase-workspace-kgreet-plugins kdepim-groupware kdepim-runtime
  libboost-program-options1.40.0 libdbd-mysql-perl libdbi-perl
  libggadget-1.0-0a libggadget-qt-1.0-0a libgnokii5 libgps19 libkabcommon4
  libkde4-ruby1.8 libkephal4 libkfontinst4 libkontactinterfaces4
  libkscreensaver5 libksgrd4 libkworkspace4 liblancelot0 libmarble4
  libnepomukquery4 libnepomukqueryclient4 libnet-daemon-perl
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4
  libplasma-ruby libplasma-ruby1.8 libplasmaclock4 libplrpc-perl
  libpolkit-qt0 libprocesscore4 libprocessui4 libqedje0a libqt4-ruby1.8
  libqtruby4shared2 libqzion0a libreadline6 libsmokekde4-2 libsmokeplasma2
  libsmokeqt4-2 libsmokesoprano2 libsolidcontrol4 libsolidcontrolifaces4
  libtaskmanager4 libweather-ion4 libxklavier15 marble-data mysql-client-5.1
  mysql-server mysql-server-5.1 oxygencursors plasma-dataengines-addons
  plasma-dataengines-workspace plasma-runners-addons
  plasma-scriptengine-googlegadgets plasma-scriptengine-javascript
  plasma-scriptengine-python plasma-scriptengine-qedje
  plasma-scriptengine-ruby plasma-scriptengine-superkaramba
  plasma-scriptengine-webkit plasma-scriptengines plasma-wallpapers-addons
  plasma-widget-lancelot plasma-widgets-addons plasma-widgets-workspace
  xdg-utils
The following packages will be upgraded:
  akregator kaddressbook kde-window-manager kdebase-workspace-bin
  kdebase-workspace-data kdelibs5 kdelibs5-data kdepim-kresources
  kdepim-wizards kdepimlibs-data kdepimlibs5 kmail knotes kontact korganizer
  ksysguard ktimetracker libakonadiprivate1 libbluetooth3 libgpgme11
  libkdepim4 libkexiv2-7 libkleo4 libkpgp4 libksieve4 libmimelib4
  libmysqlclient16 libpcsclite1 libplasma3 mysql-common phonon
  python-support
32 upgraded, 74 newly installed, 4 to remove and 932 not upgraded.
6 not fully installed or removed.
Need to get 0B/151MB of archives.
After this operation, 203MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 134941 files and directories currently installed.)
Preparing to replace ksysguard 4:4.2.2-0ubuntu2 (using .../ksysguard_4%3a4.3.4-5_i386.deb) ...
Unpacking replacement ksysguard ...
dpkg: error processing /var/cache/apt/archives/ksysguard_4%3a4.3.4-5_i386.deb (--unpack):
 trying to overwrite '/usr/bin/setscheduler', which is also in package kdebase-workspace-bin 4:4.2.2-0ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/ksysguard_4%3a4.3.4-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---


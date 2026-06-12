---
title: "Can't update to Natty - &quot;Can not mark 'ubuntu-desktop' for upgrade&quot;"
date: 2011-04-29
forum: General Help
---

### Post by Jim March on 2011-04-29
Here's var/log/dist-upgrade/main.log:

```
2011-04-29 11:14:13,367 INFO Using config files '['./DistUpgrade.cfg']'
2011-04-29 11:14:13,368 INFO uname information: 'Linux jim-lappy 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686'
2011-04-29 11:14:13,368 INFO release-upgrader version '0.150' started
2011-04-29 11:14:13,813 DEBUG svg pixbuf loader failed (Error displaying image)
2011-04-29 11:14:15,665 DEBUG Using 'DistUpgradeViewGtk' view
2011-04-29 11:14:15,711 DEBUG aufsOptionsAndEnvironmentSetup()
2011-04-29 11:14:15,713 DEBUG using '/tmp/upgrade-rw-38XTFQ' as aufs_rw_dir
2011-04-29 11:14:15,713 DEBUG using '/tmp/upgrade-chroot-lfqH3V' as aufs chroot dir
2011-04-29 11:14:15,713 DEBUG enable dpkg --force-overwrite
2011-04-29 11:14:15,781 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2011-04-29 11:14:20,095 DEBUG lsb-release: 'maverick'
2011-04-29 11:14:20,096 DEBUG _pythonSymlinkCheck run
2011-04-29 11:14:20,097 DEBUG openCache()
2011-04-29 11:14:20,691 DEBUG /openCache(), new cache size 32441
2011-04-29 11:14:20,691 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-04-29 11:14:20,692 DEBUG checkViewDepends()
2011-04-29 11:14:20,692 DEBUG running doUpdate() (showErrors=False)
2011-04-29 11:14:25,177 DEBUG openCache()
2011-04-29 11:14:25,798 DEBUG /openCache(), new cache size 32441
2011-04-29 11:14:25,799 DEBUG doPostInitialUpdate
2011-04-29 11:14:25,799 DEBUG Plugin modules in ./plugins: remove_lilo_plugin.py kdelibs4to5_plugin.py langpack_manual_plugin.py deb_plugin.py dpkg_status_plugin.py
2011-04-29 11:14:25,799 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-04-29 11:14:25,801 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-04-29 11:14:25,801 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-04-29 11:14:25,803 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-04-29 11:14:25,804 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-04-29 11:14:25,816 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-04-29 11:14:25,816 DEBUG Loading module ./plugins/deb_plugin.py
2011-04-29 11:14:25,817 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-04-29 11:14:25,817 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-04-29 11:14:25,820 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-04-29 11:14:25,820 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-04-29 11:14:25,820 DEBUG plugins for condition 'nattyPostInitialUpdate' are '[]'
2011-04-29 11:14:25,820 DEBUG plugins for condition 'from_maverickPostInitialUpdate' are '[]'
2011-04-29 11:14:32,995 DEBUG Foreign: 
2011-04-29 11:14:32,996 DEBUG Obsolete: libgoffice-0-common battery-status libaudid3tag2 libglapi-mesa libexiv2-5 libpolkit-qt0 libprotobuf3 libtotem-plparser12 apport-hooks-medibuntu libmagickwand2 libiw29 libpolkit2 ne-terminal-config libknotificationitem1 libavahi-core6 libgupnp-1.0-2 gnome-gmail kde-icons-oxygen libisccc50 libgtkhtml3.8-15 libgnome-bluetooth7 libmagickcore2 linux-backports-modules-input-2.6.35-27-generic liblzma0 linux-headers-lbm-2.6.35-28-generic linux-headers-2.6.35-28-virtual libpoppler5 libgoffice-0-4 libsmokeqt4-2 libevview1 libamrnb3 python-nautilusburn kopete-facebook linux-tools-2.6.35-27 opera libevdocument1 libpolkit-dbus2 libgdata5 clementine libqpdf1 libcdio7 abiword-plugins libboost-thread1.38.0 linux-backports-modules-net-2.6.35-27-generic linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic linux-image-2.6.35-28-generic libxklavier15 libgoffice-0-8-common libpoppler-glib4 flashblock libkorundum4-ruby1.8 linux-headers-2.6.35-27-virtual libntfs-3g54 libaudutil1 libpolkit-grant2 winetricks libisccfg50 python-elementtree adobereader-enu libdvdcss2 google-chrome-beta libgnome-desktop-2-11 linux-headers-2.6.35-27 libamrwb3 firefox-4.0-globalmenu virtualbox-4.0 libass3 python-gnomeprint w32codecs linux-headers-2.6.35-28-generic-pae creepy libffado1 libdns50 libdns53 libbeagle1 wesnoth-data linux-headers-2.6.35-28-generic firefox-4.0 nautilus-dropbox linux-headers-2.6.35-27-generic libsmokekde4-2 kbluetooth chromium librpmio0 liblash2 libbind9-50 linux-headers-2.6.35-28 libgtkhtml2-0 librpm0 libkexiv2-7 libx264-85 elegant-gnome libcelt0 linux-image-2.6.35-27-generic libgirepository1.0-0 sun-java6-plugin libmodplug0c2 medibuntu-keyring libfaad0 kazam sun-java6-bin libmowgli1 libicu40 liblouis0 libboost-regex1.38.0 librasqal1 libiso9660-5 linux-headers-2.6.35-27-generic-pae libao2 kdebluetooth gcc-3.3-base gdiskdump libsad2 libindicate-gtk1 skype liblwres50 abiword-help libmagick++2 sun-java6-fonts libkpathsea4 libxtrap6 python-gtkhtml2 libboost-iostreams1.38.0 python-gnome2-desktop mplayer-nogui libtalloc1 libavutil-extra-49 libx264-67 libboost-date-time1.38.0 libdmraid1.0.0.rc15 firefox-4.0-core pulseaudio-equalizer libboost-program-options1.38.0 python-gtksourceview linux-backports-modules-media-2.6.35-27-generic firefox-3.5 libgssdp-1.0-1 libisc50 liboobs-1-4 libibus1 libindicate3 sun-java6-jre ubuntu-gdm-themes
2011-04-29 11:14:32,998 DEBUG updateSourcesList()
2011-04-29 11:14:33,252 DEBUG rewriteSourcesList()
2011-04-29 11:14:33,254 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu maverick main universe restricted multiverse'
2011-04-29 11:14:33,254 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu natty main universe restricted multiverse' updated to new dist
2011-04-29 11:14:34,007 DEBUG running doUpdate() (showErrors=True)
2011-04-29 11:14:38,704 DEBUG openCache()
2011-04-29 11:14:38,705 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-04-29 11:14:43,902 DEBUG /openCache(), new cache size 33887
2011-04-29 11:14:43,903 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-04-29 11:31:02,003 DEBUG Running KeepInstalledSection rules
2011-04-29 11:31:03,938 DEBUG Kernel uname: '2.6.35-28-generic' 
2011-04-29 11:31:04,226 DEBUG ./get_kernel_list.sh returns: ['linux-generic', 'linux-image-generic', 'linux-virtual', 'linux-image-virtual', 'linux-rt', 'linux-image-rt']
2011-04-29 11:31:04,227 DEBUG linux-generic kernel already installed
2011-04-29 11:31:04,227 DEBUG nvidiaUpdate()
2011-04-29 11:31:04,290 ERROR NvidiaDetection returned a error: __init__() got an unexpected keyword argument 'datadir'
2011-04-29 11:31:04,291 DEBUG Upgrading 'brasero' (Distro PostUpgradeUpgrade rule)
2011-04-29 11:31:04,379 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,380 DEBUG Removing 'kvm-source' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,380 DEBUG Removing 'gtk-qt-engine' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,380 DEBUG Removing 'libparted1.8-12' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,469 DEBUG Removing 'usplash' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,558 DEBUG Removing 'printconf' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,645 DEBUG Removing 'foomatic-db-gutenprint' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,733 DEBUG Removing 'ebox-printers' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:04,830 DEBUG Removing 'kbluetooth' (Distro PostUpgradeRemove rule)
2011-04-29 11:31:08,213 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2011-04-29 11:31:08,296 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2011-04-29 11:31:08,297 DEBUG Removing 'powermanagement-interface' (ubuntu-desktop PostUpgradeRemove rule)
2011-04-29 11:31:08,379 DEBUG Removing 'deskbar-applet' (ubuntu-desktop PostUpgradeRemove rule)
2011-04-29 11:31:08,463 DEBUG Removing 'nautilus-cd-burner' (ubuntu-desktop PostUpgradeRemove rule)
2011-04-29 11:31:08,546 DEBUG Removing 'notification-daemon' (xubuntu-desktop PostUpgradeRemove rule)
2011-04-29 11:31:08,633 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2011-04-29 11:31:08,716 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2011-04-29 11:31:08,806 DEBUG Purging 'linux-restricted-modules-common' (Distro PostUpgradePurge rule)
2011-04-29 11:31:08,807 DEBUG plugins for condition 'PostDistUpgradeCache' are '[]'
2011-04-29 11:31:08,807 DEBUG plugins for condition 'nattyPostDistUpgradeCache' are '[]'
2011-04-29 11:31:08,807 DEBUG plugins for condition 'from_maverickPostDistUpgradeCache' are '[]'
2011-04-29 11:31:08,808 DEBUG quirks: running nattyPostDistUpgradeCache
2011-04-29 11:31:08,808 DEBUG Installing 'ubuntu-minimal' (base meta package keep installed rule)
2011-04-29 11:31:11,065 DEBUG Installing 'ubuntu-standard' (base meta package keep installed rule)
2011-04-29 11:31:15,615 DEBUG Marking 'ubuntu-desktop' for upgrade
2011-04-29 11:33:30,591 DEBUG Can't mark 'ubuntu-desktop' for upgrade (E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.)
2011-04-29 11:42:16,803 ERROR Dist-upgrade failed: 'Can not mark 'ubuntu-desktop' for upgrade'
2011-04-29 11:42:16,804 DEBUG abort called
2011-04-29 11:42:17,160 DEBUG openCache()
2011-04-29 11:42:17,160 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-04-29 11:42:22,517 DEBUG /openCache(), new cache size 32441
2011-04-29 11:42:22,534 DEBUG enabling apt cron job
```

I've been trying to strip various "mods" out - pulling xorg-edgers stuff, updated kernel, etc. trying to get back to a standard Maverick 32bit install.  I don't know what else to try next.  Am I going to have to blow it away and reinstall from scratch?

---


---
title: "Broke my apt-get (and other stuff)"
date: 2012-08-24
forum: General Help
---

### Post by Trauer on 2012-08-24
Sometime ago I installed codeblocks using this "guide":

[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

Today I tried to it on my computer... And something went wrong...
Codeblocks isn't working (nor apt-get)... Whenever i run it, i receive this msg:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 codeblocks:i386 : Depends: libatk1.0-0:i386 (>= 1.20.0) but it is not installed
                   Depends: libc6:i386 (>= 2.7-1) but it is not installed
                   Depends: libcairo2:i386 (>= 1.2.4) but it is not installed
                   Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                   Depends: libglib2.0-0:i386 (>= 2.12.0) but it is not installed
                   Depends: libgtk2.0-0:i386 (>= 2.12.0) but it is not installed
                   Depends: libpango1.0-0:i386 (>= 1.20.3) but it is not installed
                   Depends: libstdc++6:i386 (>= 4.1.1) but it is not installed
                   Depends: libwxbase2.8-0:i386 (>= 2.8.10.1) but it is not installed
                   Depends: libwxgtk2.8-0:i386 (>= 2.8.10.1) but it is not installed
                   Depends: codeblocks-common:i386 (= 10.05-1) but it is not installable
                   Recommends: gcc:i386 but it is not installed or
                               g++:i386 but it is not installed
                   Recommends: gdb:i386 but it is not installed
 codeblocks-contrib:i386 : Depends: libatk1.0-0:i386 (>= 1.20.0) but it is not installed
                           Depends: libbz2-1.0:i386 but it is not installed
                           Depends: libc6:i386 (>= 2.7-1) but it is not installed
                           Depends: libcairo2:i386 (>= 1.2.4) but it is not installed
                           Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                           Depends: libglib2.0-0:i386 (>= 2.12.0) but it is not installed
                           Depends: libgtk2.0-0:i386 (>= 2.12.0) but it is not installed
                           Depends: libpango1.0-0:i386 (>= 1.20.3) but it is not installed
                           Depends: libstdc++6:i386 (>= 4.2.1) but it is not installed
                           Depends: libwxbase2.8-0:i386 (>= 2.8.10.1) but it is not installed
                           Depends: libwxgtk2.8-0:i386 (>= 2.8.10.1) but it is not installed
                           Depends: libx11-6:i386 but it is not installed
                           Depends: zlib1g:i386 (>= 1:1.2.3.3.dfsg) but it is not installed
                           Depends: codeblocks-contrib-common:i386 (= 10.05-1) but it is not installable
 codeblocks-dev:i386 : Depends: codeblocks-headers:i386 (= 10.05-1) but it is not installable
 libcodeblocks0:i386 : Depends: libc6:i386 (>= 2.7-1) but it is not installed
                       Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                       Depends: libstdc++6:i386 (>= 4.1.1) but it is not installed
                       Depends: libwxbase2.8-0:i386 (>= 2.8.10.1) but it is not installed
                       Depends: libwxgtk2.8-0:i386 (>= 2.8.10.1) but it is not installed
                       Depends: binutils:i386 (>= 2.14.90.0.7) but it is not installed
                       Depends: file:i386 but it is not installed
                       Depends: libmagic1:i386 but it is not installed
                       Depends: libncurses5:i386 but it is not installed
                       Depends: zlib1g:i386 but it is not installed
 libwxsmithlib0:i386 : Depends: libc6:i386 (>= 2.7-1) but it is not installed
                       Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                       Depends: libstdc++6:i386 (>= 4.1.1) but it is not installed
                       Depends: libwxbase2.8-0:i386 (>= 2.8.10.1) but it is not installed
                       Depends: libwxgtk2.8-0:i386 (>= 2.8.10.1) but it is not installed
 wxsmith-dev:i386 : Depends: wxsmith-headers:i386 (= 10.05-1) but it is not installable
E: Unmet dependencies. Try using -f.

```Well, as suggested I tried using "sudo apt-get -f install"...
And THIS appeared

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libglib2.0-0:i386 libc6:i386 libpcre3:i386 libncurses5:i386 libx11-6:i386 libgcc1:i386
  libstdc++6:i386 zlib1g:i386 libatk1.0-0:i386 libtinfo5:i386 libgpm2:i386 libselinux1:i386
  gcc-4.6-base:i386 libffi6:i386 valgrind:i386 libc6-dbg:i386 libxcb1:i386 libxau6:i386
  libxdmcp6:i386 libwxbase2.8-0:i386 libexpat1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.6-base:i386 libatk1.0-0:i386 libc6:i386 libc6-dbg:i386 libexpat1:i386 libffi6:i386
  libgcc1:i386 libglib2.0-0:i386 libgpm2:i386 libncurses5:i386 libpcre3:i386 libpython3.2
  libselinux1:i386 libstdc++6:i386 libtinfo5:i386 libwxbase2.8-0:i386 libx11-6:i386 libxau6:i386
  libxcb1:i386 libxdmcp6:i386 python3 python3-minimal python3-uno python3.2 python3.2-minimal
  valgrind:i386 zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386 gpm:i386 python3-doc python3-tk python3.2-doc binfmt-support
  kcachegrind:i386 alleyoop:i386 valkyrie:i386
Recommended packages:
  gdb:i386
The following packages will be REMOVED:
  activity-log-manager-control-center aisleriot apparmor apport apport-gtk apt-xapian-index
  aptdaemon apturl apturl-common bluez bluez-alsa bluez-gstreamer checkbox checkbox-qt
  codeblocks:i386 codeblocks-contrib:i386 codeblocks-contrib-dbg:i386 codeblocks-dbg:i386
  codeblocks-dev:i386 command-not-found compiz compiz-gnome compiz-plugins-main-default
  compizconfig-backend-gconf deja-dup duplicity eog evolution-data-server file file-roller firefox
  firefox-globalmenu firefox-gnome-support flashplugin-installer foomatic-db-compressed-ppds gconf2
  gdb gedit gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-ubuntuoneui-3.0 gksu
  gnome-bluetooth gnome-control-center gnome-media gnome-menus gnome-orca gnome-sudoku
  gnome-terminal gnome-terminal-data gnome-user-share gstreamer0.10-gconf gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter hplip hplip-data ibus
  ibus-pinyin ibus-table indicator-datetime indicator-power jockey-common jockey-gtk
  landscape-client-ui-install language-selector-common language-selector-gnome launchpad-integration
  libcanberra-gtk-module libcanberra-gtk3-module libcodeblocks0:i386 libcompizconfig0 libfolks-eds25
  libgksu2-0 libgnome-media-profiles-3.0-0 libgnome2-common libgweather-3-0 libgweather-common
  libgwibber-gtk2 libgwibber2 libmetacity-private0 libpeas-1.0-0 libpurple-bin libpython2.7
  libreoffice-gnome librhythmbox-core5 libsyncdaemon-1.0-1 libtotem0 libubuntuoneui-3.0-1
  libwxsmithlib0:i386 libwxsmithlib0-dev:i386 light-themes lsb-release metacity metacity-common
  nautilus-share network-manager-gnome nvidia-common onboard oneconf openprinting-ppds
  printer-driver-foo2zjs printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr
  printer-driver-sag-gdi printer-driver-splix python python-appindicator python-apport python-apt
  python-apt-common python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-brlapi python-cairo python-chardet python-configglue python-crypto python-cups
  python-cupshelpers python-dateutil python-dbus python-debian python-debtagshw python-defer
  python-dirspec python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gdbm python-gi
  python-gi-cairo python-gnomekeyring python-gnupginterface python-gobject python-gobject-2
  python-gst0.10 python-gtk2 python-httplib2 python-ibus python-imaging python-keyring
  python-launchpadlib python-lazr.restfulclient python-lazr.uri python-libproxy python-libxml2
  python-louis python-mako python-markupsafe python-minimal python-notify python-oauth
  python-openssl python-packagekit python-pam python-pexpect python-piston-mini-client
  python-pkg-resources python-problem-report python-protobuf python-pyatspi2 python-pycurl
  python-pyinotify python-renderpm python-reportlab python-reportlab-accel python-serial
  python-simplejson python-smbc python-software-properties python-speechd python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client
  python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno
  python-virtkey python-wadllib python-xapian python-xdg python-xkit python-zeitgeist
  python-zope.interface python2.7 python2.7-minimal rhythmbox rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist
  rhythmbox-plugins rhythmbox-ubuntuone sessioninstaller software-center
  software-center-aptdaemon-plugins software-properties-common software-properties-gtk
  system-config-printer-common system-config-printer-gnome system-config-printer-udev totem
  totem-mozilla totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-minimal ubuntu-sso-client
  ubuntu-sso-client-gtk ubuntu-standard ubuntu-system-service ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-couch ubuntuone-installer ufw
  unattended-upgrades unity unity-2d unity-common unity-lens-applications unity-lens-video
  unity-scope-musicstores unity-scope-video-remote update-manager update-manager-core
  update-notifier update-notifier-common usb-creator-common usb-creator-gtk wxsmith-dev:i386
  xdiagnose xul-ext-ubufox zeitgeist zeitgeist-core zeitgeist-datahub
The following NEW packages will be installed:
  gcc-4.6-base:i386 libatk1.0-0:i386 libc6:i386 libc6-dbg:i386 libexpat1:i386 libffi6:i386
  libgcc1:i386 libglib2.0-0:i386 libgpm2:i386 libncurses5:i386 libpcre3:i386 libpython3.2
  libselinux1:i386 libstdc++6:i386 libtinfo5:i386 libwxbase2.8-0:i386 libx11-6:i386 libxau6:i386
  libxcb1:i386 libxdmcp6:i386 python3 python3-minimal python3-uno python3.2 python3.2-minimal
  valgrind:i386 zlib1g:i386
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  python-minimal python2.7-minimal (due to python-minimal)
0 upgraded, 27 newly installed, 246 to remove and 1 not upgraded.
9 not fully installed or removed.
Need to get 30.8 MB of archives.
After this operation, 284 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
```Well... Thats a scary error... But manly as **** I typed
"Yes, do as I say!"...
Let's just say I had to reinstall Ubuntu after that... And here I'm, trying to install codeblocks again... And it happened all over again, but this time I didn't type "Yes, do as I say!"...

Gentleman, would you kindly help me fix this?

---

### Post by Trauer on 2012-08-24
Mentlegen, help me please...

---

### Post by Trauer on 2012-08-24
Don't worry, I won't... As matter of fact, I'm not using this forum anymore... G'bye people

---

### Post by bodhi.zazen on 2012-08-24
Well, to be honest, you are using a third party package. You really need to contact the person who maintains the .deb

As far as fixing apt, you can try removing codeblocks and see.

---


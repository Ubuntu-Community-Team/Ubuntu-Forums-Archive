---
title: "Updates seem to have broken a lot of UI elements."
date: 2012-07-24
forum: General Help
---

### Post by SaryonOnline on 2012-07-24
Hello everyone,

This morning I had a batch of about 50 updates, after which a lot of issues arose that are probably related. I use Ubuntu 12.04 amd64.

This is what I noticed so far:

[LIST]
[*]Pressing super + w no longer brings up a shortcut list, but shows a small search bar in the lower right corner instead (looks like search in nautilus).
[*]Tapping super and alt brings up the dash and options screens in the top left, but only after several seconds.
[*]Super still brings up the side bar and number shortcuts as expected.
[*]unity --reset and unity --replace result in a segfault in compiz.
[*]alt-tab brings up a small grey box with icons instead of the 'fancy' regular one.
[*]switching between multiple windows of the same application through for instance super + 2, shows the windows on a black background in very low resolution.
[*]Reboot via the cog in the top right hanged twice, but I can't reproduce that reliably.
[*]EDIT: I had the sidebar set to autohide, but it now shows up all the time. EDIT: That was probably an effect of unity --reset.
[/LIST]

EDIT: I am also no longer able to run Steam in Wine. It crashes with the following error:
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  301
  Current serial number in output stream:  301

These are the updates from today, taken from /var/log/apt/history.log. The majority of these are for qt, with some for libjpeg, gnome-media, linux, python, R, and libexif. I also installed aptitude, but that's probably unrelated.

If there is anyone who can point me in the right direction, I would really appreciate it. My system is still fairly usable, but it's annoying none the less.

Start-Date: 2012-07-24  08:23:39
Commandline: aptdaemon role='role-commit-packages' sender=':1.62'
Install: linux-headers-3.2.0-27:amd64 (3.2.0-27.43), linux-image-3.2.0-27-generic:amd64 (3.2.0-27.43), linux-headers-3.2.0-27-generic:amd64 (3.2.0-27.43)
Upgrade: libqt4-declarative:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-declarative:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libjpeg-turbo8-dev:amd64 (1.1.90+svn733-0ubuntu4, 1.1.90+svn733-0ubuntu4.1), gnome-media:amd64 (3.4.0-0ubuntu2, 3.4.0-0ubuntu2.1), libqt4-qt3support:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-qt3support:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-opengl-dev:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libjpeg-turbo8:amd64 (1.1.90+svn733-0ubuntu4, 1.1.90+svn733-0ubuntu4.1), libjpeg-turbo8:i386 (1.1.90+svn733-0ubuntu4, 1.1.90+svn733-0ubuntu4.1), qdbus:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-test:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-test:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-script:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-script:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-designer:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-designer:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), python-piston-mini-client:amd64 (0.7.2-0ubuntu1, 0.7.2+bzr57-0ubuntu1), r-cran-mgcv:amd64 (1.7-18-1precise0, 1.7-19-1precise0), libqt4-network:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-network:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-dbus:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-dbus:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), linux-generic:amd64 (3.2.0.26.28, 3.2.0.27.29), libqt4-opengl:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-opengl:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-xmlpatterns:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-xmlpatterns:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-sql-sqlite:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-dev:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-help:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqtcore4:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqtcore4:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), qt4-qmake:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), linux-headers-generic:amd64 (3.2.0.26.28, 3.2.0.27.29), linux-image-generic:amd64 (3.2.0.26.28, 3.2.0.27.29), libqt4-sql:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-sql:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-svg:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-svg:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-xml:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-xml:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqtgui4:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqtgui4:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), qt4-linguist-tools:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), linux-libc-dev:amd64 (3.2.0-26.41, 3.2.0-27.43), libqt4-sql-mysql:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libexif12:amd64 (0.6.20-2, 0.6.20-2ubuntu0.1), libexif12:i386 (0.6.20-2, 0.6.20-2ubuntu0.1), libqt4-scripttools:amd64 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2), libqt4-scripttools:i386 (4.8.1-0ubuntu4.1, 4.8.1-0ubuntu4.2)
End-Date: 2012-07-24  08:24:35

Start-Date: 2012-07-24  12:45:10
Commandline: apt-get install aptitude
Install: libsub-name-perl:amd64 (0.05-1build2, automatic), libparse-debianchangelog-perl:amd64 (1.2.0-1ubuntu1, automatic), aptitude:amd64 (0.6.6-1ubuntu1), libcwidget3:amd64 (0.5.16-3.1ubuntu1, automatic), libboost-iostreams1.46.1:amd64 (1.46.1-7ubuntu3, automatic), libio-string-perl:amd64 (1.08-2, automatic), libept1.4.12:amd64 (1.0.6~exp1ubuntu1, automatic), libclass-accessor-perl:amd64 (0.34-1, automatic)
End-Date: 2012-07-24  12:45:16

---

### Post by SaryonOnline on 2012-07-25
It turned out that the ATI driver was broken somehow. After I found out that I got that ATI error even by running fglrxinfo, I decided to replace the version I had installed from the binary provided by the AMD website with the regular version supplied by Ubuntu.

I used the steps from [this link]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx") to remove the driver completely. Steps are reproduced below:

```

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

I then activated the Ubuntu supplied driver in the 'Additional Drivers' menu and rebooted.

Note that there also seems to be a patch to the binary ATI driver that fixes an issue with Ubuntu 12.04, but I am not sure if that relates to the issues I had, so I just used the Ubuntu version.

---


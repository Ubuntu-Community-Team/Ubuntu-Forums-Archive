---
title: "Unable to build QIBASE/Firebird support in Qt"
date: 2011-01-09
forum: General Help
---

### Post by yyyc186 on 2011-01-09
roland@roland-Generic-Desktop1:~/rebuild$ lsb_release -rd
Description:    Ubuntu 10.10
Release:        10.10


Followed the following instructions:

installed build-essential package

mkdir rebuild
cd rebuild
apt-get source libqt4-sql
Reading package lists... Done
Building dependency tree
Reading state information... Done
Picking 'qt4-x11' as source package instead of 'libqt4-sql'
NOTICE: 'qt4-x11' packaging is maintained in the 'Git' version control system at:
git://git.debian.org/pkg-kde/qt4-x11.git
Need to get 209MB of source archives.
blah blah blah

sudo apt-get build-dep libqt4-sql
[sudo] password for roland:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Picking 'qt4-x11' as source package instead of 'libqt4-sql'
Note, selecting 'libjpeg62-dev' instead of 'libjpeg-dev'
The following NEW packages will be installed:
  autotools-dev comerr-dev debhelper diffstat flex freetds-common freetds-dev gettext html2text intltool-debian krb5-multidev libasound2-dev
  libatk1.0-dev libaudio-dev libcairo-gobject2 libcairo2-dev libct4 libcups2-dev libdbus-1-dev libexpat1-dev libfontconfig1-dev
...
  x11proto-composite-dev x11proto-damage-dev x11proto-fixes-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-video-dev
  x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
0 upgraded, 98 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.7MB of archives.
After this operation, 124MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main m4 amd64 1.4.14-3 [290kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main flex amd64 2.5.35-9.1 [261kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main libxmu-headers all 2:1.0.5-1 [22.7kB]
…


Get:96 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main libaudio-dev amd64 1.9.2-3 [553kB]
Get:97 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main pkg-kde-tools all 0.9.2ubuntu15 [105kB]
Get:98 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main unixodbc-dev amd64 2.2.14p2-1ubuntu1 [567kB]
Fetched 32.7MB in 2min 10s (250kB/s)
Extracting templates from packages: 100%
Selecting previously deselected package m4.
(Reading database ... 203436 files and directories currently installed.)
Unpacking m4 (from .../archives/m4_1.4.14-3_amd64.deb) ...
Selecting previously deselected package flex.
Unpacking flex (from .../flex_2.5.35-9.1_amd64.deb) ...
Selecting previously deselected package libxmu-headers.
…

Selecting previously deselected package libaudio-dev.
Unpacking libaudio-dev (from .../libaudio-dev_1.9.2-3_amd64.deb) ...
Selecting previously deselected package pkg-kde-tools.
Unpacking pkg-kde-tools (from .../pkg-kde-tools_0.9.2ubuntu15_all.deb) ...
Selecting previously deselected package unixodbc-dev.
Unpacking unixodbc-dev (from .../unixodbc-dev_2.2.14p2-1ubuntu1_amd64.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Setting up m4 (1.4.14-3) ...
Setting up flex (2.5.35-9.1) ...
Setting up libxmu-headers (2:1.0.5-1) ...
Setting up libgssrpc4 (1.8.1+dfsg-5ubuntu0.2) ...
Setting up libkadm5clnt-mit7 (1.8.1+dfsg-5ubuntu0.2) ...
Setting up libkdb5-4 (1.8.1+dfsg-5ubuntu0.2) ...
Setting up libkadm5srv-mit7 (1.8.1+dfsg-5ubuntu0.2) …
...
Setting up libaudio-dev (1.9.2-3) ...
Setting up pkg-kde-tools (0.9.2ubuntu15) ...
Setting up unixodbc-dev (2.2.14p2-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

roland@roland-Generic-Desktop1:~/rebuild$ dir qt4*
qt4-x11_4.7.0-0ubuntu4.2.debian.tar.gz  qt4-x11_4.7.0-0ubuntu4.2.dsc  qt4-x11_4.7.0.orig.tar.gz

qt4-x11-4.7.0:
bin            configure      demos     imports  LGPL_EXCEPTION.txt  LICENSE.GPL3  projects.pro  src        translations
changes-4.7.0  configure.exe  doc       include  lib                 LICENSE.LGPL  qmake         templates
config.tests   debian         examples  INSTALL  LICENSE.FDL         mkspecs       README        tools


dpkg-source -x qt4-x11_4.7.0-0ubuntu4.2.dsc
gpgv: Signature made Fri 19 Nov 2010 07:17:45 AM CST using DSA key ID A2D06936
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./qt4-x11_4.7.0-0ubuntu4.2.dsc
blah blah blah

cd qt4*
juffed debian/rules

made ibase section of file look as follows:

#no ibase in Kubuntu, jriddell 2010-05-19
ibase_architectures := i386 kfreebsd-i386 kfreebsd-amd64 knetbsd-i386 netbsd-i386 amd64 sparc powerpc
#ibase_architectures := none
ifeq ($(DEB_HOST_ARCH),$(findstring $(DEB_HOST_ARCH), $(ibase_architectures)))
	extra_configure_opts += -plugin-sql-ibase
else
	extra_configure_opts += -no-sql-ibase
endif




dpkg-buildpackage -rfakeroot -b

verified on terminal that extra_configure_opts did indeed say plugin-sql-ibase

spent HOURS waiting for build to complete

dpkg-deb: warning: 'debian/qt4-doc/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: building package `qt4-doc' in `../qt4-doc_4.7.0-0ubuntu4.2_all.deb'.
dpkg-deb: warning: ignoring 1 warnings about the control file(s)

dpkg-deb: warning: 'debian/qt4-doc-html/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: building package `qt4-doc-html' in `../qt4-doc-html_4.7.0-0ubuntu4.2_all.deb'.
dpkg-deb: warning: ignoring 1 warnings about the control file(s)

 dpkg-genchanges -b >../qt4-x11_4.7.0-0ubuntu4.2_amd64.changes
dpkg-genchanges: binary-only upload - not including any source code
 signfile qt4-x11_4.7.0-0ubuntu4.2_amd64.changes
gpg: skipped "Oliver Grawert <ogra@ubuntu.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-source --after-build qt4-x11-4.7.0
dpkg-buildpackage: binary only upload (no source included)
dpkg-buildpackage: warning: Failed to sign .changes file

***********************  Notice how there is no QIBASE, IBASE, fire or inter anything
***********************  yes I have the fbclient installed
cd ..
dir *.deb
libqt4-assistant_4.7.0-0ubuntu4.2_amd64.deb                    libqt4-sql-sqlite2_4.7.0-0ubuntu4.2_amd64.deb
libqt4-core_4.7.0-0ubuntu4.2_amd64.deb                         libqt4-sql-sqlite_4.7.0-0ubuntu4.2_amd64.deb
libqt4-dbg_4.7.0-0ubuntu4.2_amd64.deb                          libqt4-sql-tds_4.7.0-0ubuntu4.2_amd64.deb
libqt4-dbus_4.7.0-0ubuntu4.2_amd64.deb                         libqt4-svg_4.7.0-0ubuntu4.2_amd64.deb
libqt4-declarative_4.7.0-0ubuntu4.2_amd64.deb                  libqt4-test_4.7.0-0ubuntu4.2_amd64.deb
libqt4-declarative-folderlistmodel_4.7.0-0ubuntu4.2_amd64.deb  libqt4-webkit_4.7.0-0ubuntu4.2_amd64.deb
libqt4-declarative-gestures_4.7.0-0ubuntu4.2_amd64.deb         libqt4-webkit-dbg_4.7.0-0ubuntu4.2_amd64.deb
libqt4-declarative-particles_4.7.0-0ubuntu4.2_amd64.deb        libqt4-xml_4.7.0-0ubuntu4.2_amd64.deb
libqt4-designer_4.7.0-0ubuntu4.2_amd64.deb                     libqt4-xmlpatterns_4.7.0-0ubuntu4.2_amd64.deb
libqt4-dev_4.7.0-0ubuntu4.2_amd64.deb                          libqt4-xmlpatterns-dbg_4.7.0-0ubuntu4.2_amd64.deb
libqt4-gui_4.7.0-0ubuntu4.2_amd64.deb                          libqtcore4_4.7.0-0ubuntu4.2_amd64.deb
libqt4-help_4.7.0-0ubuntu4.2_amd64.deb                         libqtgui4_4.7.0-0ubuntu4.2_amd64.deb
libqt4-network_4.7.0-0ubuntu4.2_amd64.deb                      qt4-demos_4.7.0-0ubuntu4.2_amd64.deb
libqt4-opengl_4.7.0-0ubuntu4.2_amd64.deb                       qt4-demos-dbg_4.7.0-0ubuntu4.2_amd64.deb
libqt4-opengl-dev_4.7.0-0ubuntu4.2_amd64.deb                   qt4-designer_4.7.0-0ubuntu4.2_amd64.deb
libqt4-qt3support_4.7.0-0ubuntu4.2_amd64.deb                   qt4-dev-tools_4.7.0-0ubuntu4.2_amd64.deb
libqt4-script_4.7.0-0ubuntu4.2_amd64.deb                       qt4-doc_4.7.0-0ubuntu4.2_all.deb
libqt4-scripttools_4.7.0-0ubuntu4.2_amd64.deb                  qt4-doc-html_4.7.0-0ubuntu4.2_all.deb
libqt4-sql_4.7.0-0ubuntu4.2_amd64.deb                          qt4-qmake_4.7.0-0ubuntu4.2_amd64.deb
libqt4-sql-mysql_4.7.0-0ubuntu4.2_amd64.deb                    qt4-qmlviewer_4.7.0-0ubuntu4.2_amd64.deb
libqt4-sql-odbc_4.7.0-0ubuntu4.2_amd64.deb                     qt4-qtconfig_4.7.0-0ubuntu4.2_amd64.deb
libqt4-sql-psql_4.7.0-0ubuntu4.2_amd64.deb


sudo dpkg -i libqt4-sql_4.7.0-0ubuntu4.2_amd64.deb 
[sudo] password for roland: 
(Reading database ... 210025 files and directories currently installed.)
Preparing to replace libqt4-sql 4:4.7.0-0ubuntu4.2 (using libqt4-sql_4.7.0-0ubuntu4.2_amd64.deb) ...
Unpacking replacement libqt4-sql ...
Setting up libqt4-sql (4:4.7.0-0ubuntu4.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


Rebuild and run my little test application:

Drivers installed on your system: QSQLITE   QMYSQL3   QMYSQL   QPSQL7   QPSQL  

What gives?

---


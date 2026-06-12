---
title: "any installation/removal gets stuck at 90%"
date: 2010-08-31
forum: General Help
---

### Post by supermooshman on 2010-08-31
Hi All,

I just installed ubuntu 10.04 on my spare computer.
Everytime I try to install or remove something (through the ubuntu software center) I get to 90% and I get an errormessage. The software seems to be installed, so I'm not sure what the deal is.

The programs I tried to install:
- chromium
- skype
- thunderbird
- ubuntu restricted extras

The programs I tried to uninstall:
- evolution

Anyone any idea what went wrong?

---

### Post by sikander3786 on 2010-08-31
Please quote the error message. Also does it succeede in 

**sudo apt-get update**

from a terminal?

---

### Post by andrewthomas on 2010-08-31
> **sikander3786 said:**
> Please quote the error message. Also does it succeede in 

**sudo apt-get update**

from a terminal?+1
  copy and paste the code in the terminal and post your error message (if any)```
sudo apt-get update && sudo apt-get install thunderbird
```

---

### Post by supermooshman on 2010-08-31
> **sikander3786 said:**
> 
**sudo apt-get update**


this seems to work, but when I did the first update (it's a fresh install) I got an error saying I had some broken packages
I fixed these by using synaptic -> edit - fix broken packages

The error message displays:```
installArchives() failed: 
Extracting templates from packages: 35%
Extracting templates from packages: 70%
Extracting templates from packages: 100%

Extracting templates from packages: 35%
Extracting templates from packages: 70%
Extracting templates from packages: 100%
Selecting previously deselected package libattica0.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 147106 files and directories currently installed.)
Unpacking libattica0 (from .../libattica0_0.1.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libdbusmenu-qt2.
Unpacking libdbusmenu-qt2 (from .../libdbusmenu-qt2_0.3.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-designer.
Unpacking libqt4-designer (from .../libqt4-designer_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libphonon4.
Unpacking libphonon4 (from .../libphonon4_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libpolkit-qt-1-0.
Unpacking libpolkit-qt-1-0 (from .../libpolkit-qt-1-0_0.95.1-1fakesync1_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-svg.
Unpacking libqt4-svg (from .../libqt4-svg_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-xmlpatterns.
Unpacking libqt4-xmlpatterns (from .../libqt4-xmlpatterns_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-webkit.
Unpacking libqt4-webkit (from .../libqt4-webkit_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libclucene0ldbl.
Unpacking libclucene0ldbl (from .../libclucene0ldbl_0.9.21b-2_i386.deb) ...
Selecting previously deselected package libiodbc2.
Unpacking libiodbc2 (from .../libiodbc2_3.52.6-4_i386.deb) ...
Selecting previously deselected package soprano-daemon.
Unpacking soprano-daemon (from .../soprano-daemon_2.4.2+dfsg.1-0ubuntu1.1_i386.deb) ...
Selecting previously deselected package libsoprano4.
Unpacking libsoprano4 (from .../libsoprano4_2.4.2+dfsg.1-0ubuntu1.1_i386.deb) ...
Selecting previously deselected package libexiv2-6.
Unpacking libexiv2-6 (from .../libexiv2-6_0.19-1_i386.deb) ...
Selecting previously deselected package libstreams0.
Unpacking libstreams0 (from .../libstreams0_0.7.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libstreamanalyzer0.
Unpacking libstreamanalyzer0 (from .../libstreamanalyzer0_0.7.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package kdelibs5-data.
Unpacking kdelibs5-data (from .../kdelibs5-data_4%3a4.4.2-0ubuntu4_all.deb) ...
Selecting previously deselected package kdelibs-bin.
Unpacking kdelibs-bin (from .../kdelibs-bin_4%3a4.4.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package shared-desktop-ontologies.
Unpacking shared-desktop-ontologies (from .../shared-desktop-ontologies_0.3-1_all.deb) ...
Selecting previously deselected package kdelibs5.
Unpacking kdelibs5 (from .../kdelibs5_4%3a4.4.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package amarok-common.
Unpacking amarok-common (from .../amarok-common_2%3a2.3.0-0ubuntu4_all.deb) ...
Selecting previously deselected package libtag-extras1.
Unpacking libtag-extras1 (from .../libtag-extras1_1.0.1-2_i386.deb) ...
Selecting previously deselected package amarok-utils.
Unpacking amarok-utils (from .../amarok-utils_2%3a2.3.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package libxine1-bin.
Unpacking libxine1-bin (from .../libxine1-bin_1.1.17-1ubuntu3_i386.deb) ...
Selecting previously deselected package libxine1-misc-plugins.
Unpacking libxine1-misc-plugins (from .../libxine1-misc-plugins_1.1.17-1ubuntu3_i386.deb) ...
Selecting previously deselected package libxcb-shape0.
Unpacking libxcb-shape0 (from .../libxcb-shape0_1.5-2_i386.deb) ...
Selecting previously deselected package libxcb-shm0.
Unpacking libxcb-shm0 (from .../libxcb-shm0_1.5-2_i386.deb) ...
Selecting previously deselected package libxcb-xv0.
Unpacking libxcb-xv0 (from .../libxcb-xv0_1.5-2_i386.deb) ...
Selecting previously deselected package libxine1-x.
Unpacking libxine1-x (from .../libxine1-x_1.1.17-1ubuntu3_i386.deb) ...
Selecting previously deselected package libxine1-console.
Unpacking libxine1-console (from .../libxine1-console_1.1.17-1ubuntu3_i386.deb) ...
Selecting previously deselected package libxine1.
Unpacking libxine1 (from .../libxine1_1.1.17-1ubuntu3_i386.deb) ...
Selecting previously deselected package phonon-backend-xine.
Unpacking phonon-backend-xine (from .../phonon-backend-xine_4%3a4.4.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package libqca2.
Unpacking libqca2 (from .../libqca2_2.0.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package libqt4-opengl.
Unpacking libqt4-opengl (from .../libqt4-opengl_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libplasma3.
Unpacking libplasma3 (from .../libplasma3_4%3a4.4.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package libssh-4.
Unpacking libssh-4 (from .../libssh-4_0.4.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package kdebase-runtime-data.
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a4.4.2-0ubuntu4.1_all.deb) ...
Selecting previously deselected package oxygen-icon-theme.
Unpacking oxygen-icon-theme (from .../oxygen-icon-theme_4%3a4.4.2-0ubuntu2_all.deb) ...
Selecting previously deselected package plasma-scriptengine-javascript.
Unpacking plasma-scriptengine-javascript (from .../plasma-scriptengine-javascript_4%3a4.4.2-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package kdebase-runtime.
Unpacking kdebase-runtime (from .../kdebase-runtime_4%3a4.4.2-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package liblastfm0.
Unpacking liblastfm0 (from .../liblastfm0_0.4.0~git20090710-1_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.1.41-3ubuntu12.6_all.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.41-3ubuntu12.6_i386.deb) ...
Selecting previously deselected package phonon.
Unpacking phonon (from .../phonon_4%3a4.6.2-0ubuntu5_all.deb) ...
Selecting previously deselected package libqtscript4-core.
Unpacking libqtscript4-core (from .../libqtscript4-core_0.1.0-3build1_i386.deb) ...
Selecting previously deselected package libqtscript4-gui.
Unpacking libqtscript4-gui (from .../libqtscript4-gui_0.1.0-3build1_i386.deb) ...
Selecting previously deselected package libqtscript4-network.
Unpacking libqtscript4-network (from .../libqtscript4-network_0.1.0-3build1_i386.deb) ...
Selecting previously deselected package libqtscript4-xml.
Unpacking libqtscript4-xml (from .../libqtscript4-xml_0.1.0-3build1_i386.deb) ...
Selecting previously deselected package libqtscript4-sql.
Unpacking libqtscript4-sql (from .../libqtscript4-sql_0.1.0-3build1_i386.deb) ...
Selecting previously deselected package libqtscript4-uitools.
Unpacking libqtscript4-uitools (from .../libqtscript4-uitools_0.1.0-3build1_i386.deb) ...
Selecting previously deselected package amarok.
Unpacking amarok (from .../amarok_2%3a2.3.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package exiv2.
Unpacking exiv2 (from .../archives/exiv2_0.19-1_i386.deb) ...
Selecting previously deselected package libboost-program-options1.40.0.
Unpacking libboost-program-options1.40.0 (from .../libboost-program-options1.40.0_1.40.0-4ubuntu4_i386.deb) ...
Selecting previously deselected package libakonadiprivate1.
Unpacking libakonadiprivate1 (from .../libakonadiprivate1_1.3.1-0ubuntu3_i386.deb) ...
Selecting previously deselected package kdepimlibs-data.
Unpacking kdepimlibs-data (from .../kdepimlibs-data_4%3a4.4.2-0ubuntu2.1_all.deb) ...
Selecting previously deselected package kdepimlibs5.
Unpacking kdepimlibs5 (from .../kdepimlibs5_4%3a4.4.2-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package libqt4-assistant.
Unpacking libqt4-assistant (from .../libqt4-assistant_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-help.
Unpacking libqt4-help (from .../libqt4-help_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-scripttools.
Unpacking libqt4-scripttools (from .../libqt4-scripttools_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-test.
Unpacking libqt4-test (from .../libqt4-test_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package python-sip.
Unpacking python-sip (from .../python-sip_4.10.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package python-qt4.
Unpacking python-qt4 (from .../python-qt4_4.7.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package python-kde4.
Unpacking python-kde4 (from .../python-kde4_4%3a4.4.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package kdesudo.
Unpacking kdesudo (from .../kdesudo_3.4.2.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package gdebi-kde.
Unpacking gdebi-kde (from .../gdebi-kde_0.6.0ubuntu1_all.deb) ...
Selecting previously deselected package icoutils.
Unpacking icoutils (from .../icoutils_0.26.0-4ubuntu1_i386.deb) ...
Selecting previously deselected package install-package.
Unpacking install-package (from .../install-package_0.5.2_all.deb) ...
Selecting previously deselected package libkcddb4.
Unpacking libkcddb4 (from .../libkcddb4_4%3a4.4.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package kdemultimedia-kio-plugins.
Unpacking kdemultimedia-kio-plugins (from .../kdemultimedia-kio-plugins_4%3a4.4.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package libpackagekit-qt-12.
Unpacking libpackagekit-qt-12 (from .../libpackagekit-qt-12_0.5.7-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package polkit-kde-1.
Unpacking polkit-kde-1 (from .../polkit-kde-1_0.95.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package software-properties-kde.
Unpacking software-properties-kde (from .../software-properties-kde_0.75.10_all.deb) ...
Selecting previously deselected package libpackagekit-glib2-12.
Unpacking libpackagekit-glib2-12 (from .../libpackagekit-glib2-12_0.5.7-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package python-packagekit.
Unpacking python-packagekit (from .../python-packagekit_0.5.7-0ubuntu2.1_all.deb) ...
Selecting previously deselected package packagekit-backend-apt.
Unpacking packagekit-backend-apt (from .../packagekit-backend-apt_0.5.7-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package packagekit.
Unpacking packagekit (from .../packagekit_0.5.7-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package update-manager-kde.
Unpacking update-manager-kde (from .../update-manager-kde_1%3a0.134.10_all.deb) ...
Selecting previously deselected package kpackagekit.
Unpacking kpackagekit (from .../kpackagekit_0.5.4-0ubuntu4.3_i386.deb) ...
Selecting previously deselected package kubuntu-debug-installer.
Unpacking kubuntu-debug-installer (from .../kubuntu-debug-installer_10.04ubuntu4_i386.deb) ...
Selecting previously deselected package libqt4-sql-mysql.
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package libqt4-sql-sqlite.
Unpacking libqt4-sql-sqlite (from .../libqt4-sql-sqlite_4%3a4.6.2-0ubuntu5_i386.deb) ...
Selecting previously deselected package ttf-dejavu.
Unpacking ttf-dejavu (from .../ttf-dejavu_2.30-2_all.deb) ...
Selecting previously deselected package virtuoso-nepomuk.
Unpacking virtuoso-nepomuk (from .../virtuoso-nepomuk_6.1.0-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up nvidia-96 (96.43.17-0ubuntu1) ...
Removing old nvidia-96-96.43.17 DKMS files...

------------------------------
Deleting module version: 96.43.17
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-96-96.43.17 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-96/96.43.17/build/ for more information.
dpkg: error processing nvidia-96 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up libattica0 (0.1.3-0ubuntu1) ...

Setting up libdbusmenu-qt2 (0.3.2-0ubuntu1) ...

Setting up libqt4-script (4:4.6.2-0ubuntu5) ...

Setting up libqt4-designer (4:4.6.2-0ubuntu5) ...

Setting up libphonon4 (4:4.6.2-0ubuntu5) ...

Setting up libpolkit-qt-1-0 (0.95.1-1fakesync1) ...

Setting up libqt4-sql (4:4.6.2-0ubuntu5) ...

Setting up libqt4-qt3support (4:4.6.2-0ubuntu5) ...

Setting up libqt4-svg (4:4.6.2-0ubuntu5) ...

Setting up libqt4-xmlpatterns (4:4.6.2-0ubuntu5) ...

Setting up libqt4-webkit (4:4.6.2-0ubuntu5) ...

Setting up libclucene0ldbl (0.9.21b-2) ...

Setting up libiodbc2 (3.52.6-4) ...

Setting up soprano-daemon (2.4.2+dfsg.1-0ubuntu1.1) ...
Setting up libsoprano4 (2.4.2+dfsg.1-0ubuntu1.1) ...

Setting up libexiv2-6 (0.19-1) ...

Setting up libstreams0 (0.7.2-0ubuntu1) ...

Setting up libstreamanalyzer0 (0.7.2-0ubuntu1) ...

Setting up kdelibs5-data (4:4.4.2-0ubuntu4) ...

Setting up shared-desktop-ontologies (0.3-1) ...
Setting up amarok-common (2:2.3.0-0ubuntu4) ...
Setting up libtag-extras1 (1.0.1-2) ...

Setting up amarok-utils (2:2.3.0-0ubuntu4) ...
Setting up libxine1-bin (1.1.17-1ubuntu3) ...

Setting up libxine1-misc-plugins (1.1.17-1ubuntu3) ...

Setting up libxcb-shape0 (1.5-2) ...

Setting up libxcb-shm0 (1.5-2) ...

Setting up libxcb-xv0 (1.5-2) ...

Setting up libxine1-x (1.1.17-1ubuntu3) ...

Setting up libxine1-console (1.1.17-1ubuntu3) ...

Setting up libxine1 (1.1.17-1ubuntu3) ...

Setting up phonon-backend-xine (4:4.4.0-0ubuntu2) ...
Setting up libqca2 (2.0.2-1ubuntu2) ...

Setting up libqt4-opengl (4:4.6.2-0ubuntu5) ...

Setting up libssh-4 (0.4.2-1ubuntu1) ...

Setting up kdebase-runtime-data (4:4.4.2-0ubuntu4.1) ...

Setting up oxygen-icon-theme (4:4.4.2-0ubuntu2) ...
Setting up liblastfm0 (0.4.0~git20090710-1) ...

Setting up mysql-common (5.1.41-3ubuntu12.6) ...
Setting up libmysqlclient16 (5.1.41-3ubuntu12.6) ...

Setting up phonon (4:4.6.2-0ubuntu5) ...
Setting up libqtscript4-core (0.1.0-3build1) ...
Setting up libqtscript4-gui (0.1.0-3build1) ...
Setting up libqtscript4-network (0.1.0-3build1) ...
Setting up libqtscript4-xml (0.1.0-3build1) ...
Setting up libqtscript4-sql (0.1.0-3build1) ...
Setting up libqtscript4-uitools (0.1.0-3build1) ...
Setting up exiv2 (0.19-1) ...
Setting up libboost-program-options1.40.0 (1.40.0-4ubuntu4) ...

Setting up libakonadiprivate1 (1.3.1-0ubuntu3) ...

Setting up kdepimlibs-data (4:4.4.2-0ubuntu2.1) ...

Setting up libqt4-assistant (4:4.6.2-0ubuntu5) ...

Setting up libqt4-help (4:4.6.2-0ubuntu5) ...

Setting up libqt4-scripttools (4:4.6.2-0ubuntu5) ...

Setting up libqt4-test (4:4.6.2-0ubuntu5) ...

Setting up python-sip (4.10.1-0ubuntu1) ...

Setting up python-qt4 (4.7.2-0ubuntu1) ...

Setting up icoutils (0.26.0-4ubuntu1) ...
Setting up libpackagekit-qt-12 (0.5.7-0ubuntu2.1) ...

Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2.1) ...

Setting up python-packagekit (0.5.7-0ubuntu2.1) ...

Setting up libqt4-sql-mysql (4:4.6.2-0ubuntu5) ...
Setting up libqt4-sql-sqlite (4:4.6.2-0ubuntu5) ...
Setting up ttf-dejavu (2.30-2) ...
Setting up virtuoso-nepomuk (6.1.0-0ubuntu3) ...
Processing triggers for python-central ...
Setting up packagekit-backend-apt (0.5.7-0ubuntu2.1) ...
Generating mime/codec maps...

Processing triggers for python-central ...
Setting up packagekit (0.5.7-0ubuntu2.1) ...

Setting up ca-certificates-java (20100406ubuntu1) ...
creating /etc/ssl/certs/java/cacerts...
/var/lib/dpkg/info/ca-certificates-java.postinst: line 30: keytool: command not found
  error adding brasil.gov.br/brasil.gov.br.crt
  error adding cacert.org/cacert.org.crt
  error adding debconf.org/ca.crt
  error adding gouv.fr/cert_igca_dsa.crt
  error adding gouv.fr/cert_igca_rsa.crt
  error adding mozilla/ABAecom_=sub.__Am._Bankers_Assn.=_Root_CA.crt
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_1.crt
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_2.crt
  error adding mozilla/AddTrust_External_Root.crt
  error adding mozilla/AddTrust_Low-Value_Services_Root.crt
  error adding mozilla/AddTrust_Public_Services_Root.crt
  error adding mozilla/AddTrust_Qualified_Certificates_Root.crt
  error adding mozilla/America_Online_Root_Certification_Authority_1.crt
  error adding mozilla/America_Online_Root_Certification_Authority_2.crt
  error adding mozilla/Baltimore_CyberTrust_Root.crt
  error adding mozilla/COMODO_Certification_Authority.crt
  error adding mozilla/COMODO_ECC_Certification_Authority.crt
  error adding mozilla/Camerfirma_Chambers_of_Commerce_Root.crt
  error adding mozilla/Camerfirma_Global_Chambersign_Root.crt
  error adding mozilla/Certplus_Class_2_Primary_CA.crt
  error adding mozilla/Certum_Root_CA.crt
  error adding mozilla/Comodo_AAA_Services_root.crt
  error adding mozilla/Comodo_Secure_Services_root.crt
  error adding mozilla/Comodo_Trusted_Services_root.crt
  error adding mozilla/DST_ACES_CA_X6.crt
  error adding mozilla/DST_Root_CA_X3.crt
  error adding mozilla/DigiCert_Assured_ID_Root_CA.crt
  error adding mozilla/DigiCert_Global_Root_CA.crt
  error adding mozilla/DigiCert_High_Assurance_EV_Root_CA.crt
  error adding mozilla/DigiNotar_Root_CA.crt
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_1.crt
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_2.crt
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_3.crt
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_4.crt
  error adding mozilla/Entrust.net_Global_Secure_Personal_CA.crt
  error adding mozilla/Entrust.net_Global_Secure_Server_CA.crt
  error adding mozilla/Entrust.net_Premium_2048_Secure_Server_CA.crt
  error adding mozilla/Entrust.net_Secure_Personal_CA.crt
  error adding mozilla/Entrust.net_Secure_Server_CA.crt
  error adding mozilla/Entrust_Root_Certification_Authority.crt
  error adding mozilla/Equifax_Secure_CA.crt
  error adding mozilla/Equifax_Secure_Global_eBusiness_CA.crt
  error adding mozilla/Equifax_Secure_eBusiness_CA_1.crt
  error adding mozilla/Equifax_Secure_eBusiness_CA_2.crt
  error adding mozilla/Firmaprofesional_Root_CA.crt
  error adding mozilla/GTE_CyberTrust_Global_Root.crt
  error adding mozilla/GTE_CyberTrust_Root_CA.crt
  error adding mozilla/GeoTrust_Global_CA.crt
  error adding mozilla/GeoTrust_Global_CA_2.crt
  error adding mozilla/GeoTrust_Primary_Certification_Authority.crt
  error adding mozilla/GeoTrust_Universal_CA.crt
  error adding mozilla/GeoTrust_Universal_CA_2.crt
  error adding mozilla/GlobalSign_Root_CA.crt
  error adding mozilla/GlobalSign_Root_CA_-_R2.crt
  error adding mozilla/Go_Daddy_Class_2_CA.crt
  error adding mozilla/IPS_CLASE1_root.crt
  error adding mozilla/IPS_CLASE3_root.crt
  error adding mozilla/IPS_CLASEA1_root.crt
  error adding mozilla/IPS_CLASEA3_root.crt
  error adding mozilla/IPS_Chained_CAs_root.crt
  error adding mozilla/IPS_Servidores_root.crt
  error adding mozilla/IPS_Timestamping_root.crt
  error adding mozilla/NetLock_Business_=Class_B=_Root.crt
  error adding mozilla/NetLock_Express_=Class_C=_Root.crt
  error adding mozilla/NetLock_Notary_=Class_A=_Root.crt
  error adding mozilla/NetLock_Qualified_=Class_QA=_Root.crt
  error adding mozilla/Network_Solutions_Certificate_Authority.crt
  error adding mozilla/QuoVadis_Root_CA.crt
  error adding mozilla/QuoVadis_Root_CA_2.crt
  error adding mozilla/QuoVadis_Root_CA_3.crt
  error adding mozilla/RSA_Root_Certificate_1.crt
  error adding mozilla/RSA_Security_1024_v3.crt
  error adding mozilla/RSA_Security_2048_v3.crt
  error adding mozilla/SecureTrust_CA.crt
  error adding mozilla/Secure_Global_CA.crt
  error adding mozilla/Security_Communication_Root_CA.crt
  error adding mozilla/Sonera_Class_1_Root_CA.crt
  error adding mozilla/Sonera_Class_2_Root_CA.crt
  error adding mozilla/Staat_der_Nederlanden_Root_CA.crt
  error adding mozilla/Starfield_Class_2_CA.crt
  error adding mozilla/StartCom_Certification_Authority.crt
  error adding mozilla/StartCom_Ltd..crt
  error adding mozilla/SwissSign_Gold_CA_-_G2.crt
  error adding mozilla/SwissSign_Platinum_CA_-_G2.crt
  error adding mozilla/SwissSign_Silver_CA_-_G2.crt
  error adding mozilla/Swisscom_Root_CA_1.crt
  error adding mozilla/TC_TrustCenter__Germany__Class_2_CA.crt
  error adding mozilla/TC_TrustCenter__Germany__Class_3_CA.crt
  error adding mozilla/TDC_Internet_Root_CA.crt
  error adding mozilla/TDC_OCES_Root_CA.crt
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_1.crt
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_2.crt
  error adding mozilla/Taiwan_GRCA.crt
  error adding mozilla/Thawte_Personal_Basic_CA.crt
  error adding mozilla/Thawte_Personal_Freemail_CA.crt
  error adding mozilla/Thawte_Personal_Premium_CA.crt
  error adding mozilla/Thawte_Premium_Server_CA.crt
  error adding mozilla/Thawte_Server_CA.crt
  error adding mozilla/Thawte_Time_Stamping_CA.crt
  error adding mozilla/UTN-USER_First-Network_Applications.crt
  error adding mozilla/UTN_DATACorp_SGC_Root_CA.crt
  error adding mozilla/UTN_USERFirst_Email_Root_CA.crt
  error adding mozilla/UTN_USERFirst_Hardware_Root_CA.crt
  error adding mozilla/ValiCert_Class_1_VA.crt
  error adding mozilla/ValiCert_Class_2_VA.crt
  error adding mozilla/VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.crt
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority.crt
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority.crt
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Verisign_RSA_Secure_Server_CA.crt
  error adding mozilla/Verisign_Time_Stamping_Authority_CA.crt
  error adding mozilla/Visa_International_Global_Root_2.crt
  error adding mozilla/Visa_eCommerce_Root.crt
  error adding mozilla/WellsSecure_Public_Root_Certificate_Authority.crt
  error adding mozilla/Wells_Fargo_Root_CA.crt
  error adding mozilla/XRamp_Global_CA_Root.crt
  error adding mozilla/beTRUSTed_Root_CA-Baltimore_Implementation.crt
  error adding mozilla/beTRUSTed_Root_CA.crt
  error adding mozilla/beTRUSTed_Root_CA_-_Entrust_Implementation.crt
  error adding mozilla/beTRUSTed_Root_CA_-_RSA_Implementation.crt
  error adding mozilla/thawte_Primary_Root_CA.crt
  error adding signet.pl/signet_ca1_pem.crt
  error adding signet.pl/signet_ca2_pem.crt
  error adding signet.pl/signet_ca3_pem.crt
  error adding signet.pl/signet_ocspklasa2_pem.crt
  error adding signet.pl/signet_ocspklasa3_pem.crt
  error adding signet.pl/signet_pca2_pem.crt
  error adding signet.pl/signet_pca3_pem.crt
  error adding signet.pl/signet_rootca_pem.crt
  error adding signet.pl/signet_tsa1_pem.crt
  error adding spi-inc.org/spi-ca-2003.crt
  error adding spi-inc.org/spi-cacert-2008.crt
  error adding telesec.de/deutsche-telekom-root-ca-2.crt
failed (VM used: java-6-sun).
dpkg: error processing ca-certificates-java (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openjdk-6-jre-headless (6b18-1.8.1-0ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk/jre/bin/java doesn't exist.
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up kdelibs-bin (4:4.4.2-0ubuntu4) ...
Setting up kdelibs5 (4:4.4.2-0ubuntu4) ...

Setting up libplasma3 (4:4.4.2-0ubuntu4) ...

Setting up plasma-scriptengine-javascript (4:4.4.2-0ubuntu4.1) ...
Setting up kdepimlibs5 (4:4.4.2-0ubuntu2.1) ...

Setting up kdebase-runtime (4:4.4.2-0ubuntu4.1) ...
update-alternatives: using /usr/lib/kde4/libexec/kdesu-distrib/kdesu to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.

Setting up amarok (2:2.3.0-0ubuntu4) ...

Setting up python-kde4 (4:4.4.2-0ubuntu2) ...

Setting up kdesudo (3.4.2.3-0ubuntu1) ...
update-alternatives: using /usr/bin/kdesudo to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.

Setting up gdebi-kde (0.6.0ubuntu1) ...

Setting up libkcddb4 (4:4.4.2-0ubuntu3) ...

Setting up kdemultimedia-kio-plugins (4:4.4.2-0ubuntu3) ...

Setting up polkit-kde-1 (0.95.1-2ubuntu1) ...
Setting up update-manager-kde (1:0.134.10) ...

Processing triggers for python-central ...
Setting up install-package (0.5.2) ...
Setting up software-properties-kde (0.75.10) ...

Processing triggers for python-central ...
Setting up kpackagekit (0.5.4-0ubuntu4.3) ...
Setting up kubuntu-debug-installer (10.04ubuntu4) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-96
 ca-certificates-java
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 icedtea6-plugin
Setting up nvidia-96 (96.43.17-0ubuntu1) ...
Removing old nvidia-96-96.43.17 DKMS files...

------------------------------
Deleting module version: 96.43.17
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-96-96.43.17 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-96/96.43.17/build/ for more information.
dpkg: error processing nvidia-96 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up openjdk-6-jre-headless (6b18-1.8.1-0ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk/jre/bin/java doesn't exist.
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-96
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 icedtea6-plugin
 ca-certificates-java

```

---

### Post by sikander3786 on 2010-08-31
There are a few unmet dependencies. Try

```

sudo apt-get install -f

```

And post back any error messages.

---

### Post by supermooshman on 2010-08-31
> **sikander3786 said:**
> There are a few unmet dependencies. Try

```

sudo apt-get install -f

```

And post back any error messages.


I got this output:
```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nvidia-96 (96.43.17-0ubuntu1) ...
Removing old nvidia-96-96.43.17 DKMS files...

------------------------------
Deleting module version: 96.43.17
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-96-96.43.17 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-96/96.43.17/build/ for more information.
dpkg: error processing nvidia-96 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up openjdk-6-jre-headless (6b18-1.8.1-0ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk/jre/bin/java doesn't exist.
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-96
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 icedtea6-plugin
 ca-certificates-java
```


thanks

---

### Post by sikander3786 on 2010-08-31
Ok. Now try reconfiguring dpkg by

```

sudo dpkg --configure -a

```

---

### Post by supermooshman on 2010-08-31
> **sikander3786 said:**
> Ok. Now try reconfiguring dpkg by

```

sudo dpkg --configure -a

```


another error :(:
```

Setting up nvidia-96 (96.43.17-0ubuntu1) ...
Removing old nvidia-96-96.43.17 DKMS files...

------------------------------
Deleting module version: 96.43.17
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-96-96.43.17 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-96/96.43.17/build/ for more information.
dpkg: error processing nvidia-96 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up openjdk-6-jre-headless (6b18-1.8.1-0ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk/jre/bin/java doesn't exist.
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8.1-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-96
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 icedtea6-plugin
 ca-certificates-java
```

---

### Post by sikander3786 on 2010-08-31
Go to Synaptic >>> Custom Filters >>> Broken and see if any packages are listed there. Try to remove or reconfigure from there.

Also please take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=1557182](http://ubuntuforums.org/showthread.php?t=1557182)

---


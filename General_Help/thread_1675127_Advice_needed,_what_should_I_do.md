---
title: "Advice needed, what should I do?"
date: 2011-01-25
forum: General Help
---

### Post by TDK800 on 2011-01-25
[B]When I try to update packages on web server, it gives error:
[/B]

sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.28-16-server: Depends: linux-restricted-modules-common which is a virtual package.
  linux-restricted-modules-2.6.27-15-server: Depends: linux-restricted-modules-common which is a virtual package.




[B]When I try to install the missing package:
[/B]


sudo aptitude install linux-restricted-modules-common
Reading package lists... Done



Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for linux-restricted-modules-common
No candidate version found for linux-restricted-modules-common
The following packages are BROKEN:
  linux-restricted-modules-2.6.27-15-server linux-restricted-modules-2.6.28-16-server 
The following packages will be REMOVED:
  binutils-static{u} ca-certificates-java{u} default-jre{u} default-jre-headless{u} defoma{u} fontconfig{u} fontconfig-config{u} hicolor-icon-theme{u} 
  icedtea-6-jre-cacao{u} java-common{u} latex-xft-fonts{u} libaccess-bridge-java{u} libaccess-bridge-java-jni{u} libasound2{u} libatk1.0-0{u} libatk1.0-data{u} 
  libavahi-client3{u} libavahi-common-data{u} libavahi-common3{u} libbind9-50{u} libcairo2{u} libcolamd2.7.1{u} libcompress-bzip2-perl{u} libcups2{u} libdatrie1{u} 
  libdirectfb-1.2-0{u} libdns53{u} libevent-1.4-2{u} libflac8{u} libfontconfig1{u} libfontenc1{u} libgif4{u} libgraphite3{u} libgstreamer-plugins-base0.10-0{u} 
  libgstreamer0.10-0{u} libgtk2.0-0{u} libgtk2.0-bin{u} libgtk2.0-common{u} libhsqldb-java{u} libhunspell-1.2-0{u} libhyphen0{u} libice6{u} libicu40{u} libicu42{u} 
  libisc50{u} libisccc50{u} libisccfg50{u} libjasper1{u} libjs-jquery{u} libkadm5clnt6{u} liblcms1{u} liblwres50{u} libneon27-gnutls{u} libnspr4-0d{u} libnss3-1d{u} 
  libntfs-3g54{u} libogg0{u} libpango1.0-0{u} libpango1.0-common{u} libpixman-1-0{u} libpq5{u} libpulse0{u} libraptor1{u} librasqal1{u} librasqal2{u} librdf0{u} 
  libservlet2.4-java{u} libservlet2.5-java{u} libsm6{u} libsndfile1{u} libthai-data{u} libthai0{u} libtiff4{u} libts-0.0-0{u} libunbound1{u} libvorbis0a{u} libvorbisenc2{u} 
  libwpd8c2a{u} libwpg-0.1-1{u} libwps-0.1-1{u} libxaw7{u} libxcb-render-util0{u} libxcb-render0{u} libxcomposite1{u} libxcursor1{u} libxdamage1{u} libxfixes3{u} 
  libxfont1{u} libxft2{u} libxi6{u} libxinerama1{u} libxmu6{u} libxpm4{u} libxrandr2{u} libxrender1{u} libxslt1.1{u} libxt6{u} libxtst6{u} lp-solve{u} openjdk-6-jre{u} 
  openjdk-6-jre-headless{u} openjdk-6-jre-lib{u} openoffice.org{u} openoffice.org-base{u} openoffice.org-base-core{u} openoffice.org-calc{u} openoffice.org-common{u} 
  openoffice.org-core{u} openoffice.org-draw{u} openoffice.org-emailmerge{u} openoffice.org-filter-binfilter{u} openoffice.org-filter-mobiledev{u} 
  openoffice.org-hyphenation{u} openoffice.org-hyphenation-en-us{u} openoffice.org-impress{u} openoffice.org-java-common{u} openoffice.org-math{u} 
  openoffice.org-officebean{u} openoffice.org-report-builder-bin{u} openoffice.org-style-galaxy{u} openoffice.org-thesaurus-en-au{u} openoffice.org-thesaurus-en-us{u} 
  openoffice.org-writer{u} python-uno{u} raptor-utils{u} redland-utils{u} tsconf{u} ttf-dejavu{u} ttf-dejavu-core{u} ttf-dejavu-extra{u} ttf-liberation{u} ttf-opensymbol{u} 
  ttf-sil-gentium{u} ttf-sil-gentium-basic{u} tzdata-java{u} uno-libs3{u} ure{u} x-ttcidfont-conf{u} x11-common{u} xfonts-encodings{u} xfonts-mathml{u} xfonts-utils{u} 
0 packages upgraded, 0 newly installed, 142 to remove and 107 not upgraded.
Need to get 0B of archives. After unpacking 579MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.28-16-server: Depends: linux-restricted-modules-common which is a virtual package.
  linux-restricted-modules-2.6.27-15-server: Depends: linux-restricted-modules-common which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
linux-restricted-modules-2.6.27-15-server
linux-restricted-modules-2.6.28-16-server

Score is 188

Accept this solution? [Y/n/q/?]



**How should I solve it?**

---

### Post by dcstar on 2011-01-25
> **TDK800 said:**
> When I try to **update** packages on web server, it gives error:

sudo aptitude safe-**upgrade**
.........

An **upgrade** is **not** an **update**, what actually are you trying to do?

---

### Post by TDK800 on 2011-01-27
upgrade

It just seems unusual that an upgrade would want to remove 142 packages and free up 579MB, especially as it's not a distro-upgrade.

---


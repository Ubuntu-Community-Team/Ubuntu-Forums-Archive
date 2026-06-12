---
title: "Electricsheep = blank screen"
date: 2010-06-24
forum: General Help
---

### Post by Mathieu147 on 2010-06-24
Hi,

I installed Electricsheep. When I go to System &#8594; Preferences &#8594; Screensaver and choose "Electricsheep", I can see the preview.

If I click on "Preview", I can see the screensaver running fine.

But when my screensaver really starts (or whenever I start it manually by locking the screen), all I have is a blanck screen :confused:

Would you guys have a solution?

Thanks!

---

### Post by wilee-nilee on 2010-06-24
The site download works.
[http://electricsheep.org/](http://electricsheep.org/)

---

### Post by Mathieu147 on 2010-06-24
> **wilee-nilee said:**
> The site download works.
[http://electricsheep.org/](http://electricsheep.org/)

On the site they say to use the version that is in the repositeries... But I'll try, thanks.

---

### Post by wilee-nilee on 2010-06-24
> **Mathieu147 said:**
> On the site they say to use the version that is in the repositeries... But I'll try, thanks.

Hey do what you want but I have used electric sheep on several computers and it always works with the site download, and just the install from the Ubuntu repo has the same black screen. I think the Ubuntu one works it just takes configuring, that is included in the site download.

---

### Post by Mathieu147 on 2010-06-24
I went to the site and downloaded the script. I saw it makes me install billions of packages, including developpment packages. Then it just "make install".

I thought I didn't want a "dirty" install like this, so I begun setting up a virtual machine to install all that stuff and make a deb package with checkinstall.

I left my computer alone during the reboot of the virtual machine after installing the guest additions, and when I came back, my screensaver was working :D

I did absolutely nothing, but now it works. Pretty strange, but I don't really care as long as it works...

---

### Post by WorMzy on 2010-06-24
I've found that a fresh install of Electricsheep often has a "blank" period where it doesn't show anything, but, as you've found out, it doesn't last too long.

---

### Post by spotspot on 2010-06-24
> **Mathieu147 said:**
> I went to the site and downloaded the script. I saw it makes me install billions of packages, including developpment packages. Then it just "make install". ...

I did absolutely nothing, but now it works. Pretty strange, but I don't really care as long as it works...

It's now available by synaptic, you don't have to compile from src, ust "sudo apt-get install electricsheep".

---

### Post by wilee-nilee on 2010-06-24
> **Mathieu147 said:**
> I went to the site and downloaded the script.** I saw it makes me install billions of packages, including developpment packages.** Then it just "make install".

I thought I didn't want a "dirty" install like this, so I begun setting up a virtual machine to install all that stuff and make a deb package with checkinstall.

I left my computer alone during the reboot of the virtual machine after installing the guest additions, and when I came back, my screensaver was working :D

I did absolutely nothing, but now it works. Pretty strange, but I don't really care as long as it works...

This is hilarious.

---

### Post by Mathieu147 on 2010-06-24
> **wilee-nilee said:**
> This is hilarious.

:mrgreen: but (almost) true!

This is what the script wanted me to install:
[LIST]
[*]mplayer
[*]curl
[*]subversion
[*]libtool
[*]libjpeg-dev
[*]libdbus-glib-1-dev
[*]libgconf2-dev
[*]libavformat-dev
[*]libgnome-menu-dev
[*]libglade2-dev
[*]libgnomeui-dev
[/LIST]

And when I ask apt-get to do it:

```
mathieu@mathieu-desktop:~$ sudo apt-get install mplayer curl subversion libtool libjpeg-dev libdbus-glib-1-dev libgconf2-dev libavformat-dev libgnome-menu-dev libglade2-dev libgnomeui-dev
[sudo] password for mathieu: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
curl est déjà la plus récente version disponible.
curl passé en «*installé manuellement*».
subversion est déjà la plus récente version disponible.
Note, sélection de libjpeg62-dev au lieu de libjpeg-dev
Les paquets supplémentaires suivants seront installés*: 
  autotools-dev build-essential cvs debhelper dpkg-dev g++ g++-4.4 gettext
  html2text intltool-debian libart-2.0-dev libatk1.0-dev libaudiofile-dev
  libavahi-client-dev libavahi-common-dev libavahi-glib-dev libavcodec-dev
  libavutil-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev libdbus-1-dev
  libdirectfb-dev libdirectfb-extra libesd0-dev libexpat1-dev libfaac0
  libfontconfig1-dev libfreetype6-dev libgail-dev libgcrypt11-dev
  libglib2.0-dev libgnome-keyring-dev libgnome2-dev libgnomecanvas2-dev
  libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgtk2.0-dev libice-dev
  libidl-dev libjpeg62-dev libltdl-dev libmail-sendmail-perl liborbit2-dev
  libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev libpthread-stubs0
  libpthread-stubs0-dev libselinux1-dev libsepol1-dev libsm-dev
  libstdc++6-4.4-dev libsys-hostname-long-perl libsysfs-dev libtasn1-3-dev
  libx11-dev libxau-dev libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev
  libxrender-dev orbit2 po-debconf x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev xz-utils zlib1g-dev
Paquets suggérés*:
  dh-make debian-keyring debian-maintainers g++-multilib g++-4.4-multilib
  gcc-4.4-doc libstdc++6-4.4-dbg gettext-doc libfaad-dev libgsm1-dev
  libogg-dev libschroedinger-dev libspeex-dev libtheora-dev libvorbis-dev
  libraw1394-dev libdc1394-22-dev libcairo2-doc libgail-doc libgcrypt11-doc
  glade glade-gnome libglib2.0-doc python-subunit libgnome2-doc
  libgnomecanvas2-doc libgnomeui-doc gnutls-doc gnutls-bin guile-gnutls
  libgtk2.0-doc libtool-doc libpango1.0-doc libstdc++6-4.4-doc autoconf
  automaken gfortran fortran95-compiler gcj mplayer-doc netselect fping
  libmail-box-perl
Les NOUVEAUX paquets suivants seront installés*:
  autotools-dev build-essential cvs debhelper dpkg-dev g++ g++-4.4 gettext
  html2text intltool-debian libart-2.0-dev libatk1.0-dev libaudiofile-dev
  libavahi-client-dev libavahi-common-dev libavahi-glib-dev libavcodec-dev
  libavformat-dev libavutil-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev
  libdbus-1-dev libdbus-glib-1-dev libdirectfb-dev libdirectfb-extra
  libesd0-dev libexpat1-dev libfaac0 libfontconfig1-dev libfreetype6-dev
  libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libglib2.0-dev
  libgnome-keyring-dev libgnome-menu-dev libgnome2-dev libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgtk2.0-dev
  libice-dev libidl-dev libjpeg62-dev libltdl-dev libmail-sendmail-perl
  liborbit2-dev libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev
  libpthread-stubs0 libpthread-stubs0-dev libselinux1-dev libsepol1-dev
  libsm-dev libstdc++6-4.4-dev libsys-hostname-long-perl libsysfs-dev
  libtasn1-3-dev libtool libx11-dev libxau-dev libxcb-render-util0-dev
  libxcb-render0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev orbit2 po-debconf
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev
  xz-utils zlib1g-dev
Les paquets suivants seront mis à jour*:
  mplayer
1 mis à jour, 97 nouvellement installés, 0 à enlever et 14 non mis à jour.
Il est nécessaire de prendre 41,1Mo dans les archives.
Après cette opération, 139Mo d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? 

```
97 packages (139 Mb) for **one** screensaver...

So I'm happy the version from the repositeries finally works.

---


---
title: "aptitude vs apt-get"
date: 2009-10-06
forum: General Help
---

### Post by dino99 on 2009-10-06
hi all,

today i spend time to clean my system; it's work smoothly but each week i check it.

so after doing updates, i clean the cache & end with apt-get install -f: cool, all is ok. Looking at synaptic, nothing broken. neither orphans. well everything seem perfect. At this time, don't know why but i run sudo aptitude install -f: can't believe it, it saying that lots of packages are broken, dependencies missing & need to remove packages.

Curious don't you ?

here is the output:

 oem@Mubuntu:~$ sudo apt-get install -f
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.


oem@Mubuntu:~$ sudo aptitude install -f
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait
Écriture de l'information d'état étendu... Fait
Les paquets suivants sont CASSÉS*:
  audacious-plugins audacious-plugins-extra avidemux bogofilter-bdb build-essential clamav-freshclam cpp-4.3 
  g++-4.3 gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-pulseaudio guile-1.8-libs 
  libasound2-plugins libavcodec-unstripped-52 libggi2 libgmyth0 libgpod-common libgraphviz4 libimlib2 libmpfr1ldbl 
  libpulse-browse0 libpulse-mainloop-glib0 librpm4.4 libstdc++6-4.3-dev libwxgtk2.8-0 lintian lsb-core 
  microcode.ctl mpg321 mplayer openoffice.org-java-common padevchooser paman pavucontrol pavumeter pulseaudio 
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 
  pulseaudio-module-zeroconf pulseaudio-utils python-wxgtk2.8 seahorse seahorse-plugins streamripper 
  sun-java6-fonts sun-java6-plugin ttf-mscorefonts-installer vlc-nox 
Les paquets suivants seront ENLEVÉS*:
  alien bogofilter bogofilter-common cabextract clamav-base debhelper dpkg-dev fakeroot flashplugin-installer{u} 
  flashplugin-nonfree gdesklets{u} gdesklets-data gettext gstreamer0.10-plugins-ugly html2text intltool-debian 
  java-common liba52-0.7.4 libbeecrypt6 libc6-dev libfaac0 libgd2-xpm libgii1 libgii1-target-x libgmp3c2 libgpgme11 
  libhttrack2{u} libid3tag0 libmad0 libmpcdec3 libmpeg2-4 libmysqlclient15off libpth20 libpulse0 libsgutils1 
  libsidplay1 libwxbase2.8-0 libxvidcore4 libxvmc1 linux-libc-dev lsscsi mplayer-skins mysql-common po-debconf 
  python-wxversion rpm sg3-utils sun-java6-bin sun-java6-jre ubuntu-restricted-extras unrar webhttrack 
  webhttrack-common{u} 
0 paquets mis à jour, 0 nouvellement installés, 53 à enlever et 0 non mis à jour.
Il est nécessaire de télécharger 0o d'archives. Après dépaquetage, 198Mo seront libérés.
Les paquets suivants ont des dépendances non satisfaites*:
  libstdc++6-4.3-dev: Dépend: libc6-dev (>= 2.5) mais il n'est pas installable
  sun-java6-plugin: Dépend: sun-java6-bin (= 6-16-0ubuntu1.9.04) mais il n'est pas installable
  openoffice.org-java-common: Dépend: default-jre mais il n'est pas installable ou
                                       java-gcj-compat mais il n'est pas installable ou
                                       openjdk-6-jre mais il n'est pas installable ou
                                       sun-java5-jre mais il n'est pas installable ou
                                       sun-java6-jre mais il n'est pas installable
  pulseaudio: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  avidemux: Dépend: libfaac0 (>= 1.26) mais il n'est pas installable
            Dépend: libpulse0 mais il n'est pas installable
            Dépend: libxvidcore4 (>= 1:1.0.0-0.0) mais il n'est pas installable
  g++-4.3: Dépend: libgmp3c2 mais il n'est pas installable
  libwxgtk2.8-0: Dépend: libwxbase2.8-0 (>= 2.8.9.1) mais il n'est pas installable
  clamav-freshclam: Dépend: clamav-base (>= 0.95.2+dfsg-4ubuntu1.2) mais il n'est pas installable
  streamripper: Dépend: libmad0 (>= 0.15.1b-3) mais il n'est pas installable
  mplayer: Dépend: libfaac0 (>= 1.26) mais il n'est pas installable
           Dépend: libmad0 (>= 0.15.1b-3) mais il n'est pas installable
           Dépend: libmpcdec3 mais il n'est pas installable
           Dépend: libpulse0 (>= 0.9.14) mais il n'est pas installable
           Dépend: libxvidcore4 (>= 1:1.0.0-0.0) mais il n'est pas installable
           Dépend: libxvmc1 mais il n'est pas installable
           Dépend: mplayer-skins mais il n'est pas installable
  seahorse: Dépend: libgpgme11 (>= 1.1.8) mais il n'est pas installable
  microcode.ctl: Dépend: po-debconf mais il n'est pas installable
  gstreamer0.10-plugins-bad-multiverse: Dépend: libfaac0 (>= 1.26) mais il n'est pas installable
                                        Dépend: libxvidcore4 (>= 1:1.0.0-0.0) mais il n'est pas installable
  libpulse-mainloop-glib0: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  sun-java6-fonts: Dépend: sun-java6-jre (>= 6-16-0ubuntu1.9.04) mais il n'est pas installable
  seahorse-plugins: Dépend: libgpgme11 (>= 1.1.8) mais il n'est pas installable
  audacious-plugins: Dépend: libmad0 (>= 0.15.1b-3) mais il n'est pas installable
                     Dépend: libpulse0 (>= 0.9.14) mais il n'est pas installable
  libavcodec-unstripped-52: Dépend: libfaac0 (>= 1.26) mais il n'est pas installable
                            Dépend: libxvidcore4 (>= 1:1.0.0-0.0) mais il n'est pas installable
  pavucontrol: Dépend: libpulse0 (>= 0.9.15~test1) mais il n'est pas installable
  guile-1.8-libs: Dépend: libgmp3c2 mais il n'est pas installable
  librpm4.4: Dépend: libbeecrypt6 mais il n'est pas installable
  vlc-nox: Dépend: liba52-0.7.4 mais il n'est pas installable
           Dépend: libid3tag0 (>= 0.15.1b) mais il n'est pas installable
           Dépend: libmad0 (>= 0.15.1b-3) mais il n'est pas installable
           Dépend: libmpcdec3 mais il n'est pas installable
           Dépend: libmpeg2-4 mais il n'est pas installable
  libggi2: Dépend: libgii1 mais il n'est pas installable
  pulseaudio-module-hal: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  gstreamer0.10-pulseaudio: Dépend: libpulse0 (>= 0.9.14) mais il n'est pas installable
  pulseaudio-module-x11: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  bogofilter-bdb: Dépend: bogofilter-common mais il n'est pas installable
  ttf-mscorefonts-installer: Dépend: cabextract mais il n'est pas installable
  pulseaudio-utils: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  gstreamer0.10-plugins-bad: Dépend: libmpcdec3 mais il n'est pas installable
  libgpod-common: Dépend: libsgutils1 (>= 1.24) mais il n'est pas installable
  audacious-plugins-extra: Dépend: libmpcdec3 mais il n'est pas installable
  libmpfr1ldbl: Dépend: libgmp3c2 (>= 4.2.dfsg-1) mais il n'est pas installable
  pulseaudio-module-zeroconf: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  libasound2-plugins: Dépend: libpulse0 (>= 0.9.15~test1) mais il n'est pas installable
  padevchooser: Dépend: libpulse0 (>= 0.9.14) mais il n'est pas installable
  paman: Dépend: libpulse0 (>= 0.9.14) mais il n'est pas installable
  pulseaudio-module-gconf: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  mpg321: Dépend: libid3tag0 (>= 0.15.1b) mais il n'est pas installable
          Dépend: libmad0 (>= 0.15.1b-3) mais il n'est pas installable
  libgmyth0: Dépend: libmysqlclient15off (>= 5.0.27-1) mais il n'est pas installable
  cpp-4.3: Dépend: libgmp3c2 mais il n'est pas installable
  libpulse-browse0: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  python-wxgtk2.8: Dépend: python-wxversion (>= 2.8.9.1-0ubuntu6) mais il n'est pas installable
                   Dépend: libwxbase2.8-0 (>= 2.8.9.1) mais il n'est pas installable
  libimlib2: Dépend: libid3tag0 (>= 0.15.1b) mais il n'est pas installable
  lsb-core: Dépend: libc6-dev mais il n'est pas installable ou
                     libc-dev qui est un paquet virtuel
            Dépend: alien (>= 8.36) mais il n'est pas installable
  pavumeter: Dépend: libpulse0 (>= 0.9.8) mais il n'est pas installable
  libgraphviz4: Dépend: libgd2-noxpm (>= 2.0.36~rc1~dfsg) mais il n'est pas installable ou
                         libgd2-xpm (>= 2.0.36~rc1~dfsg) mais il n'est pas installable
  lintian: Dépend: dpkg-dev (>= 1.13.17) mais il n'est pas installable
           Dépend: gettext (>= 0.16) mais il n'est pas installable
           Dépend: intltool-debian mais il n'est pas installable
  pulseaudio-esound-compat: Dépend: libpulse0 (= 1:0.9.15-3ubuntu1~ppa2) mais il n'est pas installable
  build-essential: Dépend: libc6-dev mais il n'est pas installable ou
                            libc-dev qui est un paquet virtuel
                   Dépend: dpkg-dev (>= 1.13.5) mais il n'est pas installable
Les actions suivantes permettront de résoudre ces dépendances*:

Supprimer les paquets suivants*:
openoffice.org-java-common
sun-java6-fonts
sun-java6-plugin

Conserver les paquets suivants dans leur version actuelle*:
alien [8.73 (jaunty, now)]
bogofilter-common [1.1.7-1ubuntu1 (jaunty, now)]
cabextract [1.2-3 (jaunty, now)]
clamav-base [0.95.2+dfsg-4ubuntu1.2 (jaunty-updates, now)]
debhelper [7.0.17ubuntu4 (jaunty, now)]
dpkg-dev [1.14.24ubuntu1 (jaunty, now)]
gettext [0.17-6ubuntu2 (jaunty, now)]
html2text [1.3.2a-5 (jaunty, now)]
intltool-debian [0.35.0+20060710.1 (jaunty, now)]
liba52-0.7.4 [0.7.4-11ubuntu1 (jaunty, now)]
libbeecrypt6 [4.1.2-7 (jaunty, now)]
libc6-dev [2.9-4ubuntu6.1 (jaunty-updates, now)]
libfaac0 [1.26-0.1ubuntu2 (jaunty, now)]
libgd2-xpm [2.0.36~rc1~dfsg-3ubuntu1 (jaunty, now)]
libgii1 [1:1.0.2-4 (jaunty, now)]
libgii1-target-x [1:1.0.2-4 (jaunty, now)]
libgmp3c2 [2:4.2.4+dfsg-2ubuntu1 (jaunty, now)]
libgpgme11 [1.1.8-2ubuntu3 (jaunty, now)]
libid3tag0 [0.15.1b-10 (jaunty, now)]
libmad0 [0.15.1b-4 (jaunty, now)]
libmpcdec3 [1.2.2-1build1 (jaunty, now)]
libmpeg2-4 [0.4.1-3 (jaunty, now)]
libmysqlclient15off [5.1.30really5.0.75-0ubuntu10.2 (jaunty-updates, now)]
libpth20 [2.0.7-12 (jaunty, now)]
libpulse0 [1:0.9.15-3ubuntu1~ppa2 (jaunty, now)]
libsgutils1 [1.24-2 (jaunty, now)]
libwxbase2.8-0 [2.8.9.1-0ubuntu6 (jaunty, now)]
libxvidcore4 [2:1.1.2-0.1ubuntu3 (jaunty, now)]
libxvmc1 [2:1.0.4-2ubuntu1 (jaunty, now)]
linux-libc-dev [2.6.28-15.52 (jaunty-updates, now)]
mplayer-skins [2-7 (jaunty, now)]
mysql-common [5.1.30really5.0.75-0ubuntu10.2 (jaunty-updates, now)]
po-debconf [1.0.15ubuntu1 (jaunty, now)]
python-wxversion [2.8.9.1-0ubuntu6 (jaunty, now)]
rpm [4.4.2.3-2ubuntu1 (jaunty, now)]
sg3-utils [1.24-2 (jaunty, now)]

Le score est de 655

Accepter cette solution*? [Y/n/q/?]

Can we seriouly believe in aptitude ?

---


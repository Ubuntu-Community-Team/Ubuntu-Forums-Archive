---
title: "Synaptic wants to remove everything for libogg0"
date: 2011-04-15
forum: General Help
---

### Post by statistic on 2011-04-15
EDIT: Ohhh I see. It's that all there things rely on libogg. I just wanted to reinstall it really, but I guess there's a proper way to do that. :P


This... is pretty messed up, and this output ought to tell you what's wrong:


```
mlindsay@Sewageplant:~$ sudo apt-get remove libogg0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  openoffice.org-draw libcaca-dev espeak libg15daemon-client1 libslang2-dev
  openoffice.org-emailmerge libaudiofile-dev openoffice.org-impress libglpng
  openoffice.org-base-core libsvga1 libhyphen0 libavutil-dev libsox-fmt-alsa
  libxdg-basedir1 libglademm-2.4-1c2a ttf-sil-gentium libncurses5-dev
  libiso9660-7 libhsqldb-java libcddb2 libportmidi0 libavahi-client-dev
  libdvbpsi5 openoffice.org-math openoffice.org-writer chromium-bsu-data
  libxosd2 libg15render1 libalut0 firefox-4.0-core libvlc2 uno-libs3
  ttf-uralic libmikmod2 python-uno amsn-data libupnp3 espeak-data libglc0
  libmatroska0 audacity-data libao2 openoffice.org-filter-binfilter liblzo2-2
  avidemux-common libesd0-dev libservlet2.5-java ttf-sil-gentium-basic
  libespeak1 ure libaudio-dev openoffice.org-calc libg15-1 xfonts-mathml
  vlc-data libgraphite3 libtar libvamp-hostsdk3 openoffice.org-common
  libavidemux0 libsox1a openoffice.org-style-galaxy libavahi-common-dev
  libvlccore2 lame libvcdinfo0 libebml0 tcl-tls libaa1-dev openoffice.org-core
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  icedtea-6-jre-cacao openjdk-6-jre-headless openjdk-6-jre-lib phonon
  phonon-backend-null
Suggested packages:
  sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho
  ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts phonon-backend-gstreamer phonon-backend-vlc
  phonon-backend-mplayer
The following packages will be REMOVED:
  aisleriot amsn audacity avidemux brasero chromium chromium-bsu dosbox exaile
  gdm gimp gltron gnome-games-common gnome-mahjongg gnome-settings-daemon
  gnome-sudoku gnome-user-share gnomine gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gtk-recordmydesktop
  icedtea6-plugin libaccess-bridge-java libaccess-bridge-java-jni
  libasound2-plugins libavcodec-dev libavcodec-extra-52
  libavcodec-unstripped-52 libavdevice-extra-52 libavdevice-unstripped-52
  libavfilter0 libavformat-extra-52 libavformat-unstripped-52
  libbrasero-media0 libcanberra-gtk-module libcanberra-gtk0 libcanberra0
  libflac++6 libflac8 libgegl-0.0-0 libgstfarsight0.10-0 libmjpegtools-1.9
  libogg-dev libogg0 libpulse-browse0 libpulse-dev libpulse-mainloop-glib0
  libpulse0 libpurple0 libquicktime1 libsdl-image1.2 libsdl-mixer1.2
  libsdl-net1.2 libsdl-sound1.2 libsdl-ttf2.0-0 libsdl1.2-dev libsdl1.2debian
  libsdl1.2debian-all libshout3 libsmpeg0 libsnack2-alsa libsndfile1
  libsox-fmt-base libtheora0 libvorbis0a libvorbisenc2 libvorbisfile3 libxine1
  libxine1-misc-plugins libxine1-x mangler mencoder mjpegtools
  mozilla-plugin-vlc mplayer mupen64plus openjdk-6-jdk openjdk-6-jre
  openoffice.org openoffice.org-base openoffice.org-filter-mobiledev
  openoffice.org-java-common openoffice.org-officebean
  openoffice.org-report-builder-bin opera phonon-backend-xine pidgin
  pidgin-encryption pidgin-libnotify pidgin-otr pulseaudio
  pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils
  python-pygame quadrapassel recordmydesktop sox timidity timidity-daemon
  transmission-gtk twolame virtualbox-ose virtualbox-ose-qt visualboyadvance
  visualboyadvance-gtk vlc vlc-nox vlc-plugin-pulse vorbis-tools xfce4-mixer
  xfce4-volumed xfswitch-plugin xubuntu-desktop xubuntu-gdm-theme
The following NEW packages will be installed:
  phonon-backend-null
The following packages will be upgraded:
  icedtea-6-jre-cacao openjdk-6-jre-headless openjdk-6-jre-lib phonon
4 upgraded, 1 newly installed, 118 to remove and 194 not upgraded.
Need to get 32.3MB of archives.
After this operation, 352MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
mlindsay@Sewageplant:~$ sudo apt-get remove vorbis-tools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavfilter0 firefox-4.0-core libao2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vorbis-tools
0 upgraded, 0 newly installed, 1 to remove and 229 not upgraded.
After this operation, 811kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200928 files and directories currently installed.)
Removing vorbis-tools ...
Processing triggers for man-db ...
```

As you can see, it's only angry about libogg. Removing vorbis-tools is fine.

You'll probably want me to attach some files and run some commands. I'm pretty lost right now. So please tells me what diagnostics I need.

Thanks.

---


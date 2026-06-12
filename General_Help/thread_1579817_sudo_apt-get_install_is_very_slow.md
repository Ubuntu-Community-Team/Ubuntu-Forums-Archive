---
title: "sudo apt-get install is very slow?"
date: 2010-09-22
forum: General Help
---

### Post by fuzzylogic25 on 2010-09-22
Some programs I have tried installing have been very slow. when I tried installing VLC, it took over 5minutes!

This is the text i saw on the screen:


anthony@a-cmp:/media$ sudo apt-get install vlc
vlc                 vlc-plugin-ggi      vlc-plugin-svg
vlc-data            vlc-plugin-jack     vlc-plugin-svgalib
vlc-dbg             vlc-plugin-pulse    
vlc-nox             vlc-plugin-sdl      
anthony@a-cmp:/media$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libass4 libavcodec52 libavformat52 libavutil49 libcddb2 libdca0
  libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaad2 libgsm1
  libiso9660-7 liblua5.1-0 libmatroska0 libmodplug0c2 libmpcdec3 libmpeg2-4
  libpostproc51 libschroedinger-1.0-0 libsdl-image1.2 libswscale0 libtar
  libtwolame0 libupnp3 libvcdinfo0 libvlc2 libvlccore2 libx264-85
  libxcb-keysyms1 vlc-data vlc-nox vlc-plugin-pulse
Suggested packages:
  libdvdcss2 debhelper build-essential mozilla-plugin-vlc videolan-doc
Recommended packages:
  head
The following NEW packages will be installed:
  liba52-0.7.4 libass4 libavcodec52 libavformat52 libavutil49 libcddb2 libdca0
  libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaad2 libgsm1
  libiso9660-7 liblua5.1-0 libmatroska0 libmodplug0c2 libmpcdec3 libmpeg2-4
  libpostproc51 libschroedinger-1.0-0 libsdl-image1.2 libswscale0 libtar
  libtwolame0 libupnp3 libvcdinfo0 libvlc2 libvlccore2 libx264-85
  libxcb-keysyms1 vlc vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 36 newly installed, 0 to remove and 1 not upgraded.
Need to get 19.7MB of archives.
After this operation, 55.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y^[[3~
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe liba52-0.7.4 0.7.4-13ubuntu1 [28.6kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libavutil49 4:0.5.1-1ubuntu1 [93.3kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libgsm1 1.0.13-3 [27.6kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libschroedinger-1.0-0 1.0.9.is.1.0.8-0ubuntu1 [202kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libavcodec52 4:0.5.1-1ubuntu1 [3,998kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libavformat52 4:0.5.1-1ubuntu1 [719kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libcddb2 1.3.2-0ubuntu1 [48.5kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libdvbpsi5 0.1.6-1 [33.9kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libdvdread4 4.1.3-8ubuntu1 [57.8kB]
Get:10 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libdvdnav4 4.1.3-6 [74.3kB]
Get:11 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libebml0 0.7.7-3.1 [63.7kB]
Get:12 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libenca0 1.12-1 [67.1kB]
Get:13 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libfaad2 2.7-4 [166kB]
Get:14 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libiso9660-7 0.81-4 [126kB]
Get:15 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main liblua5.1-0 5.1.4-5 [82.2kB]
Get:16 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libmatroska0 0.8.1-1.1 [196kB]
Get:17 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libmodplug0c2 1:0.8.7-1build1 [171kB]
Get:18 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libmpcdec3 1:1.2.2-2.1ubuntu1 [26.5kB]
Get:19 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libmpeg2-4 0.4.1-3 [55.9kB]
Get:20 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libpostproc51 4:0.5.1-1ubuntu1 [189kB]
Get:21 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libsdl-image1.2 1.2.10-1 [32.6kB]
Get:22 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libswscale0 4:0.5.1-1ubuntu1 [230kB]
Get:23 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libtar 1.2.11-6 [21.7kB]
Get:24 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libtwolame0 0.3.12-1 [53.6kB]
Get:25 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libvcdinfo0 0.7.23-4ubuntu2 [130kB]
Get:26 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe vlc-data 1.0.6-1ubuntu1.2 [7,199kB]
Get:27 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe libvlccore2 1.0.6-1ubuntu1.2 [410kB]
Get:28 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe libvlc2 1.0.6-1ubuntu1.2 [51.5kB]
Get:29 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libass4 0.9.9-0ubuntu1 [54.0kB]
Get:30 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libdca0 0.0.5-3 [106kB]
Get:31 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libupnp3 1:1.6.6-4 [98.3kB]
Get:32 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe libx264-85 2:0.85.1448+git1a6d32-4 [454kB]
Get:33 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe vlc-nox 1.0.6-1ubuntu1.2 [2,809kB]
Get:34 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main libxcb-keysyms1 0.3.6-1build1 [8,112B]
Get:35 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe vlc 1.0.6-1ubuntu1.2 [1,637kB]
Get:36 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe vlc-plugin-pulse 1.0.6-1ubuntu1.2 [7,308B]
Fetched 19.7MB in 13s (1,473kB/s)                                              
Extracting templates from packages: 100%
Selecting previously deselected package liba52-0.7.4.
(Reading database ... 142215 files and directories currently installed.)
Unpacking liba52-0.7.4 (from .../liba52-0.7.4_0.7.4-13ubuntu1_i386.deb) ...
Selecting previously deselected package libavutil49.
Unpacking libavutil49 (from .../libavutil49_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libgsm1.
Unpacking libgsm1 (from .../libgsm1_1.0.13-3_i386.deb) ...
Selecting previously deselected package libschroedinger-1.0-0.
Unpacking libschroedinger-1.0-0 (from .../libschroedinger-1.0-0_1.0.9.is.1.0.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package libavcodec52.
Unpacking libavcodec52 (from .../libavcodec52_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libavformat52.
Unpacking libavformat52 (from .../libavformat52_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libcddb2.
Unpacking libcddb2 (from .../libcddb2_1.3.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libdvbpsi5.
Unpacking libdvbpsi5 (from .../libdvbpsi5_0.1.6-1_i386.deb) ...
Selecting previously deselected package libdvdread4.
Unpacking libdvdread4 (from .../libdvdread4_4.1.3-8ubuntu1_i386.deb) ...
Selecting previously deselected package libdvdnav4.
Unpacking libdvdnav4 (from .../libdvdnav4_4.1.3-6_i386.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3.1_i386.deb) ...
Selecting previously deselected package libenca0.
Unpacking libenca0 (from .../libenca0_1.12-1_i386.deb) ...
Selecting previously deselected package libfaad2.
Unpacking libfaad2 (from .../libfaad2_2.7-4_i386.deb) ...
Selecting previously deselected package libiso9660-7.
Unpacking libiso9660-7 (from .../libiso9660-7_0.81-4_i386.deb) ...
Selecting previously deselected package liblua5.1-0.
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-5_i386.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1.1_i386.deb) ...
Selecting previously deselected package libmodplug0c2.
Unpacking libmodplug0c2 (from .../libmodplug0c2_1%3a0.8.7-1build1_i386.deb) ...
Selecting previously deselected package libmpcdec3.
Unpacking libmpcdec3 (from .../libmpcdec3_1%3a1.2.2-2.1ubuntu1_i386.deb) ...
Selecting previously deselected package libmpeg2-4.
Unpacking libmpeg2-4 (from .../libmpeg2-4_0.4.1-3_i386.deb) ...
Selecting previously deselected package libpostproc51.
Unpacking libpostproc51 (from .../libpostproc51_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.10-1_i386.deb) ...
Selecting previously deselected package libswscale0.
Unpacking libswscale0 (from .../libswscale0_4%3a0.5.1-1ubuntu1_i386.deb) ...


I believe the unpacking parts take really long. Is there something wrong with my hard disk? Im not doing anything else either.

---


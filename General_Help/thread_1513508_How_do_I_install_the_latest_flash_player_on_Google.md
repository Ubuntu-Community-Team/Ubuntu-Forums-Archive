---
title: "How do I install the latest flash player on Google Chrome 64-bit ubuntu?"
date: 2010-06-19
forum: General Help
---

### Post by inimitablesikh on 2010-06-19
Hey guys. I'm using 10.04 Ubuntu and Google chrome, and I wanted to know how I can install the latest flash player. I got flash player to work, but I don't think it's the latest/best version...I used this to get it working [http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04](http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04)

However, when I watch a youtube video 480p plays fairly well, but when I go 720p and above it stutters. How can I fix this. I have a more than sufficient graphics card with 512 MB dedicated ram, it's an nvidia 8600m. Please help me and it would be much appreciated :P

---

### Post by garvinrick4 on 2010-06-19
The latest is in repositories:
rick@rick-laptop:~$ aptitude show flashplugin-installer
Package: flashplugin-installer
State: installed
Automatically installed: no
Version: 10.1.53.64ubuntu1
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 188k
Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1), ia32-libs (>= 2.2ubuntu18),
         debconf | debconf-2.0, wget, fontconfig
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, xulrunner-1.9, firefox-3.0, konqueror-nsplugins,
          x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu,
          ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (< 6), flashplugin-nonfree (<
           10.0.22.87ubuntu2~), libflashsupport, xfs (< 1:1.0.1-5)
Replaces: flashplugin (< 6), flashplugin-nonfree
Provides: flashplugin-nonfree
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from the net.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can use
 the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed. 
 
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)

rick@rick-laptop:~$

---


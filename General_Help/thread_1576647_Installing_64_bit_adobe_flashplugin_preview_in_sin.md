---
title: "Installing 64 bit adobe flashplugin preview in single command"
date: 2010-09-17
forum: General Help
---

### Post by yakshbuntu on 2010-09-17
I posted a blog on how to install 64 bit adobe flash plugin in Ubuntu Lucid in a single command

[http://duopetalflower.blogspot.com/2010/09/installing-new-adobe-flashplayer-64-bit.html](http://duopetalflower.blogspot.com/2010/09/installing-new-adobe-flashplayer-64-bit.html)

The command is

**sudo aptitude remove flashplugin-nonfree flashplugin-installer && mkdir -p flashplugin-64 && cd flashplugin-64 && wget -c [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p1_64bit_linux_091510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p1_64bit_linux_091510.tar.gz) && tar xzf flashplayer_square_p1_64bit_linux_091510.tar.gz && sudo cp libflashplayer.so /usr/lib64/mozilla/plugins/**

---

### Post by lovinglinux on 2010-09-17
I just released version 1.0.12 of FLASH-AID, which supports the new 64bit version of flash. 

[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)
[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

I always keep it updated, so whenever Adobe releases a new version, the extension will prompt for a new installation. All you need to do is keep your Firefox extensions updated.

---

### Post by volaer on 2011-02-17
Here's a better way to do it...
[http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/](http://www.brandbuildit.com/ubuntu/how-to-install-adobe-flash-player-10-on-ubuntu-64-bit-lucid-lynx/)

---


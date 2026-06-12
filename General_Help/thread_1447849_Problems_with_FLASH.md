---
title: "Problems with FLASH"
date: 2010-04-05
forum: General Help
---

### Post by DieNacht on 2010-04-05
I can't seem to be able to figure Flash out. I'm using Chrome right now and Youtube videos look choppy if I scroll on the screen. Also, the controls sometimes don't work (can't stop the video or start it). And sometimes embedded videos don't play at all. 

I know that it must be that I'm using a old version of flash, but I don't know how to update it. There's Flash plugin for FF in the Software Center, but that's for FF (btw, this is also happening in FF, not only Chrome). There's also a general Plugin in the Software Center but I have no idea what it is or how to use it. 

I tried the Adobe website but that didn't help (told me to download something, but that something wasn't installing). 

Thanks.

---

### Post by mickObrian on 2010-04-05
Where did you install your current flash plugin? I used 'sudo apt-get install flashplugin-nonfree' and am currently using Firefox, everything is working well. Try that out, also have you tried disabling the visual effects? I posted that in threads quite a few times, no one replies if it works or not, but it worked for me, go to System > Preferences > Appearance > Visual Effects and select none and try and pause and play the video again, tell me how it goes.

---

### Post by DieNacht on 2010-04-05
Ok, I did the command and disable the effects. it works now. 

But I like the effects, they were nice and pleasing :(

---

### Post by mickObrian on 2010-04-05
Wish I could help you with the effects, unfortunately I don't know what's wrong either. I don't mind them turned off personally.

---

### Post by garvinrick4 on 2010-04-05
sudo apt-get clean


 sudo apt-get install --reinstall flashplugin-nonfree


rick@rick-laptop:~$ aptitude show flashplugin-nonfree
Package: flashplugin-nonfree
State: not installed
Version: 10.0.45.2ubuntu1
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 41.0k
Depends: flashplugin-installer
Provided by: flashplugin-installer
Description: Adobe Flash Player plugin installer (transitional package)
 This package is a transitional package that can safely be removed after you
 installed flashplugin-installer.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)

rick@rick-laptop:~$ aptitude show flashplugin-installer
Package: flashplugin-installer
State: installed
Automatically installed: no
Version: 10.0.45.2ubuntu1
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

### Post by DieNacht on 2010-04-05
> **garvinrick4 said:**
> sudo apt-get clean


 sudo apt-get install --reinstall flashplugin-nonfree


rick@rick-laptop:~$ aptitude show flashplugin-nonfree
Package: flashplugin-nonfree
State: not installed
Version: 10.0.45.2ubuntu1
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 41.0k
Depends: flashplugin-installer
Provided by: flashplugin-installer
Description: Adobe Flash Player plugin installer (transitional package)
 This package is a transitional package that can safely be removed after you
 installed flashplugin-installer.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)

rick@rick-laptop:~$ aptitude show flashplugin-installer
Package: flashplugin-installer
State: installed
Automatically installed: no
Version: 10.0.45.2ubuntu1
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

Is this going to allow me to put the effects on again?

---

### Post by marshmallow1304 on 2010-04-05
> **DieNacht said:**
> Ok, I did the command and disable the effects. it works now. 

But I like the effects, they were nice and pleasing :(

If you install [fusion-icon]("atp://fusion-icon"), you can more easily disable/enable visual effects.  You would just set Window Manager to Metacity, watch your YouTube video, then change it back to Compiz when done.

---

### Post by s1bley on 2010-04-07
I was having the exact same problem with flash in Google Chrome...buttons were generally unresponsive to my clicking.

I turned off the visual effects and everything was fixed. I'll take working flash over the visual effects any day.

---


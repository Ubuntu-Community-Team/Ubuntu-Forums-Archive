---
title: "Adobe drops 64 bit flash support"
date: 2010-06-16
forum: General Help
---

### Post by ibbill on 2010-06-16
Again tried to post this in the 64 bit but it is close so posting here  You can read about it [HERE]("http://www.linuxpromagazine.com/Online/News/Adobe-Drops-64-Bit-Flash-Support-for-Linux")

I have 64  flash installed seems okay not sure what the problem is or what adobe is doing.

Credit for this info Ubunt Geek

---

### Post by lovinglinux on 2010-06-19
The 64bit has a critical vulnerability. You shouldn't be using it.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by ibbill on 2010-06-19
lovinglinux thanks for the info. Not sure why they are doing this stuff you think they could get it right by now. Oh well not for me to whine about.

I have installed the 64 bit as I use chrome as my browser and so far no problems. Did the following.Thanks to [HERE]("http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html")

Go to Applications->Internet->Chromium Browser and right click it, add to panel.Right click the new chromium icon and add the following command where it says command

chromium-browser --enable-plugins

That&#8217;s it from now on you should able to view youtube or any other flash video.

Another site I followed  and install  64 bit flash and works fine in firefox and chrome. Can't remember where I got the info from. Thanks for your help.

---

### Post by deepclutch on 2010-06-22
[FONT=Trebuchet MS][SIZE=3]One Solution is to have chroot with 32-bit browser and 32-bit plugins.
I will not try that!
The Solution ,atleast for firefox users is to use  and install the 3.6.4 build7(and higher) and enable "
dom.ipc.plugins.enabled true" in "about:config" with 32-bit flash plugin and nspluginwrapper.
Check this at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/592492](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/592492)[/SIZE][/FONT] [FONT=Trebuchet MS][SIZE=3]
this is because ,latest flash 32 plugin is not supported fully by nspluginwrapper.I'm wondering if nspluginwrapper ever gets updated.Using an OBSOLTE alpha 64-bit plugin is not the solution IMHO.
If you don't mind to be a firefox beta tester:
[/SIZE][/FONT]
[LIST]
[*][FONT=Trebuchet MS][SIZE=3]get PPA for Ubuntu  Mozilla Security Team [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa)[/SIZE][/FONT]
[*][FONT=Trebuchet MS][SIZE=3]install nspluginwrapper first and install flash32 plugin.
[/SIZE][/FONT]
[/LIST]
[FONT=Trebuchet MS][SIZE=3]to have libflashplayer.so ,you can get it in this package:
[http://www.debian-multimedia.org/pool/non-free/f/flash-player-amd64/flashplayer-mozilla_10.1.53.64-0.0_amd64.deb](http://www.debian-multimedia.org/pool/non-free/f/flash-player-amd64/flashplayer-mozilla_10.1.53.64-0.0_amd64.deb)

Ref:
[http://forums.debian.net/viewtopic.php?f=16&t=53036](http://forums.debian.net/viewtopic.php?f=16&t=53036)

[/SIZE][/FONT]

---

### Post by ibbill on 2010-06-22
deepclutch thanks for the info. 

 I must say seeing that most computers you buy now are all 64 bit so I would think it's time Adobe and any of the others get their act together.

  I have been using chromium as my default browser with no problems.

Personally I have given up on Firefox found it very slow and unresponsive compared to chromium.

Thanks again.

---


---
title: "Flash will not Install on Firefox Properly"
date: 2010-05-17
forum: General Help
---

### Post by TurtleKing on 2010-05-17
OS: Ubuntu 10.04 64 bit
I tried to watch a video on Firefox through hulu.com and kept getting unresponsive script error upon the website showing up. On other occasions some websites would open up very slowly. So I went ahead and started looking up the problem on google, and found two areas where this may occur:

1.Google search toolbar or add-on in firefox which I cannot find how in the world to disable since it seems to come inside the firefox package (I tried edit-preferences-addon- its not listed).

2.Adobe Flash Player: I disabled it and the websites are no longer slow, but now I cannot watch the video on hulu.com which is the main reason why I opened firefox. So I went ahead and installed Adobe Flash again, but it doesn't seem to want to work. Gnash and the other program (I forgot the name) install properly on Firefox but Adobe Flash Player keeps giving me errors. This is one of them when I tried downloading and installing it from terminal:
```
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Honestly I wish all the websites would make their flash videos more compatible with other program, but for time being the Flash Monopoly still continues. Anyways, any solution or possible work-around? 

By the way, as some of you may know Adobe Flash player doesn't support Google chrome for Linux (chromium). I would really hate to have to switch to my Vista Hard Drive just to see a video on Firefox.

---

### Post by jubilee33 on 2010-05-17
1. The Google toolbar can be removed by doing the following:

Go to View -- Toolbars -- Cuztomize.  Drag the Google toolbar into the "cuztomize" window.  You might want to hold down the CTRL key while dragging it.  The google toolbar will disappear after this.

2. Regarding the 64bit flash, please follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1358591").  It's a sticky in the x86 64-bit forum.

---

### Post by oldos2er on 2010-05-17
> **TurtleKing said:**
> By the way, as some of you may know Adobe Flash player doesn't support Google chrome for Linux (chromium). 

Flash works fine on chromium-browser for me. I second the motion to install 64-bit flash.

---

### Post by QIII on 2010-05-17
swfdec and gnash conflict with Flash, so removing them might be something to try.

Some websites, including Hulu, do not play nicely with the 64 bit Linux version of Flash.

Hulu, for one, will give you a nasty message that you are not welcome because you are using it.

---

### Post by lovinglinux on 2010-05-17
If you are talking about this search bar:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157314&stc=1&d=1274128356[/IMG]

Then follow the instructions from jubilee33. It won't disable it, since is part of the browser, but will hide it. BTW, why you want to remove that? That is not only a Google search bar, is the browser search bar. You can add many search engines to it. See [this](http://firefox-tutorials.blogspot.com/2010/05/extension-review-add-to-search-bar.html).

If you are talking about Google toolbar extension, then you can disable or remove it from "Tools >> Add-ons" menu in Firefox.

I also recommend installing the 64bit version of Flash. Make sure you remove gnash, swfdec and the 32bit version before installing it. See [this](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

Despite the fact that Hulu might not work with 64bit, according to QIII post, it is a much better version than the 32bit. See [this poll](http://swiss.ubuntuforums.org/showthread.php?t=1450623).

I can't test Hulu here, because I'm outside US, but I have read that you would have better luck with the standalone Hulu player.

---

### Post by TurtleKing on 2010-05-17
Thanks got it working with the help of that sticky. Not sure why it stop working in the first place though with the script problem.

---


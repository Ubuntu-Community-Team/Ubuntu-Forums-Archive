---
title: "Embedded Flash objects unresponsive to mouse input"
date: 2010-03-05
forum: General Help
---

### Post by SamBam77 on 2010-03-05
I have installed Flash (via Synaptic Package manager, “flashplugin-installer” and “flashplugin-nonfree”) on Ubuntu 9.10, 64-bit.
 

 When I attempt to view / interact with embedded flash objects in HTML pages using FireFox 3.5.8 I find that they are unresponsive to my mouse clicks (though mouse-over seems to work).  For example, if I would like to start an embedded flash movie, I cannot click the play button, nor can I control any of the other mouse-click controls.  Also, on occasion, the entire flash object will not display at all but will instead just leave a big white space on the web page.
 

 I do not have any flash-blocking ad-ons installed.
 

 When I first installed flash I experienced this problem but was able to temporarily fix it by downloading the 64-bit version of flash 10 from Adobe,
 [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
 and manually copy-pasting this file into FireFox's “Plugins” folder (which I had to create myself in the “.mozilla” folder).  Immediately after doing this flash objects work properly in FireFox, but upon restarting my computer I find that the almost always problem re-occurs and I have to remove and then re-copy the 64-bit plugin into the plugins folder again to get it to work.
 

 FireFox is my primary browser, but on occasion I will use Google Chrome and have not experienced this same problem with viewing flash objects.

---

### Post by Greenwidth on 2010-03-05
From:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

---

### Post by SamBam77 on 2010-03-05
Thank you very much.

Your response also lead me to this quick set of instructions which worked for me.
[http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/](http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/)

[Solved]

---

### Post by Linux-Djihad on 2010-03-09
Thanks for the workarounds. I had the same problems.

---

### Post by Scayris on 2010-04-12
Thank you sooo much for this, I've been trying to fix unresponsive flash for an hour before I found this thread and with the 3rd workaround it was fixed in 2 minutes :D

---

### Post by abdusamed on 2010-05-17
same here on 64bit ubuntu 10.04!

yea..fixed using terminal workaroudn..always prefer solution which have terminal in it :)

---


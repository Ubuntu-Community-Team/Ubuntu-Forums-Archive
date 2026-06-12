---
title: "No flash after firefox restart"
date: 2009-12-03
forum: General Help
---

### Post by crusty420 on 2009-12-03
Hello all, first post here, and I hate to ask a question that has been so much trouble for people it seems. I'm running Kubuntu 9.10 64-bit, with firefox 3.5.5, and newest version of flash 
**Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r32It installs fine, launch the web browser and it plays fine, but as soon as I quit firefox and bring it back up all the videos/advertisement are blank, I can't even right click on where the flash is supposed to be and get the flash menu. I didn't really have any problems with the earlier version using nswrapper besides flash randomly stopped working and I would have to restart FF or reload the page(sometimes doesn't work). I've followed countless guides on here about uninstalling/reinstalling the new flash, I've cleared the /home/user/.mozilla folder, usr/lib/firefox, usr/lib64/firefox3.5, etc, tried a fresh install of FF with nothing but that plugin. The only way I can seem to get it working is to reinstall firefox, install the plugin, and it will work fine, until I close the browser. I've even check my permission(though I may have missed something) on my plugin and folders. So is there any kind of work around? Or do I need to just stick to the old flash and nswrapper?

---

### Post by crusty420 on 2009-12-03
[IMG]http://i49.tinypic.com/29tsap.jpg[/IMG]
[IMG]http://i50.tinypic.com/2utixs5.jpg[/IMG]

---

### Post by Some Penguin on 2009-12-03
Perhaps you might want to look at [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by PeggySue on 2009-12-03
I'm running 64 bit AMD (Dell Vostro) with Firefox 3.5.5.  Flash always works fine.

I installed "Adobe Flash Player plugin installer 10.0.32.18 ubuntu1" from Synaptic Package Manager and restarted Firefox.   My attempt to load Flash Player from adobe failed.

Not sure if this will help!

---

### Post by crusty420 on 2009-12-03
> **Some Penguin said:**
> Perhaps you might want to look at [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)
Thanks man exactly what I was looking for! :D

---

### Post by crusty420 on 2009-12-03
> **PeggySue said:**
> I'm running 64 bit AMD (Dell Vostro) with Firefox 3.5.5.  Flash always works fine.

I installed "Adobe Flash Player plugin installer 10.0.32.18 ubuntu1" from Synaptic Package Manager and restarted Firefox.   My attempt to load Flash Player from adobe failed.

Not sure if this will help!
Yeah I'm having the same problem, no matter what I tried I couldn't get it working properly, so I just resorted to taking the easy way out and using the script to correct everything I screwed up, after I removed the new flashplayer.so .
Here's the script for anyone having problems installing flash player on 64 bit firefox.
[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888)

If you look further down the page there is this posted, which was actually exactly what I was looking for, maybe it'll come in handy for everyone out there also. :D
It's about 3/4 down the link above ^ credit where credit is due!
> nubo 10.17.09 at 12:13 am 					 						 4th MORE IMPROVED VERSION, fully linelengh checked with #:
 **for the pure 64-bit-flash-version: installation guide:**
 download Flash from [ here]("http://labs.adobe.com/downloads/flashplayer10.html") then upack
from [ this post]("http://forum.ubuntuusers.de/post/1689592/") translatet:
 # deinstall all other Flashplayer
# which are installed?:
dpkg -l flashplugin-nonfree mozilla-plugin-gnash swfdec-mozilla
#
# delete installed:
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree
#
# create new folder for Flashplayer:
sudo mkdir /usr/lib/flashplugin-nonfree/
#
# copy the new Flashplayer in the just created folder. change the first
# term to the unpacked path.
# if you unpacked to your Desktop, replace YourDownloadPath with
# /home/YourLoginName/Desktop
sudo cp YourDownloadPath/libflashplayer.so /usr/lib/flashplugin-nonfree/
#
# give Firefox the Flashplayer as Plugin , by creating a symbolic Link
# to the path of the Flashplayers in Plugin-folder from Firefox:
sudo ln -s  /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
wrapper good bye!
 						
 					

---


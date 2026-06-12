---
title: "Stop xine firefox plugin from loading xine externally"
date: 2006-03-27
forum: General Help
---

### Post by jms830 on 2006-03-27
How can I stop the xine plugin for firefox from loading xine whenever I get to a site with a video? I uninstalled xine and then the mplayer plugin took over and plays the videos within firefox. But I prefer xine as a video player, so i reinstalled it but now I still have the problem again. How do I make videos play within firefox?

---

### Post by dcstar on 2006-03-27
[QUOTE=jms830]How can I stop the xine plugin for firefox from loading xine whenever I get to a site with a video? I uninstalled xine and then the mplayer plugin took over and plays the videos within firefox. But I prefer xine as a video player, so i reinstalled it but now I still have the problem again. How do I make videos play within firefox?[/QUOTE]
Install mozplugger

---

### Post by jms830 on 2006-03-27
thanks. I also had to delete the link to gxineplugin.so in my ~/.mozilla/plugins folder. now I tried this [http://www.ubuntuforums.org/showthread.php?t=17727](http://www.ubuntuforums.org/showthread.php?t=17727) to use embedded xine instead of the mplayer plugin, but i couldn't quite get it to work. so now after deleting that gxineplugin.so link it just reverts to the mplayer plugin and plays videos embedded.

---

### Post by eeried on 2006-05-05
In my case, gxine is installed but there is no plugin file (gxineplugin.so) in any of mozilla plugin dir.  I have
[LIST=1]
[*]/usr/lib/mozilla/plugins -- though Mozilla isn't installed
[*] /usr/libmozilla-firefox/plugins (Ubuntu package)
[*]/opt/firefox/plugins -- my installation of Firefox 1.0.3 (TARGZ binary file from mozilla.com)
[/LIST]

However gxine works fine -- but tends to take over from Mplayer. I have both mozplgger and mplayer-plugin installed which may cause some conflict??

In your case if you want to read some files with Mplayer rather than gxine you may fin the  Media Connectivity Firefox extension useful : it enables you to choose exactly which software you like to read various kinds of files. You can change your mind any time while surfing, and change the settings inside Firefox.

Could be the solution for you.:rolleyes: 

Good luck!

---


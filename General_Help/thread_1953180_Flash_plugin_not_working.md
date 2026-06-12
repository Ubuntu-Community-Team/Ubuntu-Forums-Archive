---
title: "Flash plugin not working"
date: 2012-04-05
forum: General Help
---

### Post by oslub on 2012-04-05
Hello.

Web applications requiring adobe flash plugin are not working on my lubuntu, even though I have tried to reinstall it with synaptics and in lxterminal, but still those websites require flash plugin as if it were not installed. It is happening both with Firefox and Chromium (latest versions). Just two or three days ago it was working fine.

By the way, ever since I installed lubuntu, when using Chromium to watch youtube videos, the page always crashes when trying to switch to full screen mode. That does not happen with Firefox, any ideas why?

Thank you in advance for your support to both this issues, the first one being more urgent.

---

### Post by JC Cheloven on 2012-04-05
Just to be sure, is that what you have tried? :
```
sudo apt-get install --reinstall flashplugin-installer
```

As for the second question: not exactly an answer, but you may want to try the html5 way in youtube. It's just about scrolling down to the bottom of the youtube page, click on "try something new" and select html5. It is still in testing, but I'd say it's worth to try (as it is somehow the flash alternative we were awaiting).

---

### Post by claracc on 2012-04-06
> Web applications requiring adobe flash plugin are not working on my lubuntu, even though I have tried to reinstall it with synaptics and in lxterminal, but still those websites require flash plugin as if it were not installed. It is happening both with Firefox and Chromium (latest versions). Just two or three days ago it was working fine.

I have experienced the same problem with last adobe flash plugin update: [http://ubuntuforums.org/showthread.php?t=1949598](http://ubuntuforums.org/showthread.php?t=1949598)

The only workaround found for my lubuntu 11.04 system with epiphany and chromium browsers is to install adobe flash plugin 11.1.102.62. In the thread posted you have the repositories address to install this adobe flash plugin. Of course avoid to update it to the new problematic release 11.2.202.228.

---

### Post by Rodney9 on 2012-04-06
sudo apt-get update && sudo apt-get install adobe-flashplugin -y


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by oslub on 2012-04-06
> **JC Cheloven said:**
> Just to be sure, is that what you have tried? :
```
sudo apt-get install --reinstall flashplugin-installer
```

As for the second question: not exactly an answer, but you may want to try the html5 way in youtube. It's just about scrolling down to the bottom of the youtube page, click on "try something new" and select html5. It is still in testing, but I'd say it's worth to try (as it is somehow the flash alternative we were awaiting).

Yes. I've used that command, it reinstalls adobe flash plugin and then same problems continue. It seems to be an issue with this particular update, the 11.2.202.228, since before upgrading, flash plugin web applications were working fine, except for this trouble with youtube and chromium. 

I've tried the html5 experimental mode but the same thing happens, the "Aw, Snap!" screen comes up when switching to full screen mode.


> **Rodney9 said:**
> sudo apt-get update && sudo apt-get install adobe-flashplugin -y


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

Everything is updated in my lubuntu system at the moment.

> **claracc said:**
> I have experienced the same problem with last adobe flash plugin update: [http://ubuntuforums.org/showthread.php?t=1949598](http://ubuntuforums.org/showthread.php?t=1949598)

The only workaround found for my lubuntu 11.04 system with epiphany and chromium browsers is to install adobe flash plugin 11.1.102.62. In the thread posted you have the repositories address to install this adobe flash plugin. Of course avoid to update it to the new problematic release 11.2.202.228.

Yes, I believe this new update is particulary problematic, because before updating it was working fine. Anyway I'll give it a try downgrading version.

---

### Post by Dave_G on 2012-04-06
Install Flash Aid for Linux and run it; this seemed to solve my Flash problems on 11.10.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by oslub on 2012-04-06
I was going to perform a downgrade to an older version of Flash Plugin and I used synaptics package manager, marking the plugin for complete removal. Just to be sure, before going for a previous version, I tried to install the latest version again, by marking it to install in synaptics and unexpectedly, now everything is working fine in both Chromium and Firefox. 

I don't understand why reinstalling command and marking it to reinstall in synaptics it didn't work, only worked by removing it completely first and then installing it with synaptics.

Unfortunatelly, The "Aw Snap!" crash page still occurs everytime I want to watch youtube videos in full screen with chromium. Well, anyway Firefox is my default browser. I am glad that latest version of flash plugin now works.

I'll mark the thread as solved, although I can't provide other ubuntu users a concrete solution, if you have the same issue, try to remove flash plugin completely and installing it again with synaptics, maybe it will work as it did for me now.

---

### Post by oslub on 2012-04-06
> **Dave_G said:**
> Install Flash Aid for Linux and run it; this seemed to solve my Flash problems on 11.10.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Thank you for the tip, I didn't know about this add-on, I shall make use of it next time something happens with flash plugin ;)

---

### Post by Dave_G on 2012-04-06
After running the Flash Aid i noticed that it removed the flashplugin-installer and few other things, and everything seemed to work.  I had problems watching video's on Youtube as the sizes were all messed up, but the Flash Aid seemed to fix everything.

---

### Post by Dave_G on 2012-04-06
Forgot to mention that Flash Aid also fixed a problem with me viewing street view in Google Maps and Earth.

---

### Post by Lothsahn on 2012-05-02
I attempted to install flashaid, but it didn't fix the problem.  Flashaid just attempted to reinstall the same broken 11.2.202.233 version of the plugin.

I finally resolved the problem by manually installing the adobe-flashplugin_11.1.102.62-0lucid1_i386.deb package.

---


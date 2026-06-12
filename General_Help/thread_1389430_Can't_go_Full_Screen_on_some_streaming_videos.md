---
title: "Can't go Full Screen on some streaming videos"
date: 2010-01-24
forum: General Help
---

### Post by daldude on 2010-01-24
I've started to have problems getting some streaming videos to either go full screen or go full screen properly. 
On comedycentral.com when I want to watch a South Park episode full screen it pops up a little box that says "Error Full Screen Not Allowed" and if I hover my mouse over the video connection icon is says
 "current video stream 750 kbps*
Max video stream 800kbps
**[COLOR=Black]Avalible in HD[/COLOR]**_Go to Fullscreen_

*limited by this computer"

the current avaible bandwith speed averages 2500kbps and I have a 7000kbps connection with Speedboost.

When I use Windows XP I can go to full screen with South Park Videos, only in Ubuntu can I not go full screen.


With Hulu it will go into full screen but not always the porpper way. Sometimes it will go full screen but other times it will go full screen but I have to minimize the browser window and then maximize it again and the video will play full screen but apear to be playing on the desktop as wallpaper.

I don't get this problem in XP.

This seems to have just started after the last time I did a recomended automatic secuirity update with updae maager.

My Video Card is a ATI Radeon 9000 at 1280x1024 true color.

---

### Post by warfacegod on 2010-01-24
This might help:

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by daldude on 2010-01-26
> **warfacegod said:**
> This might help:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

I don't think this is the problem because the same problem happens in all browsers and not just Firefox. It happens in Google Chrome and Epiphany Gecho browsers.

I thinks maybe it has something to do with Flash getting corrupted.
How do I uninstall and then reinstall Flash?

---

### Post by warfacegod on 2010-01-26
Go to: System> Admin.> Synaptic> search for Flash and mark them all for reinstallation.

Be sure your video driver is in working order. If you complied it from a drive from ATi's site it may not have survived the update.

---

### Post by daldude on 2010-01-26
> **warfacegod said:**
> Go to: System> Admin.> Synaptic> search for Flash and mark them all for reinstallation.

Be sure your video driver is in working order. If you complied it from a drive from ATi's site it may not have survived the update.

Sadly this did not work, I still have the same problem which does not happen in XP so it can't be the site.

What is the difference between Mark for Removal and Mark for Complete Removal?

How do I know if I have an ATI video driver or just the Ubuntu video driver?
If I did find the actuall offical ATI driver how would I install it? I tried installing what I thought was the ATI driver for my card in Ubuntu 9.10 but it did not seem to work because nothing changed. Since then I went back to Ubuntu 9.04 64-bit because 9.10 had too many problems and I did not like it's new Add Applications interface.


Thanks

---

### Post by warfacegod on 2010-01-26
> **daldude said:**
> Sadly this did not work, I still have the same problem which does not happen in XP so it can't be the site.

What is the difference between Mark for Removal and Mark for Complete Removal?

How do I know if I have an ATI video driver or just the Ubuntu video driver?
If I did find the actuall offical ATI driver how would I install it? I tried installing what I thought was the ATI driver for my card in Ubuntu 9.10 but it did not seem to work because nothing changed. Since then I went back to Ubuntu 9.04 64-bit because 9.10 had too many problems and I did not like it's new Add Applications interface.


Thanks

Mark for Complete removal will remove the software as well as the configuration settings for it.

The Ubuntu driver should be an older, better tested version of the ATi driver. If you want the newest one, there should be instructions for installing it on ATi's website.

---


---
title: "Ubuntu Software Center &quot;Dead&quot; !"
date: 2011-05-23
forum: General Help
---

### Post by samMD on 2011-05-23
So after I went to OMG ubuntu site and downloaded "complex shutdown" since it looked useful and I needed it I installed it..but it doesnt seem to start up for some reason so when I went to uninstall it software center went "blank" just a grey screen with the black toolbar

Thanks again Ubuntu Community for all the help!

---

### Post by vaina001 on 2011-07-30
I did the same thing yesterday, installed because thought it would be very useful but the app doesnt open when i click on the icon, it doesnt even appear in the software center so i cant uninstall it because i dont even know what its terminal command is.

I hope someone can help out with this.

---

### Post by vaina001 on 2011-07-30
> **samMD said:**
> So after I went to OMG ubuntu site and downloaded "complex shutdown" since it looked useful and I needed it I installed it..but it doesnt seem to start up for some reason so when I went to uninstall it software center went "blank" just a grey screen with the black toolbar

Thanks again Ubuntu Community for all the help!


I uninstalled it using this command sudo apt-get --purge remove complexshutdown and worked perfectly. Now the .deb file i originally downloaded was the complexshutdown_0.5_all.deb for all versions but that didnt work, so i went back to the website and clicked on all versions [https://launchpad.net/complexshutdown/+download](https://launchpad.net/complexshutdown/+download) and thats where i found for 32 and 64 bit and source versions.

I download this one complexshutdown_0.4_amd64.deb and now works perfect and if you have 32 bit system then choose the i386 version but its great now.** []("http://launchpad.net/complexshutdown/trunk/0.5/+download/complexshutdown_0.5_all.deb")**

---


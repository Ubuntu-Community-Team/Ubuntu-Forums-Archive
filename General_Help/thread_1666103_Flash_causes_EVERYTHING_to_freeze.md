---
title: "Flash causes EVERYTHING to freeze"
date: 2011-01-13
forum: General Help
---

### Post by Mgiacchetti on 2011-01-13
Basically put, title sums up everything I experience.

What can be done to stop this?

---

### Post by DanneStrat on 2011-01-13
Can you give more info about

your computer?

Does it cause your system to

freeze completely?

---

### Post by Mortosa on 2011-01-13
I had the same problem. I had installed flash through ubuntu tweak. When I was doing something that used flash it froze up the entire system. Here is what I did to fix it. 

1. uninstall the version you have currently

2. Download this version of flash from adobe if you are using 64bit Ubuntu like I am - [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

3. untar the file and open a terminal

4. In terminal issue the command sudo mv libflashplayer.so /usr/lib64/mozilla/plugins

5. Now you have a current version. Test it in firefox to make sure it works.


It fixed my issue. If you are using the 32 bit version then just find the download on their site and put it in the appropriate place.  Hope this helps

---

### Post by Cavsfan on 2011-01-13
> **Mortosa said:**
> I had the same problem. I had installed flash through ubuntu tweak. When I was doing something that used flash it froze up the entire system. Here is what I did to fix it. 

1. uninstall the version you have currently

2. Download this version of flash from adobe if you are using 64bit Ubuntu like I am - [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

3. untar the file and open a terminal

4. In terminal issue the command sudo mv libflashplayer.so /usr/lib64/mozilla/plugins

5. Now you have a current version. Test it in firefox to make sure it works.


It fixed my issue. If you are using the 32 bit version then just find the download on their site and put it in the appropriate place.  Hope this helps


I had the 64 bit "square preview release" flash installed on my system, but when it came up with security holes in it, I uninstalled it and went with the 32 bit version.
That Adobe site states this: "This preview release is designed for evaluation purposes only. We do not  recommended that this release be used on production systems or for any  mission-critical work.'

This site let me know about the security hole: [[COLOR=blue]_https://panopticlick.eff.org/_[/COLOR]]("https://panopticlick.eff.org/")
With Noscript installed, it says "[SIZE=-2]no javascript" on many of the items, but with that 64 bit square version installed, it said I was unique and even Noscript didn't keep me protected.
If you want security, go with the 32 bit version of flash.
[/SIZE]

---

### Post by Mortosa on 2011-01-13
ahh I didnt see that thanks for the info.

---

### Post by Cavsfan on 2011-01-13
> **Mortosa said:**
> ahh I didnt see that thanks for the info.

You're welcome. Maybe Adobe will one day support 64 bit flash for Ubuntu.
I just clean installed Lucid after Maverick messed up on me and I was looking and looking for a way to install flash 32 bit and finally just installed the restricted extras.

```
sudo apt-get install ubuntu-restricted-extras
```That did the job and it installed a whole bunch of other stuff. I am sticking with the LTS from now on. I got anxious and wound up installing Maverick and all was well for 3 months, but then some strange things started happening.

---

